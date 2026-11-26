---
tipo: processo
status: em-uso
versao: v1
atualizado: 2026-11-26
autor: claude
---
# Publicar e agendar Reels no @guimiguelmkt pela API

O Claude sobe o Reels pela Graph API do Instagram e deixa um job do launchd publicar na hora marcada. Criado em 26/11/2026, quando o token do usuário do sistema `hub3ps` ganhou `instagram_content_publish`.

**Ferramenta:** `~/ferramentas/instagram/publicar.py` (fora do repo, como a ponte do WhatsApp), log em `~/ferramentas/instagram/logs/publicar.log`.

## Por que assim
- **A API do Instagram não agenda.** Ela publica na hora. O vídeo sobe antes e vira um contêiner pronto, que vale 24 h; o launchd chama o `media_publish` no horário
- **O token sai do Keychain** (serviço `hub3ps-meta-token`), porque job do launchd não lê a Área de Trabalho, onde fica o `credenciais.local.md`. Trocou o token: rodar de novo `security add-generic-password -U -a hub3ps -s hub3ps-meta-token -w <token>` (o Claude faz, sem mostrar o token)
- **O Mac precisa estar acordado.** Se estiver dormindo, o post sai quando ele acordar. Para horário de madrugada, o Guilherme roda `sudo pmset schedule wake "MM/DD/AAAA HH:MM:SS"` uns minutos antes

## Passo a passo
1. **Vídeo:** sai do [[03-processos/editar-video|editor]] em HDR (HEVC 10 bits). Converter para H.264 1080p: `avconvert --source <video> --preset Preset1920x1080 --output <saida>.mp4`
2. **Legenda do post:** num `.txt`, frase de uma linha e 3 a 5 hashtags
3. **Ok do Guilherme** no vídeo e na legenda. Sem ok, não sobe
4. **Subir:** `python3 publicar.py subir <video> <legenda.txt>` devolve o `creation_id` e espera ficar `FINISHED`
5. **Agendar:** `python3 publicar.py agendar <creation_id> "AAAA-MM-DD HH:MM" <nome>`. Cria `~/Library/LaunchAgents/com.hub3ps.ig-<nome>.plist`, que se apaga depois de publicar
6. **Conferir no horário:** o log mostra o link do post. Registrar o link no roteiro

## Erros já vistos
- **Upload devolve 400 `ProcessingFailedError`:** acontece mesmo com o vídeo recebido. Quem decide é o `status_code` do contêiner: `FINISHED` está pronto. O script envia em partes de 8 MB, com `Content-Type: application/octet-stream`, e confere o status depois
- **Contêiner de teste** sobra sem publicar e expira em 24 h; não precisa apagar
- **Insights da conta** (`/<ig>/insights`) dão `#10`; os de cada post funcionam

# ZenPTai — App custom para Umbrel

WebAPP para Personal trainers e ginásios com frontend + backend Node.js/TypeScript, PostgreSQL e Ollama (IA local).

## O que é necessário configurar antes de instalar

1. Copie `.env.example` para `.env` na pasta de dados da app no Umbrel:
   ```
   /home/umbrel/umbrel/app-data/zenptai/.env
   ```
2. Preencha `POSTGRES_PASSWORD`, `JWT_SECRET`, `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`, `GOOGLE_REDIRECT_URI`.
3. Se quiser usar SSL próprio, coloque os certificados em:
   ```
   /home/umbrel/umbrel/app-data/zenptai/certs/
   ```
   Caso contrário, deixe `USE_HTTPS=false` (funciona com Cloudflare Tunnel).
4. O hook `pre-start` cria automaticamente as pastas `pgdata/`, `uploads/`, `ollama_data/`, `certs/`.

## Portas

| Componente | Porta interna | Porta externa (manifesto) |
|---|---|---|
| ZenPTai app | 3000 | 3003 |
| PostgreSQL | 5432 | não publicada (interna) |
| Ollama | 11434 | não publicada (interna) |

> ⚠️ Não use porta 80, 443, 2000, 3000, 3001, 3002 (ocupadas pelo sistema/Outras apps).

## Exposição externa

Use a app oficial Cloudflare Tunnel do Umbrel ou o Nginx Proxy Manager para expor o domínio (ex: `zenpt.ileve.com.pt`) para a porta interna da app.

## Nota sobre Ollama

Esta app inclui o seu próprio container Ollama. Se já tiveres a app Ollama oficial do Umbrel instalada, podes remover o serviço `ollama` deste compose e apontar `OLLAMA_HOST` para o Ollama existente.

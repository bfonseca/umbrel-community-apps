# FocusTime — App custom para Umbrel

Webapp para gestão de tempos com frontend + backend Node.js/TypeScript e PostgreSQL.

## O que é necessário configurar antes de instalar

1. Copie `.env.example` para `.env` na pasta de dados da app no Umbrel:
   ```
   /home/umbrel/umbrel/app-data/focustime/.env
   ```
2. Preencha `JWT_SECRET`, `POSTGRES_PASSWORD`, `APP_URL`, `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`.
3. O hook `pre-start` cria automaticamente as pastas `postgres_data/` e `uploads/`.

## Portas

| Componente | Porta interna | Porta externa (manifesto) |
|---|---|---|
| FocusTime app | 3030 | 3002 |
| PostgreSQL | 5432 | não publicada (interna) |

> ⚠️ Não use porta 80, 443, 2000, 3000, 3001 (ocupadas pelo sistema/Outras apps).

## Exposição externa

Use a app oficial Cloudflare Tunnel do Umbrel ou o Nginx Proxy Manager para expor o domínio `focustime.ileve.com.pt` (ou outro) para a porta interna da app.

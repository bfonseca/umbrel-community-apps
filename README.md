# Ileve Community Apps

Store de apps customizadas para Umbrel OS. Cada subpasta é uma app independente
pronta para instalar com um clique via Community App Stores.

## Apps disponíveis

| App | ID | Descrição | Porta |
|---|---|---|---|
| ileve Website | `ileve` | Site institucional da ileve (HTML/CSS/JS + PHP contacto) | 3001 |

## Como adicionar esta store ao teu Umbrel

1. Abre a App Store no teu Umbrel.
2. Vai a **Community App Stores → Add Store**.
3. Cole a URL deste repositório GitHub.
4. A store aparece na lista — instala a app que quiseres.

## Como adicionar uma nova app/webapp

Esta store está preparada para crescer. Para adicionar um novo site ou webapp:

1. Cria uma nova pasta na raiz do repo com o ID da app (ex: `meu-outro-site/`).
2. Dentro dessa pasta, cria dois ficheiros seguindo o padrão da Umbrel:

   ```
   meu-outro-site/
     umbrel-app.yml      # metadados da app (id, nome, porta, etc.)
     docker-compose.yml  # serviços Docker + app_proxy
   ```

3. Copia os ficheiros do site para o diretório de dados no teu Umbrel:

   ```
   /home/umbrel/umbrel/app-data/meu-outro-site/
   ```

4. Faz commit e push para este repositório. A app aparece automaticamente na store do teu Umbrel.

## Padrão de cada app

Cada app segue a convenção da skill `umbrel-custom-app`:

- Sem `ports:` publicados no host (a porta é gerida pelo `app_proxy`).
- Sem `network_mode: host`.
- Sem mount do Docker socket.
- Dados persistidos em `${APP_DATA_DIR}/<app-id>/...`.
- Porta no manifesto (`port`) deve ser livre no teu Umbrel (não 80, 443, 2000, 3000, etc.).

## Sobre o `.env` e Cloudflare Tunnel

Não é necessário `.env` nas apps desta store quando usas a app oficial Cloudflare Tunnel do Umbrel para exposição externa. O túnel é gerido separadamente pela app do Umbrel.

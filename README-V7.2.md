# AETHERPLAY W3 — V7.2 (PWA Mobile)

Esta versão evolui o pacote V7.1 preservando a estrutura original, o Firebase, o jogo Aether Snake e a separação entre `index.html` (jogadores) e `admin.html` (administração).

## Novidades V7.2
- PWA: instalação pelo Chrome em Android compatível, com modo `standalone`.
- Ícones dedicados de 192×192 e 512×512 derivados do emblema cósmico AETHERPLAY.
- Service Worker com cache dos arquivos locais principais e fallback offline da página inicial.
- O tráfego externo (Firebase/API) não é interceptado nem armazenado pelo Service Worker.
- Manifest e registro do Service Worker com caminhos relativos, para funcionar também em subpastas do GitHub Pages.
- Banner de instalação, meta tags mobile, área segura do Android, foco acessível e ajustes de toque.
- A página Aether Snake também registra o mesmo Service Worker e aponta para o manifest.

## Como publicar
1. Extraia o ZIP.
2. Envie **o conteúdo** da pasta `AETHERPLAY-W3-V7.2` para o repositório/raiz publicada do site (mantenha `assets`, `css`, `games` e `js` juntos).
3. Publique em HTTPS (GitHub Pages ou Firebase Hosting).
4. Abra a URL no Chrome Android. Use o menu ⋮ → **Instalar app** ou **Adicionar à tela inicial**. O banner próprio aparece quando o Chrome disponibilizar o evento de instalação.
5. Após atualizar a versão publicada, feche e abra o app novamente para o Service Worker atualizar o cache.

## Importante sobre instalação e tela cheia
- O modo instalado `standalone` remove a barra de endereço do navegador. Barras de status/navegação do Android podem continuar visíveis conforme o aparelho e as configurações do sistema.
- O evento de instalação pode não aparecer em prévias, arquivos locais ou navegadores que não atendam aos critérios de instalação. HTTPS é obrigatório fora de `localhost`.
- O primeiro acesso precisa de internet. O cache offline é básico: guarda os arquivos locais do app; login, sincronização Firebase e dados remotos continuam dependendo de conexão.

## Firebase e segurança
- Os arquivos e regras Firebase existentes foram mantidos sem alteração nesta atualização.
- `admin.html` continua separado do `index.html`. A segurança real do admin depende das regras do Firebase e da validação de UID no backend/banco; esconder links não é controle de acesso.
- Não publique regras abertas. Faça backup e revise `database.rules.json` e `storage.rules` antes de aplicar.
- N-Coins, XP, recompensas e economia permanecem demonstrativos; não representam dinheiro ou tokens transferíveis.
- O cache não armazena respostas de Firebase, tokens de autenticação nem dados pessoais de API.

## Próximas etapas planejadas
V7.3: refinamento do dashboard e navegação mobile. V7.4: perfil, XP, níveis, recordes e conquistas. V7.5: central de jogos com categorias e favoritos. V8.0: módulos Web3 somente após desenho de segurança e backend confiável.

## Estrutura
- `index.html`: área pública.
- `admin.html`: painel administrativo separado.
- `games/aether-snake.html`: jogo Aether Snake.
- `service-worker.js`: cache PWA.
- `manifest.webmanifest`: instalação PWA.
- `assets/aetherplay-icon-192.png` e `assets/aetherplay-icon-512.png`: ícones instaláveis.
- `js/`, `css/`, `assets/`: recursos existentes do projeto.


## V7.2.1 — Correção de toque
- Rolagem vertical por gesto liberada na página principal e nas páginas do jogo.
- Tabuleiro do Aether Snake continua capturando deslizes para movimentar a cobrinha.
- Zoom por gesto reativado na página do jogo.
- Cache do service worker atualizado para entregar os arquivos corrigidos.

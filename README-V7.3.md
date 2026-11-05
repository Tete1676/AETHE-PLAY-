# AETHERPLAY W3 — V7.4

## Novidades
- Interface premium com identidade visual AETHERPLAY no destaque principal.
- Perfil com barra de progresso de XP e nível.
- Conquistas visuais por marcos de XP (100, 500, 1.000, 5.000 e 10.000).
- Navegação inferior fixa no celular para Início, Games, Missões, Ranking e Perfil.
- Cache PWA atualizado para V7.4.

## Instalação/atualização
1. Faça backup da versão atual.
2. Envie o conteúdo desta pasta para a mesma raiz do site, mantendo a estrutura.
3. Abra o site pelo Chrome em HTTPS e atualize.
4. Se o app instalado mantiver arquivos antigos, feche-o completamente e abra novamente; o service worker V7.4 substituirá o cache anterior.

## Observações
- XP e saldo continuam sendo lidos do perfil existente em `users/{uid}` no Firebase.
- As conquistas são indicadores visuais calculados com o XP já existente; não creditam XP nem N-Coins.
- Economia e recompensas continuam demonstrativas.
- `admin.html`, `js/admin.js`, `js/v7-admin.js`, Firebase e regras originais foram preservados.

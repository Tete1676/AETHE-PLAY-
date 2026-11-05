# Aetherplay W3 — V6.3

Atualização visual do projeto anterior Nexus Verse V5.6.1. A plataforma passa a se chamar **Aetherplay W3** e utiliza as duas imagens fornecidas: símbolo luminoso como logo e medalha Aetherplay como imagem ilustrativa do token.

## Identidade visual
- `assets/aetherplay-logo.png`: logo principal e favicon.
- `assets/aetherplay-token.png`: arte ilustrativa do token.
- Os fundos quadriculados externos foram recortados com máscara circular; confira a aparência nos dispositivos antes de publicar.

## Firebase
- Projeto configurado: `drama-damas` (agora destinado ao Aetherplay W3, conforme solicitado).
- Authentication: e-mail/senha.
- Realtime Database: dados de perfil, catálogo e configurações demo.
- Storage: capas de jogos, se o Storage estiver ativado e disponível no plano da conta.
- UID administrativo fixado nas regras: `vLSKhd1onRUzcYLEzK1o85uMkbg2`.

## Segurança e limitações
- O painel confere o UID após autenticação; as regras do Firebase são a barreira de segurança real.
- Revise e publique `database.rules.json` e `storage.rules` somente após salvar uma cópia das regras atuais. Elas são específicas para a estrutura deste projeto e podem precisar de adaptação se já houver outros dados no Firebase.
- Não há Cloud Functions neste pacote.
- Recompensas e saldos são demonstrativos; a recompensa automática de cadastro permanece desativada. Não use saldo editável pelo navegador como dinheiro ou token real.
- Não há conexão/transação real de carteira Web3 nesta versão.
- O Firebase Storage pode exigir configuração de faturamento conforme a política atual do Firebase e o estado da conta.

## Publicação
Hospede os arquivos em um servidor HTTPS que suporte módulos JavaScript. Para Firebase Hosting, use a CLI em um computador/ambiente com Node.js:
```bash
npm install -g firebase-tools
firebase login
firebase use drama-damas
firebase deploy --only database,storage,hosting
```
Este projeto não precisa de `firebase deploy --only functions`.

## Estrutura
- `index.html`: site dos jogadores.
- `admin.html`: painel administrativo separado.
- `css/style.css`: visual responsivo.
- `js/`: Firebase e lógica do site/painel.
- `assets/`: logo e arte do token.


## Novidades V6.3
- Painel de jogadores com leitura de perfis existentes no Realtime Database.
- Cadastro, pausa/reativação e exclusão de missões.
- Cadastro, pausa/reativação e exclusão de campanhas de recompensa.
- Seção inicial do ecossistema: Economy, NFT Gallery, Guilds e Transparency.
- Separação conceitual de APW planejado e N-Coins internos.

## Limitações importantes desta versão
- Missões e campanhas são registros administrativos; não existe motor seguro de conclusão de missão, anti-fraude ou crédito automático de saldo.
- O campo APW planejado é informativo: não executa transferências, não representa saldo on-chain e não altera contrato.
- A listagem de jogadores depende do formato real dos registros em `users`; só mostra os primeiros 100 registros retornados.
- O painel atual ainda escreve diretamente no Realtime Database com regras baseadas em UID. Para produção financeira, migrar ações sensíveis para backend com verificação de ID token, validação de dados, rate limiting e trilha de auditoria. Não abrir regras de escrita para público.
- Não há conexão MetaMask/WalletConnect, staking real, NFTs mintados ou APW negociável nesta versão.

## Regras do Realtime Database
Acrescente as seguintes permissões dentro de `nexus` nas regras existentes, mantendo o `.write` limitado ao UID administrativo:
```json
"missions": { ".read": true, ".write": "auth != null && auth.uid === 'vLSKhd1onRUzcYLEzK1o85uMkbg2'" },
"rewards": { ".read": true, ".write": "auth != null && auth.uid === 'vLSKhd1onRUzcYLEzK1o85uMkbg2'" }
```
Não substitua suas regras atuais sem fazer backup e revisar a estrutura completa.


## V6.3 — Central de manutenção
- Tela pública única em tela cheia, com ícone, título, descrição e previsão opcional.
- Categorias configuráveis no painel ADM: missões, recompensas, layout, menu, perfil, usuários, saldo/carteira, depósitos, saques, jogos, ranking, staking e NFTs.
- Aviso de proteção de dados opcional.
- A tela é exibida quando `nexus/maintenance.enabled` estiver ativo no Realtime Database.
- O conteúdo é um aviso de manutenção; não altera saldos nem bloqueia, por si só, chamadas diretas ao banco. Regras/backend devem proteger operações sensíveis.


## V7.4
Veja `README-V7.4.md` para ativar o compartilhamento opcional de recordes, consultar o histórico pessoal e publicar as regras Firebase.

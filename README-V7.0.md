# AETHERPLAY W3 V7.0 — Ecossistema Gamer

Baseada na V6.7 responsiva. Interface continua responsiva para celular, tablet e desktop.

## Novos módulos
- Recompensa diária em N-Coins demonstrativos.
- Baú semanal com modo fixo ou aleatório configurável pelo ADM.
- Solicitações de resgate ficam pendentes até aprovação administrativa. O ADM aprova e o sistema registra o crédito e o extrato N-Coins.
- Torneios com inscrições; a pontuação/resultados não são automaticamente confiáveis e exigem validação antes de premiar.
- Central de suporte com chamados e resposta administrativa.
- Notificações globais publicadas pelo ADM.
- Extrato individual N-Coins e registro de saldo anterior/posterior.

## Arquivos novos
- `js/v7-player.js`: módulos visíveis ao jogador.
- `js/v7-admin.js`: controles administrativos V7.
- `README-V7.0.md`: este guia.

## Publicação e regras
1. Faça backup do projeto e do Realtime Database.
2. Teste primeiro em um projeto Firebase de teste.
3. Revise `database.rules.json`, confirme o UID de administrador e só então publique as regras. As regras incluem leituras privadas e gravação administrativa; não as aplique sem conferir o UID.
4. Publique os arquivos estáticos no host (GitHub Pages).
5. Configure o domínio de hospedagem em Firebase Authentication > Authorized domains.

## Limitações importantes
- N-Coins são pontos internos de demonstração; APW não é distribuído.
- Pedidos de recompensa são aprovados manualmente pelo ADM. A aprovação atual é feita pelo painel autenticado com permissão do Firebase; para operação de produção, migrar o crédito para Cloud Functions/servidor com transação atômica e idempotência.
- O baú aleatório é sorteado no momento da aprovação administrativa, não no navegador do jogador.
- Inscrições e chamados são funcionais. Resultado de torneio precisa de validação humana; não existe anti-cheat robusto sem servidor autoritativo e telemetria do jogo.
- O módulo antifraude desta entrega é operacional básico: unicidade de pedido por período, controle de duplicidade, fila de aprovação e auditoria de crédito. Não detecta bots/IPs/dispositivos de forma confiável.
- Depósitos, saques, APW on-chain e pagamentos reais não estão habilitados.

## Estrutura de dados V7
- `nexus/v7Config`
- `nexus/v7Claims/{uid}/{claimId}`
- `nexus/v7Tournaments/{tournamentId}`
- `nexus/v7TournamentEntries/{tournamentId}/{uid}`
- `nexus/v7Tickets/{uid}/{ticketId}`
- `nexus/v7Notifications/{notificationId}`
- `nexus/v7Ledger/{uid}/{entryId}`
- `users/{uid}/balance` (N-Coins demo)

## Teste sugerido
1. Entrar como jogador em uma conta secundária.
2. Solicitar recompensa diária e baú semanal; confirmar que ficam pendentes.
3. Entrar no ADM e aprovar/recusar; conferir saldo e extrato do jogador.
4. Criar torneio, inscrever jogador e conferir a inscrição no ADM.
5. Abrir chamado e responder no ADM.
6. Publicar notificação e conferir na área do jogador.

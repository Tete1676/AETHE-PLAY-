# AETHERPLAY W3 V6.5 — correção de missões e melhorias do ADM

## O que mudou
- O site do jogador lê `nexus/missions` em tempo real e mostra somente missões ativas dentro do período configurado.
- O botão da missão exige login e registra participação/interesse em `nexus/missionSubmissions/{missionId}/{uid}`. Isso **não aprova conclusão nem credita saldo**.
- O ADM pode criar e editar missões, definir categoria, link, encerramento, recompensa, ativar/pausar e excluir.
- Busca de jogadores por nome, e-mail ou UID.
- Publicação/remoção de aviso global pelo ADM.
- Mensagens de erro de leitura das missões/recompensas no site.
- Cache-busting `?v=6.5` nos arquivos para evitar o navegador Android continuar usando JavaScript antigo.
- Regras do Realtime Database atualizadas: leitura da lista de usuários limitada ao UID ADM; participação de missão gravável somente no próprio UID; leitura de submissões para ADM.

## Atualização necessária
1. Faça backup do Firebase Realtime Database antes de substituir regras.
2. Publique os arquivos do site (`index.html`, `admin.html`, `js/`, `css/`, `assets/`) no host.
3. Revise e publique `database.rules.json` no projeto Firebase correto. Não publique regras sem conferir o UID ADM configurado.
4. Limpe o cache do navegador ou abra o site em aba anônima.
5. Crie uma missão ativa no ADM, entre no site com um usuário de teste e verifique se aparece.

## Limites importantes
- A participação apenas registra interesse; não existe prova automática de conclusão nem pagamento.
- XP, N-Coins e APW não são creditados por este fluxo.
- Não habilite créditos, saques ou transferências com regras abertas no cliente. Para isso, implemente backend confiável com validação, limites, idempotência e trilha de auditoria.
- A regra `users/.read` concede leitura da lista completa somente ao UID ADM configurado. Confirme que o UID é o seu antes de publicar.


## V6.6 — foco Android
- Interface mobile-first, otimizada para telas Android em orientação retrato.
- Áreas de toque maiores, campos sem zoom automático e rolagem horizontal controlada.
- Manifesto PWA para opção “Adicionar à tela inicial” no Chrome Android.
- Em telas grandes, a interface permanece em formato estreito de celular; isso é uma escolha visual, não uma barreira de segurança.
- Para instalar: publique o site em HTTPS, abra no Chrome Android, menu ⋮ e escolha “Adicionar à tela inicial” ou “Instalar app” quando disponível.
- O manifesto não habilita funcionamento offline nem transforma o site em APK.

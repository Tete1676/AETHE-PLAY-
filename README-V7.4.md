# AETHERPLAY W3 — V7.4

## Novidades
- Compartilhamento público de nick e recordes com ativação voluntária no perfil.
- Histórico pessoal dos últimos recordes enviados do Aether Snake.
- Hall da Fama comunitário com melhor pontuação por jogador.
- Integração do Aether Snake com Firebase Authentication e Realtime Database.
- Regras Firebase para cada jogador gravar apenas seus próprios recordes e preferência de privacidade.
- Cache PWA atualizado para V7.4.

## Publicação
1. Faça backup da versão atual.
2. Publique todos os arquivos mantendo as pastas.
3. No Firebase Realtime Database, publique o conteúdo atualizado de `database.rules.json` em Regras.
4. Abra o site em HTTPS, entre na conta e ative a opção de compartilhar recordes no Perfil.
5. Jogue Aether Snake conectado à internet. O resultado será enviado ao fim da partida se o compartilhamento estiver ativado.

## Privacidade e integridade
- O compartilhamento é opcional e pode ser desligado no Perfil.
- Com a opção desligada, o jogo não envia novas pontuações ao placar público.
- Os recordes enviados ficam associados ao UID do jogador no banco e o histórico pessoal só é lido pelo próprio usuário.
- O placar comunitário é baseado em pontuações enviadas pelo cliente e **não possui validação anti-cheat**. Não deve ser usado para distribuir prêmios, dinheiro, XP ou N-Coins.
- Esta versão não altera XP, saldo ou economia.
- Se as regras do Firebase não forem atualizadas, as gravações serão recusadas por segurança.

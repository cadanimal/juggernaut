# Juggernaut

Este software foi [descontinuado](http://blog.alexmaccaw.com/killing-a-library). O autor original aconselha sua substituição por [SSEs](//github.com/ninetwentyfour/Hospitium/issues/55). Não obstante, [**Hospitium**](//github.com/cadanimal/Hospitium) continua a usá-lo, ao menos por enquanto. O propósito deste fork é publicar as alterações que são necessárias para deploy em Heroku.

Mais informações devem ser consultadas no riquíssimo [README original](//github.com/maccman/juggernaut#juggernaut).

## Branches

- `master` ‒ em sincronia com o _upstream_
- `cadanimal` ‒ rebase do `master`, é o nosso branch de desenvolvimento
- `cadanimal-readme` ‒ rebase do `cadanimal`, para termos este README.md **em português**
- `cadanimal-deploy-public` ‒ rebase do `cadanimal`, para deploy no Heroku
- ~~`cadanimal-deploy-private`~~ ‒ quando existe, é rebase do `cadanimal-deploy-public` (ver [#SSL](#ssl))
- `travisberry` ‒ tem [cereja escolhida](//github.com/ninetwentyfour/juggernaut/commit/a75ccb84b5cef074c8f03feac86c26a28d4ce8d1) que minificou Javascript em `cadanimal-deploy-public`

Tenha em conta que os únicos branches onde preservamos o HEAD são: `master` e `cadanimal`.
O branch `travisberry` está neste respositório apenas por motivos históricos.

## Exemplo de deploy no Heroku

```sh
git clone git@github.com:cadanimal/juggernaut.git -b cadanimal
cd juggernaut
# alterações
git commit -a -m "DESCRIÇÃO DO COMMIT"
git checkout -b cadanimal-deploy-public cadanimal/cadanimal-deploy-public
git rebase cadanimal
git push heroku HEAD:master  # pressuposto que Heroku Toolbelt está configurado
```

## SSL

Se seu servidor usa SSL, siga as [instruções oficiais](//github.com/maccman/juggernaut#ssl) para geração de chaves. É sugerido fazer commit delas num branch como o `cadanimal-deploy-private` que seja sempre rebase de um branch `cadanimal-deploy-public`, que por sua vez é rebase do branch `cadanimal` (nosso fork).

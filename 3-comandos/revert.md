# Revert

O revert é um comando utilizado para reverter commits anteriores. Diferente do git reset, o git revert não altera a árvore de commits, ao invés disso, ele cria novos commits com mensagens no registro de log, informando quais commits foram revertidos. Isso faz com que ele seja a abordagem mais segura quando se deseja desfazer alterações na branch principal (main).

```bash
$ git revert <commit>
```

O reset recebe um commit como parâmetro, podendo ser utilizado com HEAD~ ou a HASH do commit.

## Opções

`-e` ou `--edit`

Permite alterar a mensagem do commit antes da reversão.

`--no-edit`

Não inicia o editor de mensagens do commit.

`-n` ou `--no-commit`

Executa a operação de reversão sem adicionar um commit.

## Comandos auxiliares

`—-continue`

Continua a operação em andamento. Comumente utilizado após resolver os conflitos gerados durante a operação.

`—-skip`

Ignora o commit atual e continua a operação.

`—-abort`

Cancela a operação abortando o comando.

## Exemplo

Para exemplificar o uso do comando, criamos uma nova pasta e iniciamos o git através do comando `$ git init`. Dentro da pasta, criamos um `arquivo.txt` com algumas linhas de texto, e para cada uma das linhas adicionamos um commit.

Executando o comando `$ git log`, o terminal nos apresenta os seguintes commits:

```
commit 71b26e3ee9f099a91e22bc339b788693458c4df5 (HEAD -> main)
Date: Wed May 8 11:34:13 2024 -0300

  terceiro commit

commit 42f689186678cd06700d074aa07fb4694a4e13a1
Date: Wed May 8 11:33:57 2024 -0300

  segundo commit

commit b6d27522f5ef188008857b145458b8008d420932
Date: 11:33:47 Wed May 8 11:33:42 2024 -0300

  primeiro commit
```

Neste momento, o conteúdo do nosso _arquivo.txt_ está da seguinte forma:

```txt
linha inserida no primeiro commit
linha inserida no segundo commit
linha inserida no terceiro commit
```

Agora, vamos executar o comando de reversão:

```bash
$ git revert HEAD~0
```

O comando acima irá desfazer o último commit presente na árvore de commits. Além disso, ele também irá adicionar um novo, com as informações de qual commit foi desfeito.

```
commit 5bf52ac3b69588613b15fa68009c9962bbd357ae (HEAD -> main)
Date: Wed May 8 11:35:32 2024 -0300

  Revert "terceiro commit"                                        <-- mensagem do revert

  This reverts commit 71b26e3ee9f099a91e22bc339b7886934584df5.    <-- hash do commit desfeito

commit 71b26e3ee9f099a91e22bc339b788693458c4df5
Date: Wed May 8 11:34:13 2024 -0300

  terceiro commit

commit 42f689186678cd06700d074aa07fb4694a4e13a1
Date: Wed May 8 11:33:57 2024 -0300

  segundo commit

commit b6d27522f5ef188008857b145458b8008d420932
Date: Wed May 8 11:33:42 2024 -0300

  primeiro commit
```

Com isso, a última linha do nosso arquivo foi removida, pois ela havia sido adicionada no terceiro commit.

Para finalizar o nosso exemplo, vamos adicionar mais commit e, em seguida, executar o comando:

```bash
$ git revert HEAD~3
```

Uma nova operação será iniciada, e com ela teremos alguns conflitos para resolver. Após aceitas as altearções recebidas, podemos usar o comando auxiliar `--continue` para finalizar a operação.

```bash
$ git revert --continue
```

Isso fará com que o segundo commit e todos os posteriores sejam desfeitos, voltando o conteúdo do nosso arquivo para o estado do primeiro commit, ou seja, ele terá apenas a "linha inserida no primeiro commit".

Acessando novamente o log, teremos os seguintes commits na nossa árvore:

```
commit 99d8d5a91bd570adee1371eacab8a053f998e02c (HEAD -> main)
Date: Wed May 8 11:39:54 2024 -0300

  Revert "segundo commit"

  This reverts commit 42f689186678cd06700d074aa07fb4694a4e13a1.

commit 2d3da358452ec7be9eb8229c2d70ee841b6b7d45
Date: Wed May 8 11:38:00 2024 -0300

  commit depois do revert

commit 5bf52ac3b69588613b15fa68009c9962bbd357ae (HEAD -> main)
Date: Wed May 8 11:35:32 2024 -0300

  Revert "terceiro commit"

  This reverts commit 71b26e3ee9f099a91e22bc339b7886934584df5.

commit 71b26e3ee9f099a91e22bc339b788693458c4df5
Date: Wed May 8 11:34:13 2024 -0300

  terceiro commit

commit 42f689186678cd06700d074aa07fb4694a4e13a1
Date: Wed May 8 11:33:57 2024 -0300

  segundo commit

commit b6d27522f5ef188008857b145458b8008d420932
Date: Wed May 8 11:33:42 2024 -0300

  primeiro commit
```

Para mais opções e comandos auxiliares, acesse a documentação do [Git Revert](https://git-scm.com/docs/git-revert/pt_BR).

Ir para: [3.12. Fetch](../3-comandos/fetch.md)

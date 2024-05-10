# Cherry Pick

O comando `cherry-pick` é usado para pegar um commit específico de uma branch e aplicar em outra branch.

## Exemplo

Vamos supor que você está trabalhando em uma branch `feature` e você precisa aplicar um commit específico da branch `main` na sua branch `feature`. Para isso, você pode usar o comando `cherry-pick`:

```bash
git cherry-pick <hash-do-commit>
```

## Como usar

Dando um exemplo de estado de ramificação:

```
a - b - c - d   Main
      \
        e - f - g Feature
```

Se você quiser aplicar o commit `c` na branch `Feature`, você pode usar o comando `cherry-pick`:

```bash
git cherry-pick c
```

O resultado será:

```
a - b - c - d   Main
      \
        e - f - g - c' Feature
```

## Intervalo de commits

Você também pode usar o comando `cherry-pick` para aplicar um intervalo de commits. Por exemplo, se você quiser aplicar os commits `b` e `c` na branch `Feature`, você pode usar o comando `cherry-pick`:

Há algumas formas de fazer isso:

```sh
# opção 1	
git cherry-pick b^..d 
# opção 2
git cherry-pick b..d
```

Na opção 1, indica que todos os commits entre o commit `b` (exclusivo) e o commit `d` (inclusivo) serão aplicados na branch `Feature`.

O `^` apos o commit `b` indica que o commit `b` não será aplicado.

Então irá ser aplicado todas as alterações entre o commit `b` e o commit `d` na branch `Feature`.

O resultado será:

```
# Opção 1: b^..d
a - b - c - d   Main
      \
        e - f - g - c' - d' Feature
```

Na opção 2, indica que todos os commits entre o commit `b` (inclusivo) e o commit `d` (inclusivo) serão aplicados na branch `Feature`, mas não irá aplicar o commit `b`.

O resultado será:

```
# Opção 2: b..d
a - b - c - d   Main
      \
        e - f - g - b' - c' - d' Feature
```


## Conflitos

Pode haver casos em que o Git reconheça conflitos entre o commit que esta sendo cherry-picked e as mudanças da branch de destino, nesse caso você precisará resolver manualmente as mudanças.

Depois que resolver os conflitos, você indica que as mudanças foram resolvidas com o comando:

```bash
git add
git cherry-pick --continue
```

Ao executar o comando, o Git irá criar um novo commit com as mudanças resolvidas e que o git pode continuar no processo de aplicação dos commits.

Mas caso você queira abortar o cherry-pick, você pode usar o comando:

```bash
git cherry-pick --abort
```


## Comandos complementares

O comando `cherry-pick` pode ser usado em conjunto com outros comandos, conhecidas como `flags`, como por exemplo:


`git cherry-pick --edit <hash-do-commit>` - Abre o editor de texto para editar a mensagem do commit

`git cherry-pick --signoff <hash-do-commit>` - Adiciona a assinatura do autor do commit

`git cherry-pick --no-commit <hash-do-commit>` - Aplica o commit sem fazer o commit

`git cherry-pick --continue <hash-do-commit>` - Continua o cherry-pick após resolver os conflitos

`git cherry-pick --abort <hash-do-commit>` - Cancela o cherry-pick

`git cherry-pick --quit <hash-do-commit>` - Sai do cherry-pick

`git cherry-pick --ff <hash-do-commit>` - Aplica o commit com fast-forward

`git cherry-pick --no-ff <hash-do-commit>` - Aplica o commit sem fast-forward

`git cherry-pick --allow-empty <hash-do-commit>` - Permite que o cherry-pick seja feito em um commit vazio

`git cherry-pick --keep-redundant-commits <hash-do-commit>` - Mantém os commits redundantes

`git cherry-pick --mainline <hash-do-commit>` - Define a linha principal de desenvolvimento

`git cherry-pick --quiet <hash-do-commit>` - Não mostra o log do cherry-pick

`git cherry-pick --verbose <hash-do-commit>` - Mostra o log do cherry-pick

`git cherry-pick --progress <hash-do-commit>` - Mostra o progresso do cherry-pick

`git cherry-pick --no-progress <hash-do-commit>` - Não mostra o progresso do cherry-pick


Sim, existem várias possibilidades de uso do comando `cherry-pick`. Você pode ver mais detalhes sobre o comando `cherry-pick` na [documentação oficial](https://git-scm.com/docs/git-cherry-pick/pt_BR).

Ir para: [4.1. Gitflow - O que é Git Flow](../4-gitflow/o-que-e-gitflow.md)

# Reset

Com o comando reset podemos realizar alterações na árvore dos commits de uma branch, possibilitando a utilização dos arquivos ou o descarte total do que foi alterado.

O reset recebe como parametro uma hash de commit ou um branch específica (origin ou local);

## Hard

Com o `--hard` você sobreescreve a árvore de commits do seu local para a árvore de commits do `origin/master`, descartando todas as alterações relizadas localmente que não foram empurradas para o repositório remoto.

```bash
git reset --hard origin/master
```

## Soft

Com o `--soft` podemos voltar para uma hash de um commit mantendo os arquivos editados em 'stable', possibilitando a edição dos arquivos e a reorganização da árvore de commits.

```bash
git reset --soft d60329e
```

Ir para: [3.11. Revert](../3-comandos/revert.md)

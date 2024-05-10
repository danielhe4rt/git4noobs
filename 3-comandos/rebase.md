# Rebase

O comando rebase é responsavel por reorganizar os commits de uma branch, nos permitindo alguns comando nos commits selecionados.
Mais opções deste comando na [documentação do git](https://git-scm.com/docs/git-rebase).
O mais comum do uso do rebase é para mesclarmos commit, agrupando alterações em apenas um.

## Rebase Interativo

```bash
git rebase -i HEAD~2 # o 2 representa o numero de commits que o comando irá buscar para o rebase.
```

Após rodar este comando é apresentado em seu editor padrão do git, um arquivo para você editar os comandos, e executar a tarefa desejada.

```txt
1 pick d93ec63 Add dockerfile and docker-compose.yml
2 pick 3be8acd Add dockerfile and docker-compose.yml
3
4 # Rebase 7b870a1.git commit --amend.3be8acd onto 7b870a1 (2 commands)
.
.
.
```

Commandos:

* p, pick <commit> = usa o commit
* r, reword <commit> = usa o commit, mas edita a mensagem do commit
* e, edit <commit> = usa o commit, mas para alterar
* s, squash <commit> = usa o commit, mas junta com o commit anterior
* f, fixup <commit> = igual ao commando "squash", mas discarta a mensagem do commit
* x, exec <command> = run command (the rest of the line) using shell
* b, break = para no commit, apenas continua o rebase apost 'git rebase --continue'
* d, drop <commit> = remove o commit
* l, label <label> = Cria um rotulo de HEAD
* t, reset <label> = reseta o HEAD por um label
* m, merge [-C <commit> | -c <commit>] <label> [# <oneline>] = Cria um merge commit usando as mensagens dos commits. Use a opção -c <commit> para reescrever a mensagem do commit.

Para juntarmos os 2 commits em apenas 1, precisamos alterar o comando do segundo commit para o `squash` ou `fixup`, dependedo se quiser descartar ou não a mensagem do commit.

```txt
1 pick d93ec63 Add dockerfile and docker-compose.yml
2 squash 3be8acd Add dockerfile and docker-compose.yml
3
4 # Rebase 7b870a1..3be8acd onto 7b870a1 (2 commands)
.
.
.
```

Após salvar o comando será exibido outro arquivo contendo as mensagens dos commit selecionados. Podemos editar toda a mensagem e submensagem do commit final.

```txt
1 # This is a combination of 2 commits.
2 # This is the 1st commit message:
3
4 Mensagem final editada
5
6 # This is the commit message #2:
7
8 # Add dockerfile and docker-compose.yml
9
```

## Mais comandos utlizados

Após localizar um conflito que o git não conseguiu resolver precisamos editar os arquivos manualmente, escolhendo o código correto e após aplicar as alterações utilizando o comando `git add .` só após esta operação podemos continuar com o rebase.

```bash
git rebase --continue
```

Quando estamos mesclando diversos commits podemos querer pular alguns conflitos para serem resolvidos futuramente, para isso utilizamos o `skip`. (usar com parcimônia)

```bash
git rebase --skip
```

Caso erremos durante o rebase podemos abortá-lo para não perder o código e começar novamente.

```bash
git rebase --abort
```

Ir para: [3.10. Reset](reset.md)

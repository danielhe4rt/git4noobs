# Log

Este comando puxa o histórico de alterações que o projeto teve até o momento. Mostrando da alteração mais recente para a mais antiga, assim você pode entender as mudanças que outras pessoas realizaram ou mudanças que você próprio fez.

Você pode usar as teclas de seta para cima e para baixo para percorrer os registros e pressionar o Q para retornar ao terminal.
```
$ git log

Estrutura

commit: codigo hash
Autor: autor da alteração
Data: data da alteração
 Mensagem do commit
```

Verificar o que foi mudado nos arquivos
```
$ git log -p
```

Mostrar estatísticas de todos os commits como:
    - Hash completa
    - Data
    - Comentário
    - Quantidade de alterações
```
$ git log --stat
```

Mostrar o commit inteiro de forma reduzida
```
$ git log --oneline
```

Mostrar histórico de alterações filtrando por um autor especifico
```
$ git log --author=usuario
```

Exibir o historico das das ultimas 2 alterações
```
$ git log -p -2
```

exibir o histórico de uma arquivo em especifico
```
git log -- <caminho_do_arquivo>
```

Ir para: [3.14. Stash](stash.md)

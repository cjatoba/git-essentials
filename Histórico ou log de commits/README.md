## Listar o log de commits:
```git
git log
```

## Listar o log de commits juntamente com as diferenças (diff) de cada arquivo:
```git
git log -p
```

## Lista o log de commits com cada commit ocupando apenas uma linha:
```git
git log --oneline
```

## Lista o log de commits de um arquivo específico (Substituir path/to/myfile pelo caminho e nome do arquivo):
```git
git log --follow -- path/to/myfile
```

## Busca por palavra ou frase dentro do código de cada commit (Substituir Filter pela palavra ou frase a ser buscada):
```git
git log -S Filter
```

## Busca por palavra ou frase nas mensagens de commit (Substituir keyword pela palavra ou frase a ser buscada):
```git
git log --grep keyword
```

## Filtra o resultado do git log por um ou mais autores:
```git
git log --author='\(Adam\)\|\(Jon\)'
```

## Limita o periodo do log em um período (Primeiro exemplo) ou antes ou depois de uma determinada data (Segundo e Terceiro exemplo):
```git
git log --since=1.month.ago --until=3.weeks.ago
git log --before="1 Jan 2020"
git log --after="1 Jan 2020"
```

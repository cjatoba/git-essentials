## Gitflow

![image](https://wac-cdn.atlassian.com/dam/jcr:cc0b526e-adb7-4d45-874e-9bcea9898b4a/04%20Hotfix%20branches.svg?cdnVersion=76)

## Fluxo geral

- Uma ramificação develop é criada a partir da main
- Uma ramificação de lançamento é criada a partir da ramificação de desenvolvimento
- As ramificações de recurso são criadas a partir da ramificação de desenvolvimento
- Quando um recurso é concluído, ele é mesclado na ramificação de desenvolvimento
- Quando a ramificação release é feita, é feito o merge dela na ramificação develop e na principal
- Se for detectado um bug na main, uma ramificação de hotfix vai ser criada a partir da main
- Depois que o hotfix for concluído, ele passa por merge para a ramificação develop e à main

Iniciar a git no projeto e criar as ramificações:
```git
git flow init
```

## Ramificações de feature

Criar branch feature:
```git
git flow feature start feature_branch
```

Finalizar a feature e mesclar com a branch develop:
```git
git flow feature finish feature_branch
```

## Ramificações de release

Após a finalização das features da branch develop, iniciar a ramificação de release:
```git
git flow release start 0.1.0
```

Finalizar a ramificação de release:
```git
git flow release finish '0.1.0'
```

### Ramificações de hotfix

As ramificações de manutenção ou de “hotfix” são usadas para corrigir com rapidez lançamentos de produção.

Criar ramificação de hotfix:
```git
git flow hotfix start hotfix_branch
```

Finalizar a ramificação de hotfix
```git
git flow hotfix finish hotfix_branch
```


## Fontes de informação

- https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow#:~:text=Gitflow%20Workflow%20%C3%A9%20um%20design,robusta%20para%20gerenciar%20projetos%20maiores

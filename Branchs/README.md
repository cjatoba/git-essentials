## Branchs

- Listar branchs do repositório local, a branch em que estamos trabalhando terá um * na frente
```git
git branch
```

- Listar branchs do repositório local e remoto
```git
git branch -a
```

- Mudar de branch
```git
git checkout nomeDaBranch
```

- Criar nova branch e mudar para ela
```git
git checkout -b nomeDaBranch
```

- Excluir branch local
```git
git branch -d nomeDaBranch
```

- Remove remote branch
```git
git push origin --delete branch_name
```

- Renomear branch atual
```git
git branch -m NovoNomeDaBranch
```

- Renomear branch remota
```git
//Acessar a branch que será alterada:
git checkout old-branch-name

//Renomear a branch local
git branch -m new-branch-name

//Remover a branch remota
git push origin --delete old-branch-name

//Enviar a nova branch
git push origin -u new-branch-name
```

- Renomear branch diferente da atual
```git
git branch -m NomeAtualDaBranch NovoNomeDaBranch
```

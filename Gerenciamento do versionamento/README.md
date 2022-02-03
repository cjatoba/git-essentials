## Gerenciamento do versionamento

- Puxar atualizações do repositório remoto para o local
```git
git pull origin nomeDaBranch
```

- Verificar o status do projeto:
```git
git status
```

- Adicionar arquivos na área de stage
```git
git add .
```

- Commitar alterações
```git
git commit -m "Informação sobre o commit"
```

- Verificar o histórico de commits
```git
git log
```

- Verificar alterações em um commit em específico (O --color destaca as alterações em verde e vermelho para facilitar a visualização);
```
git show --color id_do_commit
```

- Salva as alterações ainda não commitadas "que estão da área de stage" e remove essas alterações do projeto
```git
git stash save "mensagem para lembrar o que foi salvo aqui"
```

- Lista todos os stashes salvos
```git
git stash list
```

- Carrega um stash salvo, nesse exemplo será carregado o stash {2} com base na saída do comando `git stash list`
```git
git stash pop stash@{2}
```

- Exibe o diff de um stash específico, nesse exemplo será carregado o stash {2} com base na saída do comando `git stash list`
```git
git stash show -p stash@{2}
```

- Voltar arquivo para o estado original desde o último commit
```git
git checkout -- arquivo.txt
```

- Navegar entre commits, voltando o código a versões de commits anteriores:
```git
git checkout id_do_commit
```

- Voltar o código a versão original de uma branch:
```git
git checkout nome_da_branch
```

- Subir commits para repositório remoto
```git
git push -u origin NomeDaBranch
```

### (Aviso) Comandos perigosos que mexem na estrutura do histórico de versionamento

- Resetar o repositório para o estado do último commit (O commit será desfeito mas as alterações nos arquivos ainda ficarão. Neste caso é necessário fazer um novo commit com o conteúdo do commit desfeito)
```git
git reset HEAD~1
```

- Resetar o repositório para o estado do último commit desfazendo as alterações nos arquivos (O commit atual e todas as alterações dele serão removidas)
```git
git reset --hard HEAD~1
```

- Retornar o projeto para um commit anterior (Perde todos os commits na frente dele)
```git
git reset --hard idDoCommit
```

- Criar um novo commit que faz o reverso do commit especificado (Pode ocorrer conflitos nesse processo)
```git
git revert idDoCommit
```

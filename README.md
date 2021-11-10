# Git Essentials

Este repositório tem o objetivo de centralizar dicas e informações objetivas sobre o git, como fluxo de trabalho, exemplo de comandos etc.

## Instalação

- No Linux, seguir as orientações do endereço https://git-scm.com/download/linux
- No MAC, seguir as orientações do endereço https://git-scm.com/download/mac
- No Windows, baixar o executável no endereço https://git-scm.com/download/win

## Configurações

- Configurar o e-mail:
```
git config --global user.email "meuemail@mail.com"
```

- Configurar o nome do usuário:
```
git config --global user.name "meu nome"
```

- Configuração para salvar o usuário e senha de forma permanente:
```
git config --global credential.helper store
```

- Listar todas as configurações:
```git
git config -l
```

- Remover configuração global (Neste exemplo serão removidos o user.name e user.email):
```git
git config --global --unset user.name
git config --global --unset user.email
```

## Inicializar o git no projeto

Para um projeto novo já existente na máquina local, acessar a raiz do projeto e utilizar o comando:
```git
git init
```

Caso queira clonar um repositório remoto já existente:
```git
git clone enderecoDoRepositorioRemoto
```

## Fluxo de trabalho

1. Acessar o repositório principal do projeto (Repositório da empresa ou projeto que queira contribuir);
2. Fazer um fork do projeto principal para o repositório pessoal (Ao acessar o projeto no canto superior direito clicar no botão "Fork");
3. Clonar o repositório pessoal para máquina local 
```git
git clone <url do repositório do projeto da sua conta pessoal no git>
```
4. Verificar em qual branch está atualmente (Geralmente será a branch master ou main, nos exemplos posteriores vamos considerar como branch main);
```git
git branch
```
5. Criar uma branch onde serão realizadas as modificações, neste exemplo estamos nomeando esta branch como implementacao (Nunca fazer as modificações na branch principal);
```git
git checkout -b implementacao
```
6. Configurar o repositório remoto (Repositório acessado no passo 1) para onde será enviado posteriormente o pull request (upstream foi o nome dado neste exemplo ao repositório remoto, mas pode ser qualquer outro nome);
```git
git remote add upstream <url para o repositório da sua organização>
```
7. Realizar as modificações necessárias na branch criada no passo 5 e ao terminar adicionar as alterações na área de stage;
```git
git add .
```
8. Commitar as modificações
```git
git commit -m "Descrição do que foi realizado"
```
9. Acessar a branch principal e com o comando pull puxar o estado atual dela para verificar se houveram modificações enquanto estávamos trabalhando na nossa branch local, e resolver quaisquer eventuais conflitos (Lembrando que upstream foi o nome dado ao repositório remoto no passo 6):
```git
git checkout master
git pull upstream main
```
10. Fazer o merge da branch principal com a branch local que realizamos as modificações:
```git
git checkout implementacao
git merge main
```
11. Enviar nossas modificações para o nosso repositório remoto pessoal (Lembrando de sempre dar git add . e git commit antes de dar o push.):
```git
git push origin implementacao
```
12. Criar um pull request no repositório principal do projeto (O mesmo repositório acessado no passo 1)

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

- Resetar o repositório para o estado do último commit (O commit será desfeito mas as alterações nos arquivos ainda ficarão. Neste caso é necessário fazer um novo commit com o conteúdo do commit desfeito)
```git
git reset HEAD~1
```

- Criar um novo commit que faz o reverso do commit especificado (Pode ocorrer conflitos nesse processo)
```git
git revert idDoCommit
```

- Resetar o repositório para o estado do último commit desfazendo as alterações nos arquivos (O commit atual e todas as alterações dele serão removidas)
```git
git reset --hard HEAD~1
```

- Retornar o projeto para um commit anterior (Perde todos os commits na frente dele)
```git
git reset --hard idDoCommit
```

- Subir commits para repositório remoto
```git
git push -u origin NomeDaBranch
```

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

- Excluir branch
```git
git branch -d nomeDaBranch
```

- Renomear branch atual
```git
git branch -m NovoNomeDaBranch
```

- Renomear branch diferente da atual
```git
git branch -m NomeAtualDaBranch NovoNomeDaBranch
```

## Repositórios

- Lista os repositórios remotos:
```git
git remote -v
```

- Adicionar repositório remoto (origin neste exemplo será o alias que daremos ao repositório remoto, por convensão origin mas pode ser outro nome):
```git
git remote add origin https://github.com/usuario/repositorio
```

- Remover repositório remoto:
```git
git remote rm nomeDoRepositorio
```

## Resolução de conflitos

Os conflitos ocorrem quando enquanto modificamos algum arquivo em nosso repositório local, outro desenvolvedor realiza alguma alteração na mesma linha do arquivo que modificamos, então ao realizar o `git push` o git informa que há um conflito. Nesses casos é necessário resolver o conflito manualmente seguindo os passos abaixo:

 1. Puxar a versão do repositório remoto para o repositório local
  ```git
  git pull origin main
  ``` 

 2. Abrir o arquivo que o GIT indicou que há conflitos, o arquivo conterá algumas informações:
```
<<<<<<< HEAD
  Aqui ficará o código que editamos
*******
  Aqui ficará o código que foi editado por outro desenvolvedor
>>>>>>> dsadad6975970875750950975975s975c97597597
```
 
 3. Remover as tags de marcação do GIT, manter apenas o código que o arquivo deve conter e salvar o arquivo;
 
 4. Adicionar o arquivo modificado na área de stage
 ```git
 git add .
 ```
 
 5. Commitar
 ```git
 git commit -m "Resolução de conflitos"
 ```
 
 6. Subir as alterações para o repositório rmeoto
 ```
 git push -u origin main
 ```

## Configurar diretório como um repositório remoto

Vamos utilizar como exemplo um diretório com o nome localhub que se encontra no caminho F:

Acessar o diretório via terminal e digitar o comando abaixo:
```
cd F:/localhub
```
```git
git init --bare
```

Para clonar um projeto deste repositório:
```git
git clone F:\localhub
```

Acessar o diretório criado na máquina local e nele inicializar o git
```git
git init
```

Configurar o repositório remoto
```
git remote add localhub F:
```

Para subir as alterações seguir os passos normais do git alterando apenas o nome do repositório remoto de origin para localhub

## Gitflow

Iniciar a git no projeto e criar as ramificações:
```git
git flow init
```

Criar branch feature:
```git
git flow feature start feature_branch
```

Finalizar a feature e aesclar com a branch develop:
```git
git flow feature finish feature_branch
```

Após a finalização das features da branch develop, iniciar a ramificação de release:
```git
git flow release start 0.1.0
```

## Fontes de informação

https://git-scm.com/book/pt-br/v2
https://medium.com/@danilocarva9/git-workflow-guia-passo-a-passo-9dfda241ca1
https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow#:~:text=Gitflow%20Workflow%20%C3%A9%20um%20design,robusta%20para%20gerenciar%20projetos%20maiores.

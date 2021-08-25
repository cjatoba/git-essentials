# models_git

Lista de comandos e dicas git

Documentação do git: https://git-scm.com/book/pt-br/v2

## Instalação

- No Linux, seguir as orientações do endereço https://git-scm.com/download/linux
- No MAC, seguir as orientações do endereço https://git-scm.com/download/mac
- No Windows, baixar o executável no endereço https://git-scm.com/download/win

## Configurações iniciais

- Configura o e-mail:
```
git config --global user.email "meuemail@mail.com"
```

- Configura o nome do usuário:
```
git config --global user.name "meu nome"
```

- Configuração para salvar o usuário e senha de forma permanente:
```
git config --global user.name "meu nome"
```

## Inicializar o git no projeto

No terminal acessar a raiz do projeto e utilizar o comando:
```git
git init
```

Caso queira clonar um repositório remoto já existente:
```git
git clone enderecoDoRepositorioRemoto
```

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

- Retornar o projeto para um commit anterior (Perde todos os commits posteriores)
```git
git reset --hard hashDoCommit
```

- Subir commits para repositório remoto
```git
git push -u origin NomeDaBranch
```

## Branchs

- Listar branchs do repositório local
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

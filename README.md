# Git Essentials

Este repositório tem o objetivo de centralizar dicas e informações objetivas sobre o git, como fluxo de trabalho, exemplo de comandos etc.

## Instalação

- No Linux, seguir as orientações do endereço https://git-scm.com/download/linux
- No MAC, seguir as orientações do endereço https://git-scm.com/download/mac
- No Windows, baixar o executável no endereço https://git-scm.com/download/win

## Inicializar o git no projeto

Para um projeto novo já existente na máquina local, acessar a raiz do projeto e utilizar o comando:
```git
git init
```

Caso queira clonar um repositório remoto já existente:
```git
git clone enderecoDoRepositorioRemoto
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

3. Aplicar as alterações locais descartando as remotas
```git
git checkout --ours file_name
```

4. Aplicar as alterações remotas descartando as locais
```git
git checkout --theirs file_name
```
 
 5. Remover as tags de marcação do GIT, manter apenas o código que o arquivo deve conter e salvar o arquivo;
 
 6. Adicionar o arquivo modificado na área de stage
 ```git
 git add .
 ```
 
 7. Commitar
 ```git
 git commit -m "Resolução de conflitos"
 ```
 
 8. Subir as alterações para o repositório remoto
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

## Correção de erros

### fatal: refusing to merge unrelated histories

Desde o Release 2.9.0, o Git parou de permitir o merge automático de projetos que possuem históricos Git diferentes.

O erro fatal: refusing to merge unrelated histories geralmente acontece quando você tenta fazer o git pull de um repositório remoto, mas o seu repositório local possuí um histórico de commits, branches, etc, diferente do que está no repositório remoto.

Para permitir que o Git faça o merge de dois projetos com históricos diferentes, é só passar o parâmetro --allow-unrelated-histories quando for fazer o pull, assim:

```git
git pull origin main --allow-unrelated-histories
```

## Fontes de informação

- https://git-scm.com/book
- https://medium.com/@danilocarva9/git-workflow-guia-passo-a-passo-9dfda241ca1
- https://community.umbler.com/br/t/resolvendo-o-erro-fatal-refusing-to-merge-unrelated-histories-no-git/657

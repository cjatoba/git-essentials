# models_git

Lista de comandos e dicas git

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

## Resolução de conflitos

Os conflitos ocorrem quando realizamos um ´git pull´ ou git ´git clone´ e enquanto modificamos algum arquivo em nosso repositório local, outro desenvolvedor realiza alguma alteração na mesma linha do arquivo que modificamos, então ao realizar o `git push` o git informa que há um conflito. Nesses casos é necessário resolver o conflito manualmente seguindo os passos abaixo:

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

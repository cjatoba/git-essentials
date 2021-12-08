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

# models_git

Lista de comandos e dicas git

## Configurações iniciais

- Configura o e-mail:
```
git config --global user.email "meuemail@mail.com"
```

- Configura o musuário:
```
git config --global user.name "meu nome"
```


- Configuração para salvar o usuário e senha de forma permanente:
```
git config --global user.name "meu nome"
```

## Resolução de conflitos

Os conflitos ocorrem quando realizamos um ´git pull´ ou git ´git clone´ e enquanto modificamos algum arquivo em nosso repositório local, outro desenvolvedor realiza alguma alteração na mesma linha do arquivo que modificamos, então ao realizar o `git push` o git informa que há um conflito. Para resolver o conflito os passos abaixo devem ser seguidos:

 1. Puxar as alterações do repositório remoto para o repositório local:
 ```git
 git pull
 ```
 
 2. 

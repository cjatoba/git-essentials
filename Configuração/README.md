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

- Habilitar as saídas do terminal com cores (Caso não esteja habilitado por padrão)
```git
git config --global color.ui true
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

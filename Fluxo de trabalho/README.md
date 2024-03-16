## Fluxo de trabalho

1. Acessar o repositório principal do projeto (Repositório da empresa ou projeto que queira contribuir);
2. Caso seja um repositório de terceiros fazer um fork do projeto principal para o repositório pessoal (Ao acessar o projeto no canto superior direito clicar no botão "Fork");
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
git remote add origin <url para o repositório da sua organização>
```
7. Realizar as modificações necessárias na branch criada no passo 5 e ao terminar adicionar as alterações na área de stage;
```git
git add -A
```
8. Commitar as modificações
```git
git commit -m "Descrição do que foi realizado"
```
9. Acessar a branch principal e com o comando pull puxar o estado atual dela para verificar se houveram modificações enquanto estávamos trabalhando na nossa branch local, e resolver quaisquer eventuais conflitos (Lembrando que upstream foi o nome dado ao repositório remoto no passo 6):
```git
git checkout main
git pull origin main
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

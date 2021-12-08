## Correção de erros

### fatal: refusing to merge unrelated histories

Desde o Release 2.9.0, o Git parou de permitir o merge automático de projetos que possuem históricos Git diferentes.

O erro fatal: refusing to merge unrelated histories geralmente acontece quando você tenta fazer o git pull de um repositório remoto, mas o seu repositório local possuí um histórico de commits, branches, etc, diferente do que está no repositório remoto.

Para permitir que o Git faça o merge de dois projetos com históricos diferentes, é só passar o parâmetro --allow-unrelated-histories quando for fazer o pull, assim:

```git
git pull origin main --allow-unrelated-histories
```

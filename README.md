# Principles

## CODE MANAGEMENT PRINCIPLES

O desenvolvimento de aplicações na SumOne passa pelos seguintes princípios:

* **In GIT We Push**
Nós damos push, todo dia, toda hora, compulsivamente. 
Dessa forma, mantemos sempre nosso trabalho seguro e podemos trabalhar em equipe efetivamente.

* **GIT UP and Get on up**
Usamos a gem [**git-up**](https://github.com/aanand/git-up) para nos mantermos atualizados e sermos bons cidadãos, nós não "merjamos", "rebaseamos".


# Workflow

## Git Workflow

Para começar uma nova Feature associado a uma issue é necessário seguir os seguintes passos:

### Criando nova Feature

Garanta que o seu repositório de Development esteja atualizado:

```
# acessar a pasta onde está o código fonte
gem install git-up --no-doc --no-ri # caso não esteja instalado
git-up
```

Criar uma nova branch:

```
git checkout -b nome_branch
```

Realizar as alterações necessárias no código, e ao final seguir os seguintes passos:

```
git status # para verificar quais foram as atualizações realizadas
git add -A # adicionar os arquivos alterados para efetuar o commit
git commit -m "Descrição das alterações"
git up # atuliza todos os seus branchs
git merge development # para trazer todas as alterações realizadas no development para o seu branch e evitar conflitos.
git push origin nome_branch # efetua o "push" para o GitHub
```

Entrar na página do repositório onde foi realizado o push e criar um Pull Request https://help.github.com/articles/using-pull-requests/ **Atentar na escolha do base:, sempre selecionar development.**

Na descrição do pull request criado incluir uma das palavras chave para linka-lo a Issue https://help.github.com/articles/closing-issues-via-commit-messages/

Feito isso agora é aguardar para que alguem verifique o seu request e efetue o Merge ou seja necessário efetuar algum ajuste na alteração enviada. Caso isso ocorra, quem estiver analisando vai inserir um comentário no pull request.

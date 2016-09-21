# Gestão de Código

## Git

Utilizamos [Git](http://git-scm.com/) para fazer a gestão do nosso código.

### Criando uma nova feature

A cada nova feature, criamos uma branch chamada `feature/something`, com um nome descritivo
da funcionalidade que estamos desenvolvendo (em inglês). Essa branch deve ser criada a partir
da `master`.

```
git checkout master
git checkout -b feature/something
git push -u
```

Escreva o código e faça seus commits. Procure fazer commits logicamente separados para facilitar
o entendimento da evolução do código. Você pode utilizar o `git add -p` para adicionar apenas
partes das suas alterações ao índice, antes de fazer seu commit.

```
git add -p
git commit
```

Nossas [mensagens de commit](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
são sempre no presente, em inglês. A mensagem deve conter na
primeira linha um resumo do commit, em no máximo 50 caracteres, separada por uma linha em
branco e os detalhes da mudança. Todas as linhas devem possuir no máximo 72 caracteres.

```
Notify users about their status.

* More details about this commit.
* Much more details about this commit.

http://github.com/sumoners/my-project/issues/123
```

Sempre que algo novo surgir na `master`, você precisar fazer um `git rebase` na sua branch.
Dessa forma a arvore de commits do repositório permanecerá sempre linear.

```
git fetch origin
git rebase origin/master
```

Ao finalizar suas alterações, caso tenha executado diversos commits, organize-os em commits
lógicos e completos com um [`git rebase` interativo](https://help.github.com/articles/about-git-rebase/).
Você não deve ter commits como "Fix rubocop issues".

```
git rebase -i origin/master
```

Caso você já tenha enviado suas alterações para o servidor anteriormente, você precisará forçar o
envio após executar qualquer rebase. Isso acontece pois a árvore de commits foi alterada.

```
git push -f
```

Com tudo pronto, faça um [Pull Request](https://help.github.com/articles/using-pull-requests/) novamente para a branch `master`. Lembre-se de utilizar um título descritivo, bem como uma descrição do que foi realizado, para facilitar o Code Review. Na mensagem do Pull Request inclua um link para o issue (caso exista).

Copie o link do pull request e cole no Slack, mencionando os pontenciais revisores para o seu código.

### Code Review e Merge

Se você foi chamado para revisar uma feature, tente fazer o quanto antes. 
Você não precisa parar tudo o que está fazendo para fazer o Code Review, mas no primeiro
intervalo que tiver, faça. Lembre-se, logo mais será você que precisará ter seu código
revisado.

Não procure revisar a sintaxe do código, para isso temos o CI. O objetivo no code review
é analisar a abordagem ao problema, entender como a solução aplicada se relaciona ao
restante da aplicação, procurar falhas de segurança que podem ser exploradas,
verificar pontos que não foram cobertos por testes e principalmente absorver o conhecimento
desse novo trecho que código, para que você também possa modificá-lo no futuro.

Caso encontre problemas, comente no código. Caso esteja tudo OK, comente no Pull Request, sinalizando
que está tudo certo e o Merge pode ser realizado.

Após receber a confirmação de que está tudo OK, realize o merge e apague sua branch.

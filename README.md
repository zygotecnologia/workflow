# Workflow da SumOne

Esse documento visa padronizar todos os elementos que compõem nosso fluxo 
de trabalho.

Isso permite que novos desenvolvedores entrem em nossa equipe e consigam 
rapidamente começar a trabalhar em nossos projetos bem como disciplina 
nosso _modus operandi_, deixando nosso tempo disponível para fazermos
aquilo em que somos ótimos: criar produtos que mudam o mundo.

## Conteúdo

1. [Gestão de Projetos](#project-management) 
  * [Práticas](#project-practices)
  * [Issues e Boards](#project-issues)
2. [Gestão de Código](#code-management) 
  * [Git](#code-git)
    * [Criando uma nova feature](#git-workflow-feature)
    * [Code Review e Merge](#git-workflow-merge)
3. [Linguagens e Frameworks](#languages) 
  * [Ruby](#ruby)
  * [Rails](#rails)
4. [Práticas e Metodologias](#methodologies) 
  * [Continuous Integration](#ci)
  * [Test-Driven Development](#tdd)
  * [Testes e Coverage](#tests)
    
## Contribuindo com nosso workflow
O workflow só será revisto durante duas datas pré-determinadas:

  * Todo dia 15 de Junho
  * Todo dia 15 de Janeiro

Na revisão, serão abordados os **issues** abertos neste repositório,
após passarem por um filtro prévio pela equipe de gestão,
que serão levados a discussão e aprovados ou reprovados pelos presentes.

Dessa forma, quer contribuir com o _workflow_? Crie um **issue** e chame
os colegas para a discussão!

# <a name="project-management">Gestão de Projetos

Fazemos a gestão dos nossos projetos com **SCRUM**, mas não utilizamos
todas as práticas, fazemos nosso próprio mix.

## <a name="project-practices">Práticas

As práticas que utilizamos na SumOne são:

* **Papéis**: Product Owner

* **Product Backlog**: Um documento que mostra as funcionalidades desejadas do
  produto, contendo **Objetivo**, **Descrição e Requisitos**, 
  **Definição de "feito"** e **Notas**.

* **Features**: O _Product Backlog_ é composto de diversas _features_ ou 
  funcionalidades, que são levadas para o _sprint planning_.

* **Sprint Planning**: Realizado antes de começar cada _sprint_, na sala de 
  reuniões, durando no máximo 6 horas.

* **Sprint Task**: Uma tarefa que foi especificada durante o _sprint planning_.

* **Sprint**: 10 dias úteis para realizar todas as tarefas definidas no 
  _sprint planning_.

* **Pontuação**: Cada ponto corresponde a um dia de trabalho/homem. A pontuação
  mínima é 0.5 (meio dia). A pontuação de cada _sprint task_ é definida no 
  _sprint planning_, a partir do método 
  [Planning Poker](http://en.wikipedia.org/wiki/Planning_poker).

* **SCRUM Place**: Um lugar no escritório com um quadro para discussão
  e a _SCRUM Board_ com um _Burndown Chart_.

* **SCRUM Board**: Um quadro contendo as _pipelines_ do sprint: _to do_, 
  _doing_, _qa_, _done_.

* **Burndown Chart**: O jeito mais fácil de ver se o sprint está indo tão 
  rápido quanto o combinado.

* **Collective Ownership**: Todos são ao mesmo tempo responsáveis e donos do
  projeto e sua arquitetura.

* **Code Review**: Colocando em prática o _Collective Ownership_. Todo código
  é revisado pela equipe antes de ser colocado em produção.

* **Deploy Contínuo**: Realizamos diversos deploys por dia.

Todos os tópicos podem ser consultados na _Wikipedia_ :)

## <a name="project-issues">Issues e Boards

Para manter o time todo atualizado do que está acontecendo no projeto, usamos os [issues](https://guides.github.com/features/issues/) do
GitHub, para _features_, _sprint tasks_ e _bugs_.

# <a name="code-management">Gestão de Código

## <a name="code-git">Git

Utilizamos [Git](http://git-scm.com/) para fazer a gestão do nosso código.

### <a name="git-workflow-feature">Criando uma nova feature

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

### <a name="git-workflow-merge">Code Review e Merge

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


# <a name="languages">Linguagens e Frameworks

Para cada linguagem e framework temos um conjunto de regras e boas práticas.
Siga as boas práticas para não ser barrado pelo CI ou no Code Review :)

## <a name="ruby">Ruby

As boas práticas e regras que usamos quando usamos Ruby são as seguintes:

* Para o estilo de código, usamos as regras do 
  [Ruby Style Guide](https://github.com/bbatsov/ruby-style-guide).

* Sempre que mexemos no **Gemfile**, comentamos a _gem_ que colocamos dizendo
  o que ela faz e o motivo de adoção da mesma (se aplicável).
  Ex: "Devise - Faz a autenticação de usuários", 
  "Ruby Geocoder - Geoencoda latitude e longitude - Coloquei para a ferramenta
  de polígono".

## <a name="rails">Rails

* Para toda e qualquer frase que usamos nas views, usamos 
  [I18n](http://guides.rubyonrails.org/i18n.html)

* Atualizamos sempre. Saiu uma nova versão do Rails? No próximo sprint já vamos
  atualizá-lo!

* Obedecemos ao padrão 
  [REST](http://www.infoq.com/articles/webber-rest-workflow), sempre, 
  incondicionalmente.

* Não somos muito apegados a _dark magic_ nem a práticas que fujam do padrão
  do Rails, mas usamos 
  [Service Classes](http://railscasts.com/episodes/398-service-objects).

* Não hesitamos na hora de comentar código. Toda classe deve ter comentários
  indicando para que ela veio ao mundo. Usamos as
  [convenções do Rails](http://guides.rubyonrails.org/api_documentation_guidelines.html)
  para organizar nossa documentação.

* Uma sprint task nunca pode ser considerada feita se não passar nos seguintes 
  testes:
  * [RuboCop (Ruby Style Guide Compliance)](https://github.com/bbatsov/rubocop)
  * [SCSS Lint](https://github.com/brigade/scss-lint)
  * [Brakeman (Segurança)](http://brakemanscanner.org/)
  * [JSHint](http://eslint.org/)
 
 * Todos os testes acima são executados automaticamente pela plataforma de integração contínua CircleCI.

### Stack

O stack padrão que usamos no Rails, para resolver cada tipo de problema está 
listado abaixo:

| Problema | Gem |
| :------- | :-- |
| Organizar as gems de assets | [Rails Assets](https://rails-assets.org/) |
| Templating | [ERB](http://ruby-doc.org/stdlib-2.2.0/libdoc/erb/rdoc/ERB.html) (está aqui só para ninguém nunca usar HAML) |
| Melhoria de CSS | [SASS](http://sass-lang.com/) |
| Processamento de Queues | [Sidekiq](https://github.com/mperham/sidekiq) |
| Autenticação | [Devise](https://github.com/plataformatec/devise) |
| Autorização | [CanCanCan](https://github.com/CanCanCommunity/cancancan) |
| Upload | [Carrier Wave](https://github.com/carrierwaveuploader/carrierwave) |
| Jobs Recorrentes/Cron | [Whenever](https://github.com/javan/whenever) |
| Paginação | [Kaminari](https://github.com/amatsuda/kaminari) |
| Caching | [Redis](https://github.com/redis-store/redis-rails), [Dalli](https://github.com/petergoldstein/dalli) |
| Multi-Tenancy | [Apartment](https://github.com/influitive/apartment) |
| Respostas de API | [Serializers](https://github.com/rails-api/active_model_serializers), [JBuilder](https://github.com/rails/jbuilder) |
| Testes | [RSpec](https://github.com/rspec/rspec), [Rspec API Documentation](https://github.com/zipmark/rspec_api_documentation) |
| Factories | [Factory Girl](https://github.com/thoughtbot/factory_girl) |
| Deploy | [Capistrano](http://capistranorb.com/) |
| Criptografia | [DotGPG](https://github.com/ConradIrwin/dotgpg) |

# <a name="methodologies">Práticas e Metodologias

## <a name="ci">Continuous Integration

Todos os dias damos _push_ no nosso código para o _GitHub_. Nosso servidor
de CI possui um _hook_ que roda automaticamente os testes da aplicação para
verificar se você quebrou algo.

As regras são:

* Quebrar algo numa _feature_ branch não tem problema, se você ainda estiver
  trabalhando nela.

* Se você por acaso quebrar a branch _master_, você deve parar tudo o que 
  estiver fazendo para consertá-la. (Quem quebra arruma).

## <a name="tdd">Test-Driven Development

Usamos a metodologia de Test-Driven Development quando é conveniente, mas não
somos completamente ortodoxos: usamos quando faz sentido.

Sempre é bom, no entanto, ter uma visão geral do problema e da estrutura para
evitar o retrabalho. Para isso, utilizamos o _sprint planning_ para debater
o problema e tentar definir a melhor abordagem para ele.

## <a name="tests">Testes e Coverage

Criamos testes de integração para APIs utilizando _RSpec Api Documentation_ e para
aplicações web com _Capybara_. Para testes unitários, procuramos testar _models_ e qualquer
outra classe de serviço que a aplicação venha a ter (Service Objects, Workers, etc.)

Com excessão de testes mais complexos, procuramos fazer o menor uso possível de mocks,
mesmo que isso leve diversos testes a quebrarem com apenas uma mudança. O objetivo é 
procurar diminuir a dependência dos testes de uma implementação específica e simplificar
a leitura dos testes.

Utilizamos o modelo de quatro etapas para a escrita dos testes:

- Configuração: Criamos os objetivos de que dependem os testes.
- Teste: Executamos o teste.
- Verificação: Verificamos se os resultados dos testes foram os esperados.
- Limpeza: Limpeza dos dados criados para o teste. (normalmente executada automaticamente, através do Database Cleaner).

Miramos em 95% de coverage no código.

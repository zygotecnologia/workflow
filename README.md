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
  * [Versionamento](#code-versioning)
3. [Linguagens e Frameworks](#languages) 

  * [Ruby](#ruby)
  * [Rails](#rails)
4. [Práticas e Metodologias](#methodologies) 

  * [Continuous Integration](#ci)
  * [Test-Driven Development](#tdd)
  * [Testes e Coverage](#tests)
5. [Guias Práticos](#practical-guides) 

  * [Git Workflow](#git-workflow)

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

* **Papéis**: Product Owner, Scrum Master

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

* **SCRUM Place**: Um lugar no escritório com um sofá, um quadro para discussão
  e a _SCRUM Board_ com um _Burndown Chart_.

* **SCRUM Board**: Um quadro contendo as _pipelines_ do sprint: _to do_, 
  _doing_, _qa_, _done_.

* **Burndown Chart**: O jeito mais fácil de ver se o sprint está indo tão 
  rápido quanto o combinado.

Todos os tópicos podem ser consultados na _Wikipedia_ :)

## <a name="project-issues">Issues e Boards

Para manter o time todo atualizado do que está acontecendo no projeto e o que
está por vir, usamos os [issues](https://guides.github.com/features/issues/) do
GitHub, para _features_, _sprint tasks_, _bugs_ e _ideas_.

Usamos uma extensão do Chrome chamada [ZenHub](https://www.zenhub.io/) para
organizar as _pipelines_ da mesma forma que na nossa _scrum board_.

# <a name="code-management">Gestão de Código

## <a name="code-git">Git
Utilizamos [Git](http://git-scm.com/) para fazer a gestão do nosso código.

Com relação ao Git, usamos as seguintes práticas:

  * Usamos a gem _git up_ para dar um update no nosso repositório local.

  * Fazemos nossas mensagens de commit sempre no pretérito, usando a primeira
  pessoa do singular: "Fiz o sistema de gestão de notícias", 
  "Arrumei o bug #22", "Tentei fazer ..."

  * As mensagens de commit são sempre em português.

  * Para organização dos _branches_, usamos o modelo 
  [Git Flow](http://nvie.com/posts/a-successful-git-branching-model/), com a
  excessão de que ao invés de fazermos um _merge_ da _feature_ que estamos
  trabalhando com a branch _develop_, nós criamos um _pull request_ no GitHub
  para esse fim.

  * Antes de criar um Pull Request, faça um _rebase_ da branch _develop_ com a
  sua _feature branch_ para garantir que seu código está _up to date_ e evitar
  conflitos no pull request.

Para mais informações, veja o guia prático [Git Workflow](#git-workflow)

## <a name="code-versioning">Versionamento

Usamos o sistema [Semantic Versioning 2.0.0](http://semver.org/) para controle
de versão, sendo definido o seguinte:

  * **Hotfixes** mudam o patch: 0.0.X
  * **Releases** mudam o minor: 0.X.0
  * **Marketing** muda a major: X.0.0

Esse esquema fecha bem com os conceitos do _git flow_ que comentamos antes.

# <a name="languages-and-frameworks">Linguagens e Frameworks

Para cada linguagem e framework temos um conjunto de regras e boas práticas.
Siga as boas práticas para não ser barrado pelo QA :)

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
  * RuboCop (Ruby Style Guide Compliance)
  * SCSS Lint
  * Brakeman (Segurança)
  * Flay (Assegura um código DRY)
  * JSHint
  * Rails Best Practices
  * Reek (Code Smell, apenas para models)

### Stack

O stack padrão que usamos no Rails, para resolver cada tipo de problema está 
listado abaixo:

| **Problema** | **Gem** |
| Organizar as gems de assets | [Rails Assets](https://rails-assets.org/) |
| Templating | [ERB](http://ruby-doc.org/stdlib-2.2.0/libdoc/erb/rdoc/ERB.html) (está aqui só para ninguém nunca usar HAML) |
| Melhoria de CSS | [SASS](http://sass-lang.com/) |
| Processamento de Queues | [Sidekiq](https://github.com/mperham/sidekiq) |
| Autenticação | [Devise](https://github.com/plataformatec/devise) |
| Autorização | [CanCanCan](https://github.com/CanCanCommunity/cancancan) |
| Formulários Easy Breezy | [Simple Form](https://github.com/plataformatec/simple_form) |
| Upload | [Carrier Wave](https://github.com/carrierwaveuploader/carrierwave) |
| Jobs Recorrentes/Cron | [Whenever](https://github.com/javan/whenever) |
| Paginação | [Kaminari](https://github.com/amatsuda/kaminari) |
| Caching | [Redis](https://github.com/redis-store/redis-rails) |
| Multi-Tenancy | [Apartment](https://github.com/influitive/apartment) |
| Respostas de API | [Serializers](https://github.com/rails-api/active_model_serializers) |
| Testes | [RSpec](https://github.com/rspec/rspec) |
| Factories | [Factory Girl](https://github.com/thoughtbot/factory_girl) |

# <a name="methodologies">Práticas e Metodologias

## <a name="ci">Continuous Integration

Todos os dias damos _push_ no nosso código para o _GitHub_. Nosso servidor
de CI possui um _hook_ que roda automaticamente os testes da aplicação para
verificar se você quebrou algo.

As regras são:

* Quebrar algo numa _feature_ branch não tem problema, se você ainda estiver
  trabalhando nela.

* Se você por acaso quebrar a branch _develop_, você deve parar tudo o que 
  estiver fazendo para consertá-la. (Quem quebra arruma).

## <a name="tdd">Test-Driven Development

Usamos a metodologia de Test-Driven Development quando é conveniente, mas não
somos completamente ortodoxos: usamos quando faz sentido.

Sempre é bom, no entanto, ter uma visão geral do problema e da estrutura para
evitar o retrabalho. Para isso, discutimos exaustivamente no _sprint planning_
e antes de o projeto começar.

## <a name="tests">Testes e Coverage

Como regra geral, testamos apenas **Testes de Integração** e de **Models**.

Miramos em 95% de coverage no código.

# <a name="practical-guide">Guias Práticos

## <a name="git-workflow">Git Workflow

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

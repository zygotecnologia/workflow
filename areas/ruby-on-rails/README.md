## Ruby

As boas práticas e regras que usamos quando usamos Ruby são as seguintes:

* Para o estilo de código, usamos as regras do 
  [Ruby Style Guide](https://github.com/bbatsov/ruby-style-guide).

* Sempre que mexemos no **Gemfile**, comentamos a _gem_ que colocamos dizendo
  o que ela faz e o motivo de adoção da mesma (se aplicável).
  Ex: "Devise - Faz a autenticação de usuários", 
  "Ruby Geocoder - Geoencoda latitude e longitude - Coloquei para a ferramenta
  de polígono".

## Rails

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


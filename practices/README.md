# Melhores Práticas

## Arquitetura

Buscamos a simplicidade. Por mais sênior que você seja, procure sempre a
arquitetura mais simples de ser entendida por qualquer outro desenvolvedor, seja
ele júnior ou estagiário.

O código que desenvolvemos não possui um fim em si mesmo, portanto não
complique. Não apenas utilize a última tecnologia da moda, pense em como essa
tecnologia realmente vai agregar valor para nosso cliente.

## Continuous Integration

Todos os dias damos _push_ no nosso código para o _GitHub_. Nosso servidor
de CI possui um _hook_ que roda automaticamente os testes da aplicação para
verificar se você quebrou algo.

As regras são:

* Quebrar algo numa _feature_ branch não tem problema, se você ainda estiver
  trabalhando nela.

* Se você por acaso quebrar a branch _master_, você deve parar tudo o que 
  estiver fazendo para consertá-la. (Quem quebra arruma).

## Test-Driven Development

Usamos a metodologia de Test-Driven Development quando é conveniente, mas não
somos completamente ortodoxos: usamos quando faz sentido.

Sempre é bom, no entanto, ter uma visão geral do problema e da estrutura para
evitar o retrabalho. Para isso, utilizamos o _sprint planning_ para debater
o problema e tentar definir a melhor abordagem para ele.

## Testes e Coverage

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


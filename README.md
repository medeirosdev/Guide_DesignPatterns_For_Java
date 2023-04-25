# Guide Design Patterns for Java

## Categorias

### Criação:
- Factory Method
- Builder
- Abstract Factory

### Estrutura
- Proxy

### Comportamento
- Observer


## Factory Method

A ideia é facilitar a criação de Objetos:
Imagine que você quer fazer um bolo, mas não sabe exatamente que tipo de bolo fazer. Você sabe que vai precisar de ingredientes como farinha, açúcar, ovos e leite, mas não sabe em que quantidades ou qual receita seguir.

O Factory Method em Java é como se fosse uma "fábrica de bolos". Em vez de você ter que decidir exatamente qual tipo de bolo fazer e quantidades de ingredientes usar, você pode simplesmente pedir à fábrica para fazer um bolo para você. A fábrica sabe como fazer vários tipos de bolo e vai escolher a receita e quantidades de ingredientes corretas para você.

Da mesma forma, em Java, o Factory Method é um padrão de projeto que permite criar objetos sem precisar saber exatamente qual classe de objeto criar. Em vez disso, você simplesmente chama um método de criação que cuida de criar o objeto para você. Isso é útil quando você tem várias classes diferentes que podem ser usadas em um programa, mas não sabe qual delas usar antecipadamente.

"O Padrão Factory Method Define uma interface para criar um Objeto, mas permite que as classes que implementam a interface decidam qual classe instanciar. 
o Factory Method permite uma classe delegar a instanciação a subclasse".

Um exemplo de uso do padrão Factory Method é em um sistema de pagamento online que permite diferentes métodos de pagamento, como cartão de crédito, boleto bancário, transferência bancária, entre outros.

Para implementar o padrão Factory Method, primeiro criamos uma interface chamada PagamentoFactory, que define o método criarPagamento(). Em seguida, criamos classes concretas que implementam essa interface para cada método de pagamento que desejamos suportar, como CartaoCreditoPagamentoFactory, BoletoBancarioPagamentoFactory e TransferenciaBancariaPagamentoFactory.

Cada uma dessas classes concretas é responsável por criar um objeto Pagamento, que pode ter diferentes implementações dependendo do método de pagamento escolhido. Por exemplo, a classe CartaoCreditoPagamentoFactory pode criar um objeto Pagamento que representa um pagamento com cartão de crédito, enquanto a classe BoletoBancarioPagamentoFactory pode criar um objeto Pagamento que representa um pagamento com boleto bancário.

Dessa forma, quando um usuário escolhe um método de pagamento, o sistema de pagamento utiliza a classe correspondente àquele método de pagamento para criar o objeto Pagamento apropriado. Isso permite que a lógica de criação do objeto seja delegada às subclasses, mantendo assim o código mais flexível e extensível.

## Builder


Quais são os participantes que constituem o padrão Builder?

O padrão em questão é composto por quatro componentes básicos que são a Interface (ou classe abstrata) Builder, o concrete builder (construtor concreto), o Director (Diretor) e o product (produto). Vejamos a seguir o que cada um deles é responsável em fazer:

- Classe Builder – esta classe especifica uma interface ou uma classe abstrata para a criação das partes (ou podemos considerar como sendo os passos que serão realizados) de um objeto a fim de criar corretamente o produto (Product). Cada um desses passos são, geralmente, abstrações das funcionalidades realizadas nas subclasses concretas.
- Concrete Builder – esta classe é responsável pela construção e pela montagem das partes do produto por meio da implementação da classe builder. Ela define e mantém o controle da representação que a classe cria, além de fornecer uma interface para recuperação do produto.
- Director – esta é a classe que controla o algoritmo responsável por gerar o objeto do produto final. Um objeto Director é instanciado e seus métodos construtores são chamados. O método inclui um parâmetro para capturar objetos específicos do tipo Concrete Builder que serão então utilizados para gerar o produto (product). Dessa forma, o director, chama os métodos do concrete builder na ordem correta para gerar o objeto produto.
- Product – o product representa o objeto complexo que está sendo construído. O concrete builder então constrói a representação interna do produto e define o processo pelo qual essa classe será montada. Na classe product são incluídas outras classes que definem as partes que a constituem, dentre elas, as interfaces para a montagem das partes no resultado final.

---
Como tudo funciona no mundo Builder?

Primeiramente, o client (cliente) poderá ser de certa forma, ou um objeto a parte ou mesmo o cliente real que chamará o método main() da aplicação, iniciando assim as classes Builder e Director. A classe Builder representa o nosso objeto complexo que precisa ser construído em termos de objetos e tipos mais simples. O construtor da classe Director recebe um objeto Builder como sendo um parâmetro através do cliente e é responsável por chamar os métodos apropriados da classe Builder. A fim de fornecer a classe cliente com uma interface para todos os construtores concretos, a classe Builder deve ser uma classe abstrata. Desta forma, podemos adicionar novos tipos de objetos apenas definindo a estrutura e reutilizando a lógica para o processo real da construção. O cliente é o único que precisa saber sobre os novos tipos, já a classe Director, precisa saber apenas quais os métodos que precisará chamar.

https://www.devmedia.com.br/padrao-de-projeto-factory-method-em-java/26348

## Abstract Factory Pattern

O padrão Abstract Factory é um padrão de projeto de software que ajuda a criar famílias de objetos relacionados sem especificar suas classes concretas. Isso permite que você crie objetos relacionados sem ter que se preocupar com os detalhes de como eles são criados ou como funcionam internamente.

O padrão Abstract Factory consiste em duas partes principais: a fábrica abstrata e as fábricas concretas. A fábrica abstrata define uma interface para criar objetos relacionados, enquanto as fábricas concretas implementam essa interface para criar objetos específicos.

Por exemplo, suponha que você esteja criando um jogo e precise criar personagens para o jogo. Em vez de criar cada personagem manualmente, você pode usar o padrão Abstract Factory para criar uma fábrica abstrata de personagens e, em seguida, criar fábricas concretas para cada tipo de personagem que deseja criar. Cada fábrica concreta irá criar personagens específicos com base na fábrica abstrata.

Essas fábricas concretas podem ser organizadas em uma hierarquia para criar famílias de objetos relacionados. Por exemplo, você pode ter uma fábrica abstrata de personagens que cria fábricas concretas para personagens de guerreiros, magos e ladrões. Cada fábrica concreta de personagens irá criar personagens específicos de acordo com a classe de personagem.

O padrão Abstract Factory é especialmente útil quando você precisa criar objetos que dependem de um contexto específico, como criar objetos em diferentes plataformas ou para diferentes bancos de dados. Ele também pode ser usado para criar objetos relacionados de forma consistente e modular, sem ter que conhecer os detalhes de como eles são criados ou como funcionam internamente.

#### UML class diagram example for the Abstract Factory Design Pattern. 
- AbstractFactory: Declares an interface for operations that create abstract product objects. 
- ConcreteFactory: Implements the operations declared in the AbstractFactory to create concrete product objects.
- Product: Defines a product object to be created by the corresponding concrete factory and implements the AbstractProduct interface.
- Client: Uses only interfaces declared by AbstractFactory and AbstractProduct classes.

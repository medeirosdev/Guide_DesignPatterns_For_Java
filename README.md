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

## Proxy Pattern

O padrão Proxy é um padrão de projeto de software que permite criar um objeto que atua como um substituto ou proxy para outro objeto. O Proxy age como um intermediário entre o cliente e o objeto real e controla o acesso ao objeto real, podendo adicionar funcionalidades extras como cache, controle de acesso, registro de uso, entre outros.

Existem diferentes tipos de proxies, como o Proxy Remoto, que permite que objetos em diferentes máquinas possam se comunicar através de uma rede, e o Proxy Virtual, que cria objetos somente quando são necessários e mantém uma referência a eles para reutilização posterior, a fim de melhorar o desempenho do sistema.

Um exemplo comum do padrão Proxy é o proxy de proteção, que é usado para controlar o acesso a um objeto ou recurso. Imagine que você tenha uma classe que representa um banco de dados, mas você não quer que todos os usuários possam acessar diretamente a classe de banco de dados. Em vez disso, você pode criar uma classe Proxy que verifica se o usuário tem permissão para acessar o banco de dados e, em seguida, encaminha a solicitação para a classe de banco de dados real. Desta forma, o Proxy protege o banco de dados de acesso não autorizado e melhora a segurança do sistema.

Em resumo, o padrão Proxy é utilizado para controlar o acesso a um objeto ou recurso e adiciona funcionalidades extras como cache, controle de acesso, registro de uso, entre outros. Ele é útil quando se deseja adicionar segurança e controle a um objeto ou recurso e quando é necessário limitar o acesso direto ao objeto ou recurso por motivos de segurança ou desempenho.


https://www.devmedia.com.br/conheca-o-pattern-proxy-gof-gang-of-four/4066
https://www.baeldung.com/java-proxy-pattern

## Context and Dependency Injection

Na programação, usamos algo parecido chamado de "injeção de dependência" (ou dependency injection, em inglês). Funciona assim: Imagine que nosso programa é um quebra-cabeça, com várias partes que precisam ser montadas para fazer algo funcionar. Por exemplo, um programa de música precisa de um tocador de música, uma lista de reprodução, uma conexão com a internet e outras coisas.

Com a injeção de dependência, em vez de termos que construir todas as peças do quebra-cabeça sozinhos, podemos receber essas peças de outras partes do programa que já as construíram. Isso nos ajuda a economizar tempo e esforço e torna nosso código mais organizado e fácil de entender.

Por exemplo, imagine que precisamos de um tocador de música para nosso programa. Em vez de construir um novo tocador de música em nosso programa, podemos receber um tocador de música que já foi construído em outra parte do programa e que está disponível para ser usado quando precisarmos.

Isso torna nosso código mais modular e fácil de atualizar. Se precisarmos mudar o tocador de música, por exemplo, podemos simplesmente substituí-lo por outro, sem precisar mudar todo o programa.

Em resumo, a injeção de dependência é uma forma de receber peças de código que já foram construídas por outras partes do programa, em vez de termos que construí-las novamente. Isso nos ajuda a economizar tempo e esforço, torna nosso código mais organizado e fácil de entender, e nos permite atualizar e modificar o código com mais facilidade.

A injeção de dependência é um padrão de design utilizado em programação orientada a objetos que tem como objetivo desacoplar as classes do código, facilitando a manutenção, o teste e a reutilização do código.

Imagine que você está criando um programa que precisa de vários objetos, como por exemplo uma classe para lidar com o banco de dados, uma para fazer requisições HTTP, e uma para fazer cálculos matemáticos. Quando você cria essas classes, elas geralmente precisam umas das outras para funcionar corretamente. Por exemplo, a classe que lida com o banco de dados precisa da classe que faz requisições HTTP para obter informações do servidor.

A injeção de dependência ajuda a resolver esse problema, permitindo que você injete (ou passe) as dependências necessárias para cada classe em vez de criá-las dentro da classe. Isso significa que você não precisa mais instanciar cada dependência dentro da classe, tornando o código mais flexível e mais fácil de testar.

Por exemplo, em vez de criar uma nova instância da classe de banco de dados dentro de outra classe, você pode criar uma instância separada da classe de banco de dados e, em seguida, injetar essa instância na classe que precisa dela.

Existem três tipos de injeção de dependência: injeção de construtor, injeção de método e injeção de propriedade. Na injeção de construtor, as dependências são passadas através do construtor da classe. Na injeção de método, as dependências são passadas através de um método da classe. Na injeção de propriedade, as dependências são passadas através de uma propriedade da classe.

A injeção de dependência é especialmente útil em projetos grandes e complexos, onde as dependências podem ser difíceis de gerenciar. Ao desacoplar as classes do código, a injeção de dependência torna o código mais modular, o que facilita a manutenção, o teste e a reutilização do código.

Em resumo, a injeção de dependência é um padrão de design que permite injetar as dependências necessárias para cada classe em vez de criá-las dentro da classe. Isso torna o código mais flexível e mais fácil de testar e manter, o que é especialmente útil em projetos grandes e complexos.

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

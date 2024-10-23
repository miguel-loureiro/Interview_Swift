# **`Interview Prep`** 

`Preparation for interview to Junior Developer role`

## **`OOP - Object Oriented Programming`**

`É um paradigma de programação que organiza o código em objetos, que são instâncias de classes.`   
`É baseado em quatro pilares principais:`

* `encapsulamento`  
* `abstração`  
* `herança`  
* `polimorfismo`

# **`Encapsulamento:`**

`Encapsulamento é o conceito de agrupar dados e comportamentos relacionados numa única entidade chamada de class.`   
`Uma class define os atributos (dados) e métodos (comportamentos) que os objetos podem ter. O encapsulamento permite ocultar os detalhes internos da implementação e expor apenas uma interface para interagir com o objeto.`   
`Utilizamos este conceito quando queremos definir como nossas classes, propriedades e métodos são acedidos por outras classes ou objetos dentro da aplicação.`   
`Este conceito traz mais segurança e controlo durante o desenvolvimento.`   
`Existem três níveis de encapsulamento em Swift:`

* **`public`** `: permite acesso a qualquer outro elemento`  
* **`internal`** `: permite acesso apenas dentro da própria classe e nas suas subclasses`  
* **`private`** `: permite acesso apenas dentro da classe na qual foi declarada`


  
`class Pessoa {`

    `var nome: String = "Miguel"`

    `private var idade: Int = 48 //propriedade privada`

    `func mudarIdade(novaIdade: Int) {`  
        `idade = novaIdade`  
    `}`  
      
    `func imprimeIdade() {`  
        `print(idade)`  
    `}`  
`}`

`var humano : Pessoa = Pessoa()`  
`humano.idade = 35 //Resultado: erro`  
`humano.mudarIdade(novaIdade: 35) //alteração da idade, usando o método da classe`  
`humano.imprimeIdade() //Resultado: 35`

##### ***`Resumo:`***

`No exemplo acima, encapsulamos a variável idade usando o especificador de acesso private. Por isso apenas podemos alterar a idade usando o método mudarIdade() que é um método da classe e assim já tem acesso à variável idade`

# **`Abstracção:`**

`É um conceito OOP pelo qual expomos dados e métodos relevantes de um objeto ocultando sua implementação interna. Quando vamos a uma loja comprar um produto, simplesmente compramos o produto que desejamos. O vendedor não nos informa como o produto é comprado (por ex. iniciar uma venda no software, ler o código do produto e adicionar ao processo de venda, emitir o total na moeda correspondente, perguntar sobre meio de pagamento, ...). Pode-se pensar nisso como um exemplo de abstração.`

| `class Calculus {    let a: Int!    let b: Int!    private var resultado: Int?    init(a: Int,b: Int) {        self.a = a        self.b = b    }    func soma() {        resultado = a + b    }    func mostraResultado() {        print("Resultado => \(resultado)")    }}let calculo = Calculus(a: 2, b: 3)calculo.soma()calculo.mostraResultado()` |
| :---- |

##### ***`Resumo :`***

`No nosso exemplo de abstração, estamos a expor os métodos mostraResultado() e soma() ao usuário para realizar os cálculos, mas "escondemos" os cálculos internos do processamento.`

# **`Herança`**

`É um processo pelo qual a classe herda as propriedades da sua parent class. Tecnicamente, herança é um processo pelo qual uma classe filha herda as propriedades de sua classe pai.`

###### `Class parent`

| `class Animal {    var nome: String    var idade: Int    // Construtor (inicializador) para a classe Animal    init(nome: String, idade: Int) {        self.nome = nome        self.idade = idade    }    // Método comum a todos os animais    func dormir() {        print("\(nome) está a dormir.")    }    // Método que será sobrescrito pelas subclasses    func fazerSom() {        print("\(nome) faz um som.")    }}` |
| :---- |

###### `Animal é a classe base que define propriedades (nome, idade) e métodos (dormir(), fazerSom()) comuns a todos os animais.`

###### `Sub classes (Herança)`

| `class Cao: Animal {    // Subclasse 'Cao' que herda de 'Animal'    // Sobrescreve o método fazerSom para um cão    override func fazerSom() {        print("\(nome) faz: Au Au!")    }    // Método específico do cao    func abanarRabo() {        print("\(nome) está a abanar o rabo.")    }}class Gato: Animal {    // Subclasse 'Gato' que herda de 'Animal'    // Sobrescreve o método fazerSom para um gato    override func fazerSom() {        print("\(nome) faz: Miau!")    }    // Método específico do gato    func ronronar() {        print("\(nome) está a ronronar.")    }}` |
| :---- |

##### ***`Resumo:`***

**`Classe Cao`** `herda todos os comportamentos da classe Animal (como dormir()) e sobrescreve o método fazerSom() para dar um comportamento específico aos cães.`  
**`Classe Gato`** `faz o mesmo, mas com um comportamento específico para gatos.`

***`Aplicação`***`:`

| `let cao = Cao(nome: "Rex", idade: 3)let gato = Gato(nome: "Whiskers", idade: 2)// Usando métodos herdados da classe Animalcao.dormir()  // Saída: Rex está a dormir.gato.dormir()      // Saída: Whiskers está a dormir.// Usando métodos sobrescritoscao.fazerSom()  // Saída: Rex faz: Au Au!gato.fazerSom()      // Saída: Whiskers faz: Miau!// Usando métodos específicos das subclassescao.abanarRabo()  // Saída: Rex está a abanar o rabo.gato.ronronar()        // Saída: Whiskers está a ronronar.` |
| :---- |

**`Classe Base (Animal)`**`:`

* `A classe Animal define propriedades (nome, idade) e métodos (dormir(), fazerSom()) que são comuns a todos os tipos de animais.`  
* `A classe base também define comportamentos genéricos, como dormir().`

**`Subclasses (Cao e Gato)`**`:`

* `As subclasses Cao e Gato herdam todos os comportamentos e propriedades da classe Animal.`  
* `Elas sobrescrevem o método fazerSom() para dar uma implementação específica (como "Au Au!" para cães e "Miau!" para gatos).`  
* `Elas também podem adicionar métodos específicos (como abanarRabo() para Cao e ronronar() para Gato), que só fazem sentido para aquela subclasse.`

# **`Polimorfismo`**

`Permite que objetos de diferentes classes sejam tratados como objetos de uma superclasse comum. Com isto é possível escrever código mais flexível e reutilizável, permitindo trabalhar com objetos de diferentes tipos por meio de uma interface comum.`

### **`Nota: Existem 2 tipos de polimorfismo em Swift: runtime e compile-time`**

#### `Polimorfismo em runtime`

`Este tipo de polimorfismo consegue-se através de herança e override de funções`

###### `Class parent`

| `class Animal {    // Método comum a todos os animais, mas que será sobrescrito nas subclasses    func fazerSom() {        print("O animal faz um som.")    }}` |
| :---- |

###### `Sub classes (classes que vão fazer override ao método fazerSom())`

| `class Gato: Animal {    // Sobrescreve o método fazerSom() para Gatos    override func fazerSom() {        print("O gato faz: Miau!")    }}class Vaca: Animal {    // Sobrescreve o método fazerSom() para Vacas    override func fazerSom() {        print("A vaca faz: Muu!")    }}` |
| :---- |

### ***`Resumo:`***

`Aqui, temos 2 classes derivadas (Gato e Vaca), cada uma delas sobrescrevendo o método fazerSom() com um comportamento específico.`

### ***`Aplicação:`***

| `func fazerAnimalEmitirSom(animal: Animal) {    animal.fazerSom()}` |
| :---- |

| `let gato = Gato()let vaca = Vaca()// Aqui o método fazerSom() será chamado de acordo com o tipo real do objetofazerAnimalEmitirSom(animal: gato)      // Saída: O gato faz: Miau!fazerAnimalEmitirSom(animal: vaca)    // Saída: A vaca faz: Muu!` |
| :---- |

**`Classe Base (Animal)`**`: Define o método fazerSom(), que pode ser sobrescrito por subclasses.`

**`Subclasses`**`: Gato e Vaca são subclasses de Animal e sobrescrevem o comportamento do método fazerSom() para fornecer sons específicos de cada animal.`

**`Polimorfismo`**`: Quando chamamos fazerAnimalEmitirSom(animal:), mesmo que o parâmetro seja do tipo Animal, o método correto (de acordo com o tipo específico da subclasse) é chamado graças ao polimorfismo.`

### ***`Como funciona:`***

* **`Override de Métodos`**`: Cada subclasse sobrescreve o método da classe base, criando uma implementação única.`  
* **`Tratar Diferentes Objetos de Forma Uniforme`**`: Usamos uma função (fazerAnimalEmitirSom) que aceita qualquer objeto do tipo Animal, mas o comportamento específico de cada subclasse é executado.`

### `Polimorfismo em compile-time`

`Este tipo de polimorfismo consegue-se através de overloading de funções`

| `func addNumbers(_ a: Int, _ b: Int) -> Int {  return a + b}func addNumbers(_ a: Double, _ b: Double) -> Double {  return a + b}let intResult = addNumbers(3, 5) // chama a primeira função com Intlet doubleResult = addNumbers(4.5, 5.5) // chama a segunda função com Double` |
| :---- |

**`Extras:`** 

## **`Overloading`**

`É o processo pelo qual uma classe possui dois ou mais métodos com o mesmo nome, mas parâmetros diferentes, e ou tipos de retorno diferentes.`  
`Os return types das funções acima não são os mesmos. Isso ocorre porque o overloading de funções não está associado aos return types.`  
`Funções overloaded podem ter return types iguais ou diferentes, mas devem diferir em parâmetros`

### `Overloading com parámetros de tipos diferentes`

| `func displayValue(value: Int) { //recebe Int    print("Integer value:", value)}func displayValue(value: String) { //recebe String    print("String value:", value)}displayValue(value: "Swift")displayValue(value: 2)` |
| :---- |

### `Overloading com número de parâmetros diferentes`

| `func display(number1: Int, number2: Int) { //recebe 2 parametros   print("1st Integer: \(number1) and 2nd Integer: \(number2)")}func display(number: Int) { //recebe 1 parametro   print("Integer number: \(number)")}display(number: 5)display(number1: 6, number2: 8)` |
| :---- |

### `Overloading com diferentes argument label`

| `func display(person1 age:Int) {    print("Person 1 Age:", age)}func display(person2 age:Int) {    print("Person 2 Age:", age)}display(person1: 25)display(person2: 38)` |
| :---- |

## **`Overriding`**

`Se o mesmo método for definido na superclasse e na subclasse, então o método da classe da subclasse substitui o método da superclasse. Isso é conhecido como override.`

| `class Vehicle {func displayInfo() { print("Four Wheeler or Two Wheeler")}}class Car: Vehicle {override func displayInfo() { print("Four Wheeler")}}var car1 =  Car()car1.displayInfo()` |
| :---- |

### ***`Resumo:`***

`No exemplo acima, estamos a substituir o método displayInfo() da superclasse Vehicle dentro da subclasse Car.`  
`Agora, quando chamamos o método displayInfo() usando o objeto car1 de Car, é o método displayInfo() dentro da subclasse Car que é chamado.`

#### `Impedir override de um método`

`Pode-se evitar que o método seja override usando a notação final ao declarar um método na superclasse.`

| `` class Vehicle { final func displayInfo() {   print("Four Wheeler or Two Wheeler") }}class Car: Vehicle { override func displayInfo() {   print("Four Wheeler") }}var car1 =  Car()car1.displayInfo() //`error: instance method overrides a 'final' instance method` `` |
| :---- |

### ***`Resumo:`***

`Uma vez que o método é declarado como final, não podemos fazer override. Então, quando tentamos substituir o método final recebemos uma mensagem de erro: error: instance method overrides a 'final' instance method`

### `Override de computed var`

| `` class University {var cost: Int {return 5000}}class Fee: University {override var cost: Int {return 10000}}var amount = Fee()print("New Fee:", amount.cost) //prints `New Fee: 10000 ` `` |
| :---- |

### ***`Resumo:`***

`Agora, quando acedemos à propriedade cost usando o objeto Fee, é a propriedade cost dentro da subclasse Fee que é chamada.`

## **`S.O.L.I.D.`**

`SOLID é um acrônimo dos cinco primeiros princípios da programação orientada a objetos e design de código`

- `S : Single Responsibility Principle`  
- `O : Open/Closed`  
- `L : Liskov Substitution Principle`  
- `I : Interface Segregation Principle`  
- `D : Dependency Inversion`

# **`S - Single Responsibility Principle (SRP)`**

`Uma classe deve ter um, e somente um, motivo para mudar.`

`Uma classe ou módulo deve ter apenas uma razão para mudar. Em outras palavras, uma classe deve ter uma única responsabilidade bem definida.`  
`Isso promove a coesão e evita o acoplamento excessivo entre classes. Em Swift, podemos aplicar o SRP dividindo uma classe em várias classes menores, cada uma com uma responsabilidade específica`

##### ***`Exemplo de Aplicação :`***

| `import Foundationclass TwitterManager{    private func request() -> Data {        return Data()  // requisição para a API do Twitter    }    private func convertJsonToModel(with data: Data) -> [AnyObject]{        return [AnyObject]() // parse do JSON    }    private func saveInCoreData(with models: [AnyObject]){        // gravar o modelo no core data    }    public func create(){        let data = request()        let model = convertJsonToModel(with: data)        saveInCoreData(with: model)    }}class RequestManager {    func requestFB() -> Data {        return Data()    }    func requestTwitter() -> Data {        return Data()    }}class ParseManager {    func convert(data:Data) -> [AnyObject] {        return [AnyObject]()    }}class CoreDataManager {    func save(models:[AnyObject]) {    }}` |
| :---- |

###### `Qual o problema do código acima?`

`Como podemos perceber, a classe TwitterManager apresenta muitas responsabilidades desde do request para o seu endPoint até salvar localmente no banco de dados.`

`Como podemos resolver esse problema?`  
`Separando as responsabilidades, criando classes que tenham apenas uma responsabilidade em vez de uma que é a "faz tudo".`

`Deste modo mantém-se a alta coesão e o baixo acoplamento entre as classes, e consegue-se fazer testes unitários muito mais assertivos, testando diretamente os métodos já que eles não são privados.`

##### ***`Aplicação :`***

`Aplicamos o SRP ao separar as "responsabilidades" e assim cada classe fica apenas encarregue de uma só coisa.`

`No caso abaixo verifica-se que o NetworkingManager apenas faz o request.`

| `import Foundationclass RequestManager {    func request() -> Data{        return Data()    }}class ParseManager{    func convertJsonToModel(with data: Data) -> [AnyObject]{        return [AnyObject]()    }}class CoreDataManager{    fileprivate func saveInCoreData(with models: [AnyObject]){    }}class TwitterManager{    private let requestManager:RequestManager    private let parse:ParseManager    private let coreManager:CoreDataManager    init(requestManager:RequestManager, parseManager:ParseManager, coreManager:CoreDataManager){        self.requestManager = requestManager        self.parse = parseManager        self.coreManager = coreManager    }    func create(){        let data = self.requestManager.request()        let objects = self.parse.convertJsonToModel(with: data)        coreManager.saveInCoreData(with: objects)    }}` |
| :---- |

### **`O - Open/Closed Principle`**

`Objetos ou entidades devem estar abertos para extensão, mas fechados para modificação.`  
`Classes, módulos ou funções devem ser abertas para extensão, mas fechadas para modificação.`  
`Em vez de alterar o código existente para adicionar novos comportamentos, devemos estender o comportamento existente através de herança, protocolos ou composição.`  
`Em Swift, isso pode ser alcançado por meio de protocolos e extensões.`

***`Exemplo de Aplicação :`***

| `class Cat {    var name: String        init(name: String) {        self.name = name    }        func animalInfo() -> String {        return "I am Cat and name is \(self.name)"    }}class Fish {    var name: String        init(name: String) {        self.name = name    }        func animalInfo() -> String {        return "I am fish and name is \(self.name)"    }}class AnimalsInfo {    func printData() {        let cats = [Cat(name: "Luna"), Cat(name: "Tina"), Cat(name: "Moon")]                for cat in cats {            print(cat.animalInfo())        }                let fishes = [Fish(name: "Ishxan"), Fish(name: "Karas"), Fish(name: "Sterlec"), Fish(name: "fish")]        for fish in fishes {            print(fish.animalInfo())        }    }}let infoOfAnimals = AnimalsInfo()infoOfAnimals.printData()` |
| :---- |

### `Qual o problema do código acima?`

`Toda vez que houver a necessidade de adicionar um novo tipo de animal no futuro será necessário modificar na classe AnimalsInfo o método printData() e isso viola o Open-Closed Principle.`

### `Como podemos resolver esse problema?`

`Criar um protocolo AnimalInfo com o método animalInfo(). Este método pode ser implementado em qualquer classe que queira animalInfo.`

### ***`Resolução`* `:`**

`Agora podemos criar qualquer classe animal, mas a implementação base do AnimalInfo nunca será alterada. Só pode ser estendido em subclasses.`

| `protocol AnimalInfo {    func animalInfo() -> String}class Cat: AnimalInfo {    var name: String        init(name: String) {        self.name = name    }        func animalInfo() -> String {        return "I am Cat and name is \(self.name) and I meow !!! "    }}class Fish: AnimalInfo {    var name: String        init(name: String) {        self.name = name    }        func animalInfo() -> String {        return "I am Fish and name is \(self.name) and I travel the oceans ~~~~~~~~"    }}class Dog: AnimalInfo {    var name: String        init(name: String) {        self.name = name    }        func animalInfo() -> String {        return "I am dog and name is \(self.name) and I bark and play...."    }}` |
| :---- |

# **`L - Liskov Substitution Principle (LSP)`**

`Uma classe derivada deve ser substituível por sua classe base.`  
`As classes base devem ser substituíveis por suas classes derivadas.`  
`Isso significa que, ao usar herança, as classes filhas não devem quebrar as expectativas da classe pai.`  
`Em Swift, é fundamental garantir que as subclasses não alterem o contrato definido pelas classes pai.`

***`Exemplo de Aplicação :`***  
`Considere as classes Rectangle e Square, onde Square é uma subclasse de Rectangle. Se a lógica de negócios espera um objeto do tipo Rectangle, o LSP garante que podemos substituir isso por um objeto do tipo Square sem causar problemas na funcionalidade esperada.`

| ``import UIKitclass Rectangle {    private var width: Int    private var height: Int    init(width: Int, height: Int) {        self.width = width        self.height = height    }    func set(width: Int) {        self.width = width    }    func set(height: Int) {        self.height = height    }}class Square: Rectangle {    // Violação do Liskov Substitution Principle: classe herdada faz `override` ao comportamento dos métodos da classe `parent`    override init(width: Int, height: Int) {        super.init(width: width, height: height)    }    override func set(width: Int) {        super.set(width: width)    }    override func set(height: Int) {        super.set(height: height)    }}let rectangle = Rectangle(width: 200, height: 100)let square = Square(width: 200, height: 100)`` |
| :---- |

### `Qual o problema do código acima?`

`Square não é um quadrado porque só deveria ter 1 lado igual e não 2 lados diferentes. Logo existe quebra de contrato pois a width tem de ser diferente da height para ser um Rectangle`

### `Importante :`

`Por que precisamos passar altura e largura para um quadrado sendo que ele tem os lados iguais?`  
`Sempre que fomos construir um quadrado temos de ter cuidado para passar valores iguais e se por acaso alguém esquecer disso?`

### ***`Resolução :`***

`Define-se um protocol Shape com os métodos comuns`

| `protocol Shape {    var area: Int { get }    var perimeter: Int { get }}class Rectangle: Shape {    private var width: Int    private var height: Int    init(width: Int, height: Int) {        self.width = width        self.height = height    }    func set(width: Int) {        self.width = width    }    func set(height: Int) {        self.height = height    }    var area: Int {        return width * height    }    var perimeter: Int {        return 2 * (width + height)    }}class Square: Shape {    private var side: Int    init(side: Int) {        self.side = side    }    func set(side: Int) {        self.side = side    }    var area: Int {        return side * side    }    var perimeter: Int {        return 4 * side    }` |
| :---- |

`Ao fazer com que Rectangle e Square estejam em conformidade com o protocolo Shape, garantimos que eles podem ser usados ​​de forma intercambiável onde um Shape é esperado, sem violar o Princípio de Substituição de Liskov.`

`Dessa forma, o comportamento de cada classe é consistente com suas propriedades e restrições específicas.`  
 

# **`I - Interface Segregation Principle (ISP)`**

`Uma classe não deve ser forçada a implementar interfaces e métodos que não irá utilizar.`

***`Exemplo de Aplicação :`***

`Suponha que temos uma interface Trabalhador com métodos trabalhar() e cantar(). Se uma classe Engenheiro não precisa do método cantar(), aplicando o ISP, podemos dividir essa interface em interfaces menores, como Trabalhador e Artista, permitindo que as classes implementem apenas o que é relevante para elas.`

| `// Interface específica para o trabalhoprotocol Trabalhador {    func trabalhar()}// Interface específica para cantarprotocol Artista {    func cantar()}// Classe Engenheiro, que só precisa trabalharclass Engenheiro: Trabalhador {    func trabalhar() {        print("O engenheiro está a trabalhar.")    }}// Classe Cantor, que precisa tanto trabalhar quanto cantarclass Cantor: Trabalhador, Artista {    func trabalhar() {        print("O cantor está a trabalhar.")    }    func cantar() {        print("O cantor está a cantar.")    }}// Exemplo de uso:let engenheiro = Engenheiro()engenheiro.trabalhar() // O engenheiro está a trabalhar.let cantor = Artista()cantor.trabalhar() // O cantor está a trabalhar.cantor.cantar()    // O cantor está a cantar.` |
| :---- |

### 

### ***`Explicação:`***

**`Interface Trabalhador`**`: Contém apenas o método trabalhar(). Qualquer classe que represente uma profissão que requer trabalho, mas não canto, pode implementar essa interface.`

**`Interface Artista`**`: Contém apenas o método cantar(). Esta interface é usada apenas por classes que representam profissões ou papéis que envolvem canto.`

**`Classe Engenheiro`**`: Implementa apenas a interface Trabalhador, pois os engenheiros trabalham, mas não precisam implementar cantar().`

**`Classe Cantor`**`: Implementa tanto Trabalhador quanto Artista, pois pode exercer ambas as funções.`

# **`D - Dependency Inversion Principle (DIP)`**

`Depender de abstrações e não de implementações.`  
`Em vez de uma classe de alto nível depender diretamente de uma classe de baixo nível, podemos introduzir uma interface ou classe abstrata comum entre elas. Isso permite que a classe de alto nível dependa da abstração, não da implementação específica de baixo nível.`

***`Exemplo de Aplicação :`***

* `Uma classe PagamentoService que representa um módulo de "alto nível" e depende de uma interface (ProcessadorPagamento).`  
* `Implementações concretas como PaypalService e CartaoCreditoService que representam módulos de "baixo nível" e implementam essa interface.`

`Sem DIP, a classe PagamentoService estaria diretamente acoplada a uma implementação específica como PaypalService, o que limitaria a flexibilidade e dificultaria a manutenção.`

| `class PaypalService {    func processarPagamento(valor: Double) {        print("Pagamento de \(valor) processado via PayPal.")    }}class PagamentoService {    let paypalService = PaypalService()    func realizarPagamento(valor: Double) {        paypalService.processarPagamento(valor: valor)    }}// Uso:let pagamentoService = PagamentoService()pagamentoService.realizarPagamento(valor: 100.0)// Saída: Pagamento de 100.0 processado via PayPal.` |
| :---- |

### `Qual o problema do código acima?`

`A classe PagamentoService está fortemente acoplada à implementação de PaypalService. Se quisermos mudar para outro serviço de pagamento (como cartão de crédito), teremos que modificar a classe PagamentoService, violando o Open/Closed Principle e dificultando a manutenção.`

### `Como podemos resolver esse problema?`

`Deve-se depender de abstrações e não de implementações de outras classes de modo a evitar o acoplamento elevado.`

### ***`Resolução :`***

`Em vez de PagamentoService depender diretamente de PaypalService, ela dependerá de uma abstração (um protocolo ProcessadorPagamento), e implementações específicas como PaypalService e CartaoCreditoService que serão fornecidas externamente.`

| `protocol ProcessadorPagamento {    func processarPagamento(valor: Double)}class PaypalService: ProcessadorPagamento {    func processarPagamento(valor: Double) {        print("Pagamento de \(valor) processado via PayPal.")    }}class CartaoCreditoService: ProcessadorPagamento {    func processarPagamento(valor: Double) {        print("Pagamento de \(valor) processado via Cartão de Crédito.")    }}class PagamentoService {    let processador: ProcessadorPagamento    // O processador é injetado via inicialização, promovendo inversão de controlo (IoC)    init(processador: ProcessadorPagamento) {        self.processador = processador    }    func realizarPagamento(valor: Double) {        processador.processarPagamento(valor: valor)    }}let paypalService = PaypalService()let pagamentoService1 = PagamentoService(processador: paypalService)pagamentoService1.realizarPagamento(valor: 100.0)// Saída: Pagamento de 100.0 processado via PayPal.let cartaoService = CartaoCreditoService()let pagamentoService2 = PagamentoService(processador: cartaoService)pagamentoService2.realizarPagamento(valor: 200.0)// Saída: Pagamento de 200.0 processado via Cartão de Crédito.` |
| :---- |

**`Abstrações dependem de detalhes:`** `O PagamentoService depende da abstração ProcessadorPagamento e não de detalhes concretos como PaypalService ou CartaoCreditoService. Isso significa que podemos facilmente trocar a implementação do serviço de pagamento sem modificar o código de PagamentoService.`

**`Inversão de Controlo (IoC):`** `Ao passar o processador de pagamento como dependência no inicializador de PagamentoService, estamos aplicando o conceito de Inversão de Controlo. Isso promove maior flexibilidade, já que o serviço de pagamento não "sabe" ou "controla" qual o processador que será usado.`

**`Baixo Acoplamento:`** `Agora, a classe PagamentoService está desacoplada de implementações específicas. Se quisermos adicionar um novo serviço de pagamento, como BitcoinService, basta criar uma nova classe que implemente ProcessadorPagamento sem modificar a lógica de PagamentoService.`


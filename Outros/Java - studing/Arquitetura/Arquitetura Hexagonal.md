
> [!note] [[Home page studing Java]]


A Arquitetura Hexagonal, também conhecida como Arquitetura de Portos e Adaptadores (Ports and Adapters), foi proposta por Alistair Cockburn e é uma maneira de estruturar sistemas de software para torná-los mais flexíveis, testáveis e independentes de tecnologias específicas.

Ela pode parecer um pouco complexa no início, mas vou tentar simplificar o conceito para que qualquer pessoa possa entender.

### 1. **O Problema**

Imagine que você está construindo uma casa. A casa tem várias portas de entrada e saída: uma porta da frente, uma porta lateral, talvez uma porta dos fundos. Cada porta permite que você entre e saia da casa de maneiras diferentes, mas o que está dentro da casa permanece o mesmo, independentemente da porta que você usa.

Agora, pense em um sistema de software. Muitas vezes, esses sistemas são construídos de maneira que as partes internas estão muito ligadas ao "mundo exterior" — como interfaces de usuário, APIs, bancos de dados, etc. O problema é que quando uma dessas "portas" (como a interface com o banco de dados ou a API) muda, você acaba tendo que alterar várias coisas dentro do sistema.

### 2. **A Solução: Arquitetura Hexagonal**

A Arquitetura Hexagonal resolve esse problema ao separar claramente o **coração da aplicação** (a lógica de negócios) das **entradas e saídas** (como APIs, bancos de dados, interfaces de usuário). Dessa forma, você pode mudar ou adicionar "portas" sem mexer na lógica central.

Pense na aplicação como um **hexágono** com várias portas ao redor. Cada porta (ou adaptador) permite que a aplicação interaja com o mundo exterior de diferentes maneiras. Essas portas são chamadas de **Portos** e os adaptadores que se conectam a essas portas permitem que diferentes tecnologias sejam usadas para interagir com a aplicação.

### 3. **Componentes da Arquitetura Hexagonal**

Para entender melhor, vamos ver as partes que compõem essa arquitetura:

- **Núcleo (Core)**: No centro está o **núcleo** da aplicação, que contém a lógica de negócios, ou seja, as regras e operações principais que o sistema realiza. O núcleo não sabe nada sobre o "mundo exterior". Ele não se preocupa com como os dados chegam, se vêm de um banco de dados ou de uma API, apenas executa suas regras.
    
    - **Domínio (Entities)**: Classes que representam os objetos centrais da aplicação. Essas são as coisas sobre as quais a aplicação opera, como um "Pedido", "Cliente", "Produto", etc.
        
    - **Portos (Ports)**: São interfaces que definem **o que** o núcleo precisa fazer, mas não **como** isso será feito. É como se fosse um contrato dizendo: "Eu preciso que isso seja feito", mas não especifica quem ou como será feito.
        
- **Adaptadores (Adapters)**: Fora do núcleo, temos os **adaptadores**. Eles conectam o núcleo à "vida real", ou seja, eles permitem que o sistema interaja com o mundo exterior. Existem dois tipos de adaptadores:
    
    - **Adaptadores de Entrada (Driving Adapters)**: Eles **levam dados até o núcleo**. Um exemplo é um controlador de API que recebe uma requisição HTTP e passa para o núcleo, ou uma interface de linha de comando que o usuário usa para interagir com o sistema.
        
    - **Adaptadores de Saída (Driven Adapters)**: Eles são usados quando o núcleo precisa **obter dados ou enviar dados para fora**. Por exemplo, quando o sistema precisa gravar algo em um banco de dados ou chamar uma API de terceiros. Esses adaptadores implementam as interfaces definidas pelos portos de saída do núcleo.
        

### 4. **Como Funciona na Prática?**

Imagine que você está criando um sistema de pedidos de comida. Na arquitetura hexagonal, você faria o seguinte:

- O **núcleo** da aplicação contém a lógica de como os pedidos são criados, como os clientes fazem pedidos, como os pagamentos são processados, etc. O núcleo não sabe se o pedido veio de um site ou de um aplicativo móvel, nem sabe onde os dados estão sendo armazenados.
    
- Os **adaptadores de entrada** podem ser uma API REST, uma interface de linha de comando ou até uma interface gráfica de usuário (GUI). Eles pegam as ações do usuário (como "fazer um pedido") e enviam essas informações para o núcleo.
    
- Os **adaptadores de saída** são responsáveis por interagir com o banco de dados, um serviço de pagamento externo, ou qualquer outro sistema que o núcleo precise acessar. Eles implementam as interfaces definidas pelo núcleo, mas a lógica do núcleo não sabe ou se importa se você está usando um banco de dados MySQL ou MongoDB, por exemplo.
    

### 5. **Por que Hexagonal?**

O formato hexagonal é apenas uma metáfora visual para ilustrar que o sistema pode ter várias "portas" ao redor do núcleo, permitindo interações de diferentes fontes (API, banco de dados, CLI, etc.). O número de lados do hexágono não importa; ele simboliza múltiplas entradas e saídas.

### 6. **Vantagens da Arquitetura Hexagonal**

- **Flexibilidade**: Você pode trocar um banco de dados por outro ou substituir uma API externa sem mudar o núcleo da aplicação.
- **Testabilidade**: Como o núcleo não depende de detalhes externos, você pode testar a lógica de negócios sem precisar de um banco de dados real ou uma API.
- **Isolamento de Mudanças**: Alterações em uma "porta" (adaptador) não afetam o núcleo ou outras partes do sistema.

### Exemplo de Código Simplificado

Imagine que temos uma aplicação que processa pedidos:

#### 1. Porto de Entrada (Definido pelo núcleo)

```
public interface PedidoService {
    Pedido processarPedido(PedidoRequest request);
}
```

#### 2. Implementação do Núcleo

```
public class PedidoServiceImpl implements PedidoService {
    private final RepositorioPedido repositorioPedido; // Porto de saída
    
    public PedidoServiceImpl(RepositorioPedido repositorioPedido) {
        this.repositorioPedido = repositorioPedido;
    }

    @Override
    public Pedido processarPedido(PedidoRequest request) {
        Pedido pedido = new Pedido(request.getClienteId(), request.getItens());
        return repositorioPedido.salvar(pedido); // Usando um adaptador de saída
    }
}
```

#### 3. Porto de Saída (Definido pelo núcleo)

```
public interface RepositorioPedido {
    Pedido salvar(Pedido pedido);
}
```
#### 4. Adaptador de Entrada (Por exemplo, uma API REST)

```
@RestController
@RequestMapping("/api/pedidos")
public class PedidoController {
    private final PedidoService pedidoService;

    public PedidoController(PedidoService pedidoService) {
        this.pedidoService = pedidoService;
    }

    @PostMapping
    public ResponseEntity<Pedido> criarPedido(@RequestBody PedidoRequest request) {
        Pedido pedido = pedidoService.processarPedido(request);
        return ResponseEntity.ok(pedido);
    }
}
```
#### 5. Adaptador de Saída (Por exemplo, um repositório JPA)

```
@Repository
public class RepositorioPedidoJpa implements RepositorioPedido {
    
    private final PedidoRepository pedidoRepository;

    public RepositorioPedidoJpa(PedidoRepository pedidoRepository) {
        this.pedidoRepository = pedidoRepository;
    }

    @Override
    public Pedido salvar(Pedido pedido) {
        return pedidoRepository.save(pedido);
    }
}
```

### Resumo

A Arquitetura Hexagonal separa a lógica central (o núcleo) do sistema das interfaces externas (como bancos de dados, APIs, etc.), permitindo flexibilidade e testabilidade. É como ter várias portas de entrada e saída que podem ser alteradas sem impactar o interior da casa (a lógica de negócios).


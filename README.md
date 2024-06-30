# sintaxes-java
 <details>
  <summary>OO</summary>
  
  ### Invocando o contrutor da classe pai

 - Em algumas situações é necessário reaproveitar um construtor já declarado em uma classe pai e para explicar como reaproveitar irei demonstrar um situação.
 
 - Temos a classe abstrata Brasileiro que possui seus atributos como final e também tem seu método construtor.A partir da classe Brasileiro, podemos construit outras classes como Pernambucano,Carioca e Amazonense,no entanto os atributos de Brasileiro são finais e só podem ter valores atribuidos no momento de sua declaração.Sendo assim, uma forma de poder modificar o valor desses atributos em outras classes é reaproveitando o método construtor da classe pai.Para fazer isso, basta chamar o método construto da classe matriz com o ´super´, os valores serão recebidos por meio dos parâmetros do método construtor da classe filha.

```java
public abstract Brasileiro{

  private final String nome;
  private final String cpf;
  private final String rg;
  
  public Brasileiro(String nome, String cpf, String rg){
    this.nome = nome;
    this.cpf = cpf;
    this.rg = rg;
  }
}
```
```java
public class Pernambucano extends Brasileiro{

  public Pernambucano(String nome, String cpf, String rg){
    super(nome, cpf, rg);
  }
}
```
  

  
 </details>
 <details>
  <summary>java.lang</summary>
  <details>
   <summary>Classe Object</summary>
   
   ## Classe Object
   - É a superclasse de todas as classes em java e é definida no pacote java.lang.Isso significa que todas as  classes em java herdam a classe Object.

   ### Métodos importantes da classe
   #### equals
   - Este método é usado para comparar se dois objetos são iguais em termos de conteúdo.
   - Por padrão, a comparação desse método é a referência da memória e para comparar o conteúdo, é necessário sobrescrever o método.
   - o método equals não pode ser usado diretamente com tipos primitivos em Java, pois ele é um método de objetos e tipos primitivos não são objetos.
   ```C#
    package Exercicios;

    import java.util.Objects;

    public class App3 {
    private String a;
    private String b;

    public void compare(String a, String b) {
        if(a.equals(b)){
            System.out.println("a é igual a b");
        }else{
            System.out.println("a não é igual a b");
        }

    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        App3 app3 = (App3) o;
        return a == app3.a && b == app3.b;
    }

    public static void main(String[] args) {
        App3 teste = new App3();
        teste.compare("bom dia","bom dia");
    }
}
   ```

  ## toString
  - Usado para retornar uma representação String de um objeto e seus atributos
  - O método não vem com essa funcionalidade por padrão e é necessário sobrescrever para ser possível utiliza-ló de uma forma alternativa.
  - O método não imprime,apenas faz a formatação de saída.
  ```C#
  package Exercicios;

  public class App4 {
    public String nome;
    public int idade;

    @Override
    public String toString() {
        return "App4{" +
                "nome='" + nome + '\'' +
                ", idade=" + idade +
                '}';
    }

    public static void main(String[] args) {
        App4 pessoa = new App4();
        pessoa.nome="Athos";
        pessoa.idade=22;
        System.out.println(pessoa.toString());

    }
}

  ```
  
  </details>
 </details>
 <details>
  <summary>Classe String</summary>
  
  ## Variáveis, armazenamento e Strings
  
  ### Atribuição literal de uma string 
   - Quando é feita a atribuição literal de uma string, a variável é armazenada em um Pool de strings.
   O pool de strings é a memória reservada que o java usa para guardar valores de forma única,
   Ou seja, caso exista duas variáveis com valores idênticos, as duas variáveis irão apontar para
   o mesmo valor no pool de strings e terão o mesmo endereço de memória.
   
   ```java
   String s1 = "Carlos";
   String s2 = "Ana";
   String s3 = "Carlos";
   String s4 = "Ana";
   String s5 = "Luiz";
   ```
  ![Captura de tela de 2023-10-18 19-35-23](https://github.com/AthosGustavo/sintaxes-java/assets/112649935/ed1b116f-7e41-4ebb-96d9-1e1a4b7930cb)

  ### Instânciação da classe String
   - Ao instânciar uma classe, a variável é tratada como um objeto na memória e possui endereço de memória único.

  ## Comparando Strings

  ### Comparando Strings com operador igual
   - O operador de igual é usado para comparar o endereço de memória e não os valores que estão associados a essa memória.

  ```java
    String nomeInstancia = new String("athos");
    String nomeInstanciaDois = new String("athos");
        
    if(nomeInstancia == nomeInstanciaDois){
    System.out.println("nomeInstancia == nomeInstanciaDois");
    }else{
      System.out.println("Não são iguais");  //nao sao iguais
    }
   ```

  ### Comparando Strings com equals()
   - equals compara os valores associados as variáveis

   ```java
    String nomeInstancia = new String("athos");
    String nomeInstanciaDois = new String("athos");
        
    if(nomeInstancia.equals(nomeInstanciaDois)){
    System.out.println("nomeInstancia == nomeInstanciaDois"); // São iguais
    }else{
      System.out.println("Não são iguais");  //nao sao iguais
    }
   ```

  ## Imutabilidade das Strings
   - As Strings são imutáveis, existe uma diferença entre reescrever o valor de uma String e mutar esse valor.Para reescrever basta literamente apagar o valor da String e colocar outro,por sua vez, a mutação é diferente.

  ### Mutação de String
   - Em um exemplo como esse asseguir não modificará o valor da variável nome, será necessário atribuir a mutação a outra variável e o valor antigo ainda continuará existindo.

  ```java
  String nome = "athos";
  String nomeAlterado = nome.toUpperCase();
  System.out.println(nomeAlterado);
  ```

  <details>
  <summary>Métodos String</summary>
   
   ## Métodos String
   
   ### length
   - Usado para retornar o tamanho de uma string ou array
   ```java
   String originalString = "Olá, Mundo!";
        
   int comprimento = originalString.length();
   System.out.println("Comprimento da string: " + comprimento);
   ```
    
  ### substring
  - Usada para extrair uma parte de uma string
  - Ex: substring(int beginIndex, int endIndex)

  ```java
  String originalString = "Olá, Mundo!";

  String substring = originalString.substring(0, 5);
  System.out.println("Substring: " + substring);
  
  ```
  ### concat
  - Usado para unir uma String a outra
  
  ```java
  String originalString = "Olá, Mundo!";

  String outraString = " Isso é um exemplo.";
  String concatenada = originalString.concat(outraString);
  System.out.println("String concatenada: " + concatenada);
  
  ```
    
  ### contains
  - Usado para verificar se uma string comtém uma determinada sequência

  ```java
  String frase = "Java é uma linguagem de programação poderosa.";

  // Verificando se a string contém uma sequência específica
  String sequencia = "linguagem";

  if (frase.contains(sequencia)) {
    System.out.println("A string contém a sequência: " + sequencia);
  } else {
    System.out.println("A string NÃO contém a sequência: " + sequencia);
  }
  ```
  ### replace
  - Usado para substituir caracteres em uma String
  - replace(oldChar, newChar);
  ```java
  String originalString = "Olá, Mundo!";

  String substituida = originalString.replace('o', 'X');
  System.out.println("String com substituição: " + substituida);
  ```
 
 </details> 
</details>
 

<details>
 <summary>Listas e Arrays</summary>
 <details>
  <summary>Arrays simples</summary>

   ## Arrays simples

### Regras dos arrays simples
 - estruturas estáticas
 - Não permiti alocação de valores de forma dinâmica
 - A sua capacidade não pode ser mudada após a declaração, exceto com gambiarras.
 - Não é possível declara um array vazio e após preenche-lo com a quantidade de valores que bem entender.Apenas é possível declara um array com uma capacidade x e após isso preencher com valores a sua campacidade x.

### Sintaxes de declaração de um array simples

**DECLARAÇÃO**

```
int[] numeros;
numeros = new int[capacidade]
```

**INICIALIZAÇÃO:APENAS EXISTE DUAS MANEIRAS DE INICIALIZAR UM ARRAY!**

Usando a palavra chave new
```
int[] numeros = new int[5];
```
alocando os valores na declaração
```
int[] numeros = {1, 2, 3, 4};
```
  
 </details>
 <details>
  <summary>ArrayList</summary>

   ## ArraysList

   ### Regras dos ArraysList
   - Podem crescer e diminuir dinâmicamente

   **DECLARAÇÃO**

   Declarando um array vazio
   ```
   ArrayList<String> listaDeNomes = new ArrayList<>();
   ```

   Declarando um ArrayList com elementos iniciais
   ```
   ArrayList<Integer> numeros = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5));

   ```
 </details>
</details>

<details>
 <summary>CAST</summary>
 
 ## Cast
 - O cast se baseia na conversão de um tipo de variável para o outro.

 ### cast implícito
 
 ```C#
 int numero = 3;
 double valor = numero;
 ```
 - Colocamos um valor da variável número (tipo int) na variável valor (tipo double) sem usar um cast explícito.Isso funciona,pois qualquer inteiro cabe dentro de um double, por esse motivo o compilador não exibe erro.
 ```C#
 double numeroDouble = 4.75;
 int numeroInt = (int) numeroDouble;
 ```
 - Nesse caso, é necessário fazer um cast explícito, pois um double não cabe um int.




 
</details>

<details>
 <summary>HttpClient</summary>
 
 ## Explicando as principais classes do HttpClient de uma forma simplificada.

 ### HttpClient
 - Responsável por abrir e enviar a solicitação.

 ### HttpRequest
 - Responsável por preparar os detalhes da solicitação, incluindo os métodos HTTP.
 - Define como a solicitação será formatada antes de seer enviada.

 ### HttpResponse
 - Responsável por receber a resposta da requisição
 - Contém informações sobre o código de status da resposta, os cabeçalhos da resposta e o corpo da resposta.
 - Permite  acessar e processar o conteúdo da resposta, como texto, JSON ou outros.

 ```java
 import java.net.URI;
 import java.net.http.HttpClient;
 import java.net.http.HttpRequest;
 import java.net.http.HttpResponse;
 import java.io.IOException;
 import java.net.http.HttpHeaders;

 public class Main {
     public static void main(String[] args) throws IOException, InterruptedException {

         String regiao = "Brasil";
         // HttpClient é uma classe abstrata e newHttpClient() é um método estático
         HttpClient httpClient = HttpClient.newHttpClient();

         String chaveApi = "8d477a13299a1dc90901fac477cc83d3";
         String apiUrl = "http://api.openweathermap.org/data/2.5/weather?q=" + regiao + "&appid=" + chaveApi;

         HttpRequest requisicao = HttpRequest.newBuilder()
             .uri(URI.create(apiUrl))
             .build();

         HttpResponse<String> resposta = httpClient.send(requisicao, HttpResponse.BodyHandlers.ofString());

         int statusCode = resposta.statusCode();
         String responseBody = resposta.body();

         System.out.println("Código de status: " + statusCode);
         System.out.println("Resposta do servidor:");
         System.out.println(responseBody);
     }
  }

 ```

</details>
<details>
 <summary>Classe anônima</summary>

 # Classe anônima
 - A classe anônima pode ser usada para obter métodos implementados em uma interface pelo motivo de desacoplamento de um método a partir de uma classe.Ao invés de implementar o método na classe, o método é implementado em uma interface.

 ## Situações onde é indicado o uso de uma classe anônima
 - Métodos simples e curtos que não são reutilizados e precisam ser flexíveis para serem usados em diferentes cenários.

 ## Situações onde não é indicado o uso de uma classe anônima
 - `Quando a implementação precisa ser reutilizada`
 - `Quando a implementação é complexa:` Se a implementação do método é complexa e contém muitas linhas de código, pode ser melhor criar uma classe separada.

 *EXEMPLO USANDO CLASSE ANÔNIMA*
 ```java
 public interface CalculosMontagemCarro{
  public void calculosMontagemCarro();
 }

public class CarroCustoMontagem{

  public void carroValorTotal(CalculosMontagemCarro calculosMontagemCarro){
    //régra de negócio
   }
 }

 CarroCustoMontagem carroCustoMontagem = new CarroCustoMontagem();

 carroCustoMontagem.carroValorTotal(new CalculosMontagemCarro(){

   @Override
   public void calculosMontagemCarro(){
     //régra de negócio
   }
  
 });
 ```
 *SEM USAR CLASSE ANÔNIMA*
 ```java
  public class CarroCustoMontagem{

   public void carroValorTotal(CalculosMontagemCarro calculosMontagemCarro){
     //régra de negócio
   }
  }

  public class CalculosMontagemCarroImpl implements CalculosMontagemCarro {
   @Override
   public void calculosMontagemCarro(){
     //régra de negócio
   }
  }

  CarroCustoMontagem carroCustoMontagem = new CarroCustoMontagem();
  CalculosMontagemCarro calculosMontagemCarro = new CalculosMontagemCarroImpl();

  carroCustoMontagem.carroValorTotal(calculosMontagemCarro);
 ```
   
</details>




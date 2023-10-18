# sintaxes-java


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









# 📘 Exercícios  

1. **Tabuada**
2. **Cálculo do seu IMC**
3. **Par ou Impar**
4. **Divide = Zero**

Cada código está documentado com Javadoc e comentários explicativos.

---
# 1 — Tabuada
```java
import java.util.Scanner;

/**
 * Escreva um código onde o usuário entra com um número
 * e seja gerada a tabuada de 1 até 10 desse número.
 *
 * <p>Este programa utiliza a classe {@link Scanner} para leitura de dados
 * via teclado e imprime a tabuada completa do número informado.</p>
 *
 * author Marcelo Guimarães Carvalho
 * version 1.0
 * since 2025-01-28
 */
public class Main {

    /**
     * Método principal da aplicação.
     *
     * @param args argumentos de linha de comando (não utilizados neste programa)
     */
    public static void main(String[] args) {

        // Cria um objeto Scanner para ler dados digitados pelo usuário no console
        Scanner entradaDados = new Scanner(System.in);

        // Declara uma variável do tipo int para armazenar o número informado pelo usuário
        int numero;

        // Exibe a pergunta ao usuário sem pular de linha
        System.out.print("Quer a tabuada de qual número? ");

        // Lê um número inteiro digitado pelo usuário e armazena em "numero"
        numero = entradaDados.nextInt();

        // Limpa o buffer de entrada após o nextInt()
        entradaDados.nextLine();

        // Imprime um cabeçalho informando qual tabuada será exibida
        System.out.println("Imprimindo a tabuada do número: " + numero);

        // Imprime a tabuada do número digitado, de 0 até 10
        for (int i = 0; i <= 10; i++) {
            System.out.println(i + " x " + numero + " = " + (i * numero));
        }

        // Fecha o Scanner para liberar o recurso de entrada
        entradaDados.close();
    }
}

```
# 2 — Cálculo do seu IMC

```java
import java.text.DecimalFormat;
import java.util.Scanner;

/**
 * Escreva um código onde o usuário entra com sua altura e peso,
 * seja feito o cálculo do seu IMC (IMC = peso / (altura * altura))
 * e seja exibida a mensagem de acordo com o resultado:
 *
 * Se for menor ou igual a 18,5 → "Abaixo do peso";
 * Se for entre 18,6 e 24,9 → "Peso ideal";
 * Se for entre 25,0 e 29,9 → "Levemente acima do peso";
 * Se for entre 30,0 e 34,9 → "Obesidade Grau I";
 * Se for entre 35,0 e 39,9 → "Obesidade Grau II (Severa)";
 * Se for maior ou igual a 40,0 → "Obesidade Grau III (Mórbida)".
 *
 * <p>Este programa utiliza a classe {@link Scanner} para leitura de dados
 * via teclado e a classe {@link DecimalFormat} para formatar números
 * com duas casas decimais.</p>
 *
 * author Marcelo Guimarães Carvalho
 * version 1.0
 * since 2025-01-28
 */
public class Main {

    /**
     * Método principal da aplicação.
     *
     * @param args argumentos de linha de comando (não utilizados neste programa)
     */
    public static void main(String[] args) {

        // Cria um objeto Scanner para ler dados digitados pelo usuário
        Scanner entradaDados = new Scanner(System.in);

        // Variáveis para armazenar nome, altura, peso e IMC
        String nome;
        double altura;
        double peso;
        double imc;

        // Formata números com duas casas decimais
        DecimalFormat numeroDecimalFormatado = new DecimalFormat("#,##0.00");

        // Pergunta o nome do usuário
        System.out.print("Qual o seu nome? ");
        nome = entradaDados.nextLine();

        // Pergunta o peso do usuário
        System.out.print("Qual o seu peso em quilos? ");
        peso = entradaDados.nextDouble();
        entradaDados.nextLine(); // limpa o buffer

        // Pergunta a altura do usuário
        System.out.print("Qual a sua altura em metros? ");
        altura = entradaDados.nextDouble();
        entradaDados.nextLine(); // limpa o buffer

        // Cálculo do IMC
        imc = peso / (altura * altura);

        // Exibe o IMC formatado
        System.out.printf("%s, seu IMC é: %s. Você está ",
                nome, numeroDecimalFormatado.format(imc));

        // Classificação do IMC
        if (imc <= 18.5) {
            System.out.println("abaixo do peso.");

        } else if (imc <= 24.9) {
            System.out.println("com peso ideal.");

        } else if (imc <= 29.9) {
            System.out.println("levemente acima do peso.");

        } else if (imc <= 34.9) {
            System.out.println("com Obesidade Grau I.");

        } else if (imc <= 39.9) {
            System.out.println("com Obesidade Grau II (Severa).");

        } else {
            System.out.println("com Obesidade Grau III (Mórbida).");
        }

        // Fecha o Scanner
        entradaDados.close();
    }
}

```
# 3 — Par ou Impar

```java

```
# 4 — Divide = Zero

```java

```



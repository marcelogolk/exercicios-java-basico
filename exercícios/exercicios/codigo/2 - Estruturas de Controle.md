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
# 1 — Cálculo do seu IMC

```java

```



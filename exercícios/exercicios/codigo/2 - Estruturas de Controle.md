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
 * e seja gerada a tabuada de 1 até 10 desse número;
 *
 * <p>Este programa utiliza a classe {@link Scanner} para leitura de dados
 * via teclado e a classe {@link LocalDate} para obter o ano atual do sistema.</p>
 *
 * @author Marcelo Guimarães Carvalho
 * @version 1.0
 * @since 2025-01-28
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

        // Declara uma variável do tipo String para armazenar o nome do usuário
        String nome;

        // Declara uma variável do tipo int para armazenar o ano de nascimento
        int numero;


        // Exibe a pergunta ao usuário sem pular de linha
        System.out.print("Quer a tabuada de qual numero ");

        // Lê a linha um numero inteiro digitado pelo usuário
        numero = entradaDados.nextInt();
        
        // limpa o  buffer de entrada
        entradaDados.nextLine();
        
        // imprime um cabecalho
        System.out.print("Imprimindo a Tabuada do numero: "+ numero);
        
        // impprimindo a tabuada do numero digitado
        for (int i = 0; i<=10; i++){
            System.out.println(i + " x " + numero + " = " + (i*numero));
        }

        // Fecha o Scanner para liberar o recurso de entrada
        entradaDados.close();
    }
}
```
# 1 — Cálculo do seu IMC

```java

```



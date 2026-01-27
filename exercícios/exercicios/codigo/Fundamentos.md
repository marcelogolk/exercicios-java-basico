# 1 Cálculo de Idade  
```java
import java.time.LocalDate;
import java.util.Scanner;
/**
 * Escreve um programa que recebe o nome e o ano de nascimento de alguém
 * e imprime na tela a seguinte mensagem:
 * "Olá 'Fulano' você tem, ou faz 'X' anos este ano."
 *
 * <p>Este programa utiliza a classe {@link Scanner} para leitura de dados
 * via teclado e a classe {@link LocalDate} para obter o ano atual do sistema.</p>
 *
 * @author Marcelo Guimarães Carvalho
 * @version 1.0
 * @since 2025-01-27
 */
public class Main {
    /**
     * Método principal da aplicação.
     * @param args argumentos de linha de comando (não utilizados neste programa)
     */
    public static void main(String[] args) {
        Scanner entradaDados = new Scanner(System.in); // Cria um objeto Scanner para ler dados
                                                       // digitados pelo usuário
        String nome;         // Variável para armazenar o nome do usuário
        int anoNascimetno;   // Variável para armazenar o ano de nascimento
        int anoAtual;        // Obtém o ano atual do sistema
        int idade;           // Variável para armazenar a idade calculada
        anoAtual = LocalDate.now().getYear();  // Pega o ano atual na data do sistema e atribui
                                               // a vaviável "anoAtual"
        System.out.print("Qual o seu nome? "); // Pergunta o nome do usuário
        nome = entradaDados.nextLine(); // Lê a linha inteira digitada pelo usuário
                                        // e atribui a variável "nome
        System.out.print("Você nasceu em que ano(XXXX)? "); // Pergunta o ano de nascimento
        anoNascimetno = entradaDados.nextInt(); // Lê um número inteiro digitada pelo usuário
                                                // e atribui a variável "anoNascimento"
        idade = anoAtual - anoNascimetno; // Calcula a idade
        System.out.printf("Olá %s, você tem, ou faz %d anos este ano.%n", nome, idade); // Exibe a mensagem
        entradaDados.close(); // Fecha o Scanner
    }
}

🧮 Programa em Java: Cálculo de Idade
Autor: Marcelo Guimarães Carvalho

Este documento apresenta um programa simples em Java que:

Lê o nome completo do usuário

Lê o ano de nascimento

Calcula a idade com base no ano atual

Exibe uma mensagem formatada com o resultado

O código está documentado com Javadoc e inclui comentários explicativos.

📌 Código Completo (com Javadoc e comentários)
java
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
     *
     * @param args argumentos de linha de comando (não utilizados neste programa)
     */
    public static void main(String[] args) {

        // Cria um objeto Scanner para ler dados digitados pelo usuário
        Scanner entradaDados = new Scanner(System.in);

        // Variável para armazenar o nome do usuário
        String nome;

        // Variável para armazenar o ano de nascimento
        int anoNascimetno;

        // Obtém o ano atual do sistema
        int anoAtual = LocalDate.now().getYear();

        // Variável para armazenar a idade calculada
        int idade;

        // Pergunta o nome do usuário
        System.out.print("Qual o seu nome? ");
        nome = entradaDados.nextLine(); // Lê a linha inteira

        // Pergunta o ano de nascimento
        System.out.print("Você nasceu em que ano(XXXX)? ");
        anoNascimetno = entradaDados.nextInt(); // Lê um número inteiro

        // Calcula a idade
        idade = anoAtual - anoNascimetno;

        // Exibe a mensagem formatada
        System.out.printf("Olá %s, você tem, ou faz %d anos este ano.%n", nome, idade);

        // Fecha o Scanner
        entradaDados.close();
    }
}
📝 Explicação Linha a Linha
Importações
import java.time.LocalDate;  
Permite acessar a data atual do sistema.

import java.util.Scanner;  
Permite ler dados digitados pelo usuário.

Javadoc da classe
Explica o propósito do programa e inclui tags importantes como:

@author

@version

@since

Método main
Cria o Scanner para entrada de dados.

Declara variáveis para nome, ano de nascimento, ano atual e idade.

Lê o nome completo usando nextLine().

Lê o ano de nascimento usando nextInt().

Calcula a idade subtraindo o ano de nascimento do ano atual.

Exibe a mensagem formatada com printf().

Fecha o Scanner.

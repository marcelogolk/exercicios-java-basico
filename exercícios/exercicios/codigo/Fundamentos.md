# 📘 Exercícios em Java  
Autor: **Marcelo Guimarães Carvalho**  
Data: **27/01/2025**

Este repositório contém dois programas simples em Java:

1. **Cálculo de Idade**  
2. **Cálculo da Área de um Quadrado**

Cada código está documentado com Javadoc e comentários explicativos.

---

# Cálculo de Idade

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
     *
     * @param args argumentos de linha de comando (não utilizados neste programa)
     */
    public static void main(String[] args) {

        // Cria um objeto Scanner para ler dados digitados pelo usuário no console
        Scanner entradaDados = new Scanner(System.in);

        // Declara uma variável do tipo String para armazenar o nome do usuário
        String nome;

        // Declara uma variável do tipo int para armazenar o ano de nascimento
        int anoNascimetno;

        // Obtém o ano atual do sistema usando a API de datas do Java
        int anoAtual = LocalDate.now().getYear();

        // Declara uma variável do tipo int para armazenar a idade calculada
        int idade;

        // Exibe a pergunta ao usuário sem pular de linha
        System.out.print("Qual o seu nome? ");

        // Lê a linha inteira digitada pelo usuário (pode conter espaços)
        nome = entradaDados.nextLine();

        // Pergunta o ano de nascimento do usuário
        System.out.print("Você nasceu em que ano(XXXX)? ");

        // Lê um número inteiro digitado pelo usuário e guarda em anoNascimetno
        anoNascimetno = entradaDados.nextInt();

        // Calcula a idade subtraindo o ano de nascimento do ano atual
        idade = anoAtual - anoNascimetno;

        // Imprime a mensagem formatada com o nome e a idade calculada
        System.out.printf("Olá %s, você tem, ou faz %d anos este ano.%n", nome, idade);

        // Fecha o Scanner para liberar o recurso de entrada
        entradaDados.close();
    }
}
```
# Cálculo da Área de um Quadrado   
**Autor:** Marcelo Guimarães Carvalho  

```java
import java.text.DecimalFormat;
import java.util.Scanner;

/**
 * Escreva um código que receba o tamanho do lado de um quadrado,
 * calcule sua área e exiba na tela
 * fórmula: área = lado x lado
 *
 * <p>Este programa utiliza a classe {@link Scanner} para leitura de dados
 * via teclado e a classe {@link DecimalFormat} para formatar a saída numérica
 * com duas casas decimais no padrão brasileiro (vírgula como separador decimal).</p>
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

        // Cria um objeto Scanner para ler dados digitados pelo usuário no console
        Scanner entradaDados = new Scanner(System.in);

        // Cria um objeto DecimalFormat para formatar números com duas casas decimais
        // e separador decimal no padrão brasileiro (ex.: 1,50)
        DecimalFormat numeroDecimalFormatado = new DecimalFormat("#,##0.00");

        // Variável para armazenar o lado do quadrado
        double lado = 0;

        // Variável para armazenar a área do quadrado
        double area = 0;

        // Pergunta ao usuário o tamanho do lado do quadrado
        System.out.print("Qual o tamanho do lado do quadrado? ");

        // Lê um número digitado pelo usuário e atribui à variável "lado"
        lado = entradaDados.nextDouble();

        // Calcula a área do quadrado usando a fórmula: área = lado x lado
        area = lado * lado;

        // Exibe a mensagem formatada, usando df.format() para mostrar os números
        // com duas casas decimais e vírgula como separador decimal
        System.out.printf(
                "Olá! o quadrado de lado %s possui área de %s.%n",
                numeroDecimalFormatado.format(lado),
                numeroDecimalFormatado.format(area)
        );

        // Fecha o Scanner para liberar o recurso de entrada
        entradaDados.close();
    }
}


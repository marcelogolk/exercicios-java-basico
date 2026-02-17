# 📘 Exercícios

1. **Conta Bancaria**
2. **Controla Carro**
3. **Petshop**

Cada código está documentado com Javadoc e comentários explicativos.

---

# 1 — Conta Bancaria

Este projeto implementa o controle das funcionalidades básicas de uma conta Bancario, seguindo todas as regras e operações definidas no enunciado abaixo.

## Descrição do Problema

Escreva um código onde temos uma conta bancaria que possa realizar as seguintes operações:
- Consultar saldo
- Consultar cheque especial
- Depositar dinheiro;
- Sacar dinheiro;
- Pagar um boleto.
- Verificar se a conta está usando cheque especial.

Siga as seguintes regras para implementar
-	- A conta bancária deve ter um limite de cheque especial somado ao saldo da conta;
-	- O o valor do cheque especial é definido no momento da criação da conta, de acordo com o valor depositado na conta em sua criação;
-	- Se o valor depositado na criação da conta for de R$500,00 ou menos o cheque especial deve ser de R$50,00
-	- Para valores acima de R$500,00 o cheque especial deve ser de 50% do valor depositado;
-	- Caso o limite de cheque especial seja usado, assim que possível a conta deve cobrar uma taxa de 20% do valor usado do cheque especial.
	
---
🧩 Classes do Projeto
A seguir estão as classes que compõem o sistema de controle do carro.
Elas estão organizadas na ordem ideal de leitura:

---
```java

```

---
# 2 — Controla Carro
Este projeto implementa o controle das funcionalidades básicas de um carro, seguindo todas as regras e operações definidas no enunciado abaixo.

## 🚗 Descrição do Problema

Escreva um código onde controlamos as funções de um carro, ele deve ter as seguintes funções:
- Ligar o carro;
- Desligar o carro;
- Acelerar;
- Diminuir velocidade;
- Virar para esquerda/direita
- Verificar velocidade;
- Trocar a marcha

Siga as seguintes regras na implementação
-  Quando o carro for criado ele deve começar desligado, em ponto morto e com sua velocidade em 0
-  O carro desligado não pode realizar nenhuma função;
-  Quando o carro for acelerado ele deve incrementar 1km em sua velocidade (pode chegar no máximo a 120km);
-  Quando diminuir a velocidade do carro ele deve decrementar 1 km de sua velocidade (pode chegar no minimo a 0km);
-  O carro deve possuir 6 marchas, não deve ser permitido pular uma marcha no carro;
-  A velocidade do carro deve respeitar os seguintes limites para cada marcha
	-  Se o carro estiver na marcha 0 (ponto morto) ele não pode acelerar
	-   Se estiver na 1ª marcha sua velocidade pode estar entre 0km e 20km
    -  Se estiver na 2ª marcha sua velocidade pode estar entre 21km e 40km
    -  Se estiver na 3ª marcha sua velocidade pode estar entre 41km e 60km
    -  Se estiver na 4ª marcha sua velocidade pode estar entre 61km e 80km
    -  Se estiver na 5ª marcha sua velocidade pode estar entre 81km e 100km
    -  Se estiver na 6ª marcha sua velocidade pode estar entre 101km e 120km
-  O carro podera ser desligado se estiver em ponto morto (marcha 0) e sua velocidade em 0 km
-  O carro só pode virar para esquerda/direita se sua velocidade for de no mínimi 1km e no máximo 40km;
-  Se o carro estiver desligado, não troca marcha.

---

🧩 Classes do Projeto
A seguir estão as classes que compõem o sistema de controle do carro.
Elas estão organizadas na ordem ideal de leitura:

Enums — definem os tipos fundamentais usados pelo carro (marcha, direção e estado).

Classe Carro — implementa toda a lógica e regras de funcionamento.

Classe Main — contém o menu interativo que permite ao usuário operar o carro.

Cada Classe e Enum deve ser colocado em um arquivo separado.

---

🧭 Enums do Projeto

```java
/**
 * Representa as marchas disponíveis no carro.
 */
public enum Marcha {
    PONTO_MORTO,
    PRIMEIRA,
    SEGUNDA,
    TERCEIRA,
    QUARTA,
    QUINTA,
    SEXTA
}

/**
 * Representa o estado do carro: ligado ou desligado.
 */
public enum StatusCarro {
    LIGADO,
    DESLIGADO
}

/**
 * Representa as direções possíveis ao virar o carro.
 */
public enum Direcao {
    ESQUERDA,
    DIREITA
}
```

---

🚗 Classe Carro

```java
/**
 * Classe que representa um carro com funcionalidades básicas como ligar,
 * desligar, acelerar, frear, virar e trocar marchas.
 *
 * Todas as regras do enunciado foram implementadas.
 */
public class Carro {

    /** Velocidade mínima permitida (0 km/h). */
    private static final int VELOCIDADE_MIN = 0;

    /** Velocidade máxima permitida (120 km/h). */
    private static final int VELOCIDADE_MAX = 120;

    private StatusCarro status;
    private Marcha marcha;
    private int velocidade;

    /**
     * Construtor: inicia o carro desligado, em ponto morto e velocidade zero.
     */
    public Carro() {
        this.status = StatusCarro.DESLIGADO;
        this.velocidade = VELOCIDADE_MIN;
        this.marcha = Marcha.PONTO_MORTO;
    }

    // Getters e setters privados para proteger o estado interno
    public StatusCarro getStatus() { return status; }
    private void setStatus(StatusCarro status) { this.status = status; }

    public int getVelocidade() { return velocidade; }
    private void setVelocidade(int velocidade) { this.velocidade = velocidade; }

    public Marcha getMarcha() { return marcha; }
    private void setMarcha(Marcha marcha) { this.marcha = marcha; }

    // ============================================================
    // LIGAR / DESLIGAR
    // ============================================================

    /**
     * Liga o carro, caso já não esteja ligado.
     */
    public void ligar() {
        if (this.getStatus() == StatusCarro.LIGADO) {
            System.out.println("O carro já está ligado.");
            return;
        }
        this.setStatus(StatusCarro.LIGADO);
        System.out.println("Ligando carro...");
    }

    /**
     * Desliga o carro somente se estiver parado e em ponto morto.
     */
    public void desligar() {
        if (this.getStatus() == StatusCarro.DESLIGADO) {
            System.out.println("O carro já está desligado.");
            return;
        }
        if (this.getVelocidade() != VELOCIDADE_MIN) {
            System.out.printf("O carro está a %d km/h. Só pode ser desligado parado.%n", this.getVelocidade());
            return;
        }
        if (this.getMarcha() != Marcha.PONTO_MORTO) {
            System.out.printf("O carro está na marcha %s. Só pode ser desligado em ponto morto.%n", this.getMarcha());
            return;
        }
        this.setStatus(StatusCarro.DESLIGADO);
        System.out.println("Desligando carro...");
    }

    // ============================================================
    // MARCHAS
    // ============================================================

    /**
     * Retorna a marcha imediatamente anterior à atual.
     */
    private Marcha verificaMarchaAnterior() {
        return switch (this.marcha) {
            case PRIMEIRA -> Marcha.PONTO_MORTO;
            case SEGUNDA -> Marcha.PRIMEIRA;
            case TERCEIRA -> Marcha.SEGUNDA;
            case QUARTA -> Marcha.TERCEIRA;
            case QUINTA -> Marcha.QUARTA;
            case SEXTA -> Marcha.QUINTA;
            default -> null;
        };
    }

    /**
     * Retorna a marcha imediatamente posterior à atual.
     */
    private Marcha verificaMarchaPosterior() {
        return switch (this.marcha) {
            case PONTO_MORTO -> Marcha.PRIMEIRA;
            case PRIMEIRA -> Marcha.SEGUNDA;
            case SEGUNDA -> Marcha.TERCEIRA;
            case TERCEIRA -> Marcha.QUARTA;
            case QUARTA -> Marcha.QUINTA;
            case QUINTA -> Marcha.SEXTA;
            default -> null;
        };
    }

    /**
     * Troca a marcha do carro, respeitando:
     * - Não pode pular marchas.
     * - Não pode trocar desligado.
     * - Velocidade deve estar dentro do limite da marcha desejada.
     *
     * DECISÃO DE IMPLEMENTAÇÃO:
     * O enunciado é ambíguo quanto ao limite de velocidade por marcha.
     * Aqui adotamos a interpretação mais comum em exercícios:
     * Os limites servem APENAS para validar a troca de marcha.
     * A aceleração não é limitada pela marcha atual.
     */
    public void trocarMarcha(Marcha novaMarcha){
        if (this.getStatus() == StatusCarro.DESLIGADO){
            System.out.println("Não é possível trocar marcha com o carro desligado.");
            return;
        }

        if (novaMarcha != verificaMarchaAnterior() && novaMarcha != verificaMarchaPosterior()){
            System.out.println("Não é permitido pular marchas.");
            return;
        }

        if (!podeTrocarMarcha(novaMarcha, this.getVelocidade())) {
            System.out.println("Velocidade incompatível com a marcha desejada.");
            return;
        }

        this.setMarcha(novaMarcha);
        System.out.printf("Marcha trocada para %s.%n", novaMarcha);
    }

    /**
     * Verifica se a velocidade atual permite trocar para a marcha desejada.
     */
    private boolean podeTrocarMarcha(Marcha novaMarcha, int velocidade) {
        int limite = limiteVelocidadeDaMarcha(novaMarcha);
        return velocidade <= limite;
    }

    /**
     * Retorna o limite máximo de velocidade permitido para cada marcha.
     */
    private int limiteVelocidadeDaMarcha(Marcha marcha) {
        return switch (marcha) {
            case PONTO_MORTO -> VELOCIDADE_MIN;
            case PRIMEIRA -> 20;
            case SEGUNDA -> 30;
            case TERCEIRA -> 40;
            case QUARTA -> 60;
            case QUINTA -> 80;
            case SEXTA -> VELOCIDADE_MAX;
        };
    }

    // ============================================================
    // ACELERAR / FREAR
    // ============================================================

    /**
     * Acelera o carro em 1 km/h, respeitando:
     * - Não acelerar desligado
     * - Não acelerar em ponto morto
     * - Não ultrapassar 120 km/h
     */
    public void acelerar() {
        if (this.getStatus() == StatusCarro.DESLIGADO){
            System.out.println("Não é possível acelerar com o carro desligado.");
            return;
        }
        if (this.getVelocidade() == VELOCIDADE_MAX){
            System.out.println("O carro já está na velocidade máxima.");
            return;
        }
        if (this.getMarcha() == Marcha.PONTO_MORTO){
            System.out.println("Não é possível acelerar em ponto morto.");
            return;
        }

        this.setVelocidade(this.getVelocidade() + 1);
        System.out.printf("Velocidade atual: %d km/h%n", this.getVelocidade());
    }

    /**
     * Diminui a velocidade em 1 km/h, respeitando o limite mínimo.
     */
    public void frear() {
        if (this.getVelocidade() == VELOCIDADE_MIN){
            System.out.println("O carro já está parado.");
            return;
        }
        this.setVelocidade(this.getVelocidade() - 1);
        System.out.printf("Velocidade atual: %d km/h%n", this.getVelocidade());
    }

    // ============================================================
    // VIRAR
    // ============================================================

    /**
     * Vira o carro para a direção desejada, respeitando:
     * - Não virar desligado
     * - Velocidade entre 1 e 40 km/h
     * - Não virar em ponto morto
     */
    public void virar(Direcao direcao){
        if (this.getStatus() == StatusCarro.DESLIGADO){
            System.out.println("Não é possível virar com o carro desligado.");
            return;
        }
        if (this.getVelocidade() < 1) {
            System.out.println("O carro precisa estar em movimento para virar.");
            return;
        }
        if (this.getVelocidade() > 40) {
            System.out.printf("Velocidade atual: %d km/h. Para virar, reduza para no máximo 40 km/h.%n",
                    this.getVelocidade());
            return;
        }
        if (this.getMarcha() == Marcha.PONTO_MORTO) {
            System.out.println("Não é possível virar em ponto morto.");
            return;
        }

        switch (direcao){
            case ESQUERDA -> System.out.println("Virando à esquerda...");
            case DIREITA -> System.out.println("Virando à direita...");
        }
    }

    // ============================================================
    // PAINEL
    // ============================================================

    /**
     * Exibe no console o estado atual do carro.
     */
    public void mostrarPainel() {
        System.out.println("========== PAINEL DO CARRO ==========");
        System.out.printf("Status:      %s%n", this.getStatus());
        System.out.printf("Marcha:      %s%n", this.getMarcha());
        System.out.printf("Velocidade:  %d km/h%n", this.getVelocidade());
        System.out.println("======================================");
    }
}
```

---

⚙️ Classe Main
```java
/**
 * Escreva um código onde controlamos as funções de um carro, ele deve ter as seguintes funções:
 * - Ligar o carro;
 * - Desligar o carro;
 * - Acelerar;
 * - Diminuir velocidade;
 * - Virar para esquerda/direita;
 * - Verificar velocidade;
 * - Trocar a marcha.
 *
 * Regras:
 * - Quando o carro for criado ele deve começar desligado, em ponto morto e com sua velocidade em 0.
 * - O carro desligado não pode realizar nenhuma função.
 * - Quando o carro for acelerado ele deve incrementar 1km/h (máximo 120km/h).
 * - Quando diminuir a velocidade deve decrementar 1km/h (mínimo 0km/h).
 * - O carro deve possuir 6 marchas e não deve ser permitido pular marchas.
 * - A velocidade deve respeitar os limites de troca de marcha:
 *      Ponto morto: não acelera
 *      1ª marcha: 0–20 km/h
 *      2ª marcha: 21–40 km/h
 *      3ª marcha: 41–60 km/h
 *      4ª marcha: 61–80 km/h
 *      5ª marcha: 81–100 km/h
 *      6ª marcha: 101–120 km/h
 * - O carro só pode ser desligado se estiver em ponto morto e velocidade 0.
 * - O carro só pode virar se estiver entre 1 e 40 km/h.
 * - Se o carro estiver desligado, não troca marcha.
 *
 * Classe Main
 *
 * Esta classe cont&eacute;m o menu interativo que permite ao usu&aacute;rio controlar
 * todas as fun&ccedil;&otilde;es do carro. O programa permanece em execu&ccedil;&atilde;o at&eacute; que
 * o usu&aacute;rio escolha a op&ccedil;&atilde;o de sair.
 */

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        // Scanner responsável por ler as entradas do usuário
        Scanner entrada = new Scanner(System.in);

        // Instância do carro que será controlado pelo menu
        Carro carro = new Carro();

        int opcao; // Armazena a opção escolhida pelo usuário

        // Loop principal do menu — continua até o usuário escolher 0 (sair)
        do {
            System.out.println("\n=========== MENU DO CARRO ===========");
            System.out.println("1 - Ligar carro");
            System.out.println("2 - Desligar carro");
            System.out.println("3 - Acelerar");
            System.out.println("4 - Frear");
            System.out.println("5 - Trocar marcha");
            System.out.println("6 - Virar");
            System.out.println("7 - Mostrar painel");
            System.out.println("0 - Sair");
            System.out.println("=====================================");
            System.out.print("Escolha uma opção: ");

            // Lê a opção digitada pelo usuário
            opcao = entrada.nextInt();

            // Executa a ação correspondente à opção escolhida
            switch (opcao) {
                case 1:
                    ligarCarro(carro);
                    break;

                case 2:
                    desligarCarro(carro);
                    break;

                case 3:
                    acelerarCarro(carro);
                    break;

                case 4:
                    frearCarro(carro);
                    break;

                case 5:
                    trocarMarcha(entrada, carro);
                    break;

                case 6:
                    virarCarro(entrada, carro);
                    break;

                case 7:
                    mostrarPainelCarro(carro);
                    break;

                case 0:
                    encerrarApp();
                    break;

                default:
                    System.out.println("Opção inválida.");
            }

        } while (opcao != 0); // Condição de saída do menu

        // Fecha o scanner ao final da execução
        entrada.close();
    }

    /**
     * Exibe mensagem de encerramento da aplicação.
     */
    private static void encerrarApp() {
        System.out.println("Encerrando aplicação...");
    }

    /**
     * Chama o método do carro que exibe o painel com status, marcha e velocidade.
     */
    private static void mostrarPainelCarro(Carro carro) {
        carro.mostrarPainel();
    }

    /**
     * Solicita ao usuário a direção desejada e chama o método virar() do carro.
     */
    private static void virarCarro(Scanner entrada, Carro carro) {
        System.out.println("Escolha a direção:");
        System.out.println("1 - Esquerda");
        System.out.println("2 - Direita");
        System.out.print("Direção: ");

        int d = entrada.nextInt();

        // Converte a escolha numérica para o enum correspondente
        if (d == 1) {
            carro.virar(Direcao.ESQUERDA);
        } else if (d == 2) {
            carro.virar(Direcao.DIREITA);
        } else {
            System.out.println("Direção inválida.");
        }
    }

    /**
     * Solicita ao usuário a marcha desejada e chama o método trocarMarcha().
     */
    private static void trocarMarcha(Scanner entrada, Carro carro) {
        System.out.println("Escolha a marcha:");
        System.out.println("0 - Ponto Morto");
        System.out.println("1 - Primeira");
        System.out.println("2 - Segunda");
        System.out.println("3 - Terceira");
        System.out.println("4 - Quarta");
        System.out.println("5 - Quinta");
        System.out.println("6 - Sexta");
        System.out.print("Marcha: ");

        int m = entrada.nextInt();

        // Verifica se a marcha digitada é válida
        if (m >= 0 && m <= 6) {
            carro.trocarMarcha(Marcha.values()[m]);
        } else {
            System.out.println("Marcha inválida.");
        }
    }

    /**
     * Chama o método frear() do carro.
     */
    private static void frearCarro(Carro carro) {
        carro.frear();
    }

    /**
     * Chama o método acelerar() do carro.
     */
    private static void acelerarCarro(Carro carro) {
        carro.acelerar();
    }

    /**
     * Chama o método desligar() do carro.
     */
    private static void desligarCarro(Carro carro) {
        carro.desligar();
    }

    /**
     * Chama o método ligar() do carro.
     */
    private static void ligarCarro(Carro carro) {
        carro.ligar();
    }
}

```
---

# 3 — Petshop

Este projeto implementa o controle de uma máquina de banho de um petshop, seguindo todas as regras e operações definidas no enunciado abaixo.

---

## 🐶 Descrição do Problema

Escreva um código onde temos o controle de banho de um petshop, a máquina de banhos dos pets deve ter as seguintes operações:

- Dar banho no pet  
- Abastecer com água  
- Abastecer com shampoo  
- Verificar nível de água  
- Verificar nível de shampoo  
- Verificar se tem pet no banho  
- Colocar pet na máquina  
- Retirar pet da máquina  
- Limpar máquina  

### Regras de Implementação

- A máquina de banho deve permitir somente **1 pet por vez**  
- Cada banho realizado irá consumir **10 litros de água** e **2 litros de shampoo**  
- A máquina tem capacidade máxima de **30 litros de água** e **10 litros de shampoo**  
- Se o pet for retirado da máquina **sem estar limpo**, será necessário **limpar a máquina** para permitir a entrada de outro pet  
- A limpeza da máquina irá consumir **3 litros de água** e **1 litro de shampoo**  
- O abastecimento de água e shampoo deve permitir **2 litros por vez** que for acionado  

---

# 🧩 Classes do Projeto

A seguir estão as três classes que compõem o sistema.

---

# 🐾 Classe `Pet`

```java
package PetShop;

/**
 * Representa um Pet que será colocado na máquina de banho.
 * Cada pet possui um nome e um estado de limpeza.
 *
 * - O nome é definido no momento da criação e não pode ser alterado.
 * - O estado de limpeza começa como "sujo" (clean = false).
 *
 * author Marcelo Guimarães Carvalho
 * version 1.0
 * since 2025-01-28
 */
public class Pet {

    /** Nome do pet. É final porque não muda após a criação. */
    private final String nome;

    /** Indica se o pet está limpo (true) ou sujo (false). */
    private boolean clean;

    /**
     * Construtor da classe Pet.
     * Ao criar um pet, ele sempre começa sujo.
     *
     * @param nome Nome do pet informado pelo usuário.
     */
    public Pet(String nome) {
        this.nome = nome;
        this.clean = false; // Todo pet entra na máquina sujo.
    }

    /**
     * Retorna o nome do pet.
     *
     * @return nome do pet.
     */
    public String getNome() {
        return nome;
    }

    /**
     * Informa se o pet está limpo.
     *
     * @return true se estiver limpo, false se estiver sujo.
     */
    public boolean isClean() {
        return clean;
    }

    /**
     * Define o estado de limpeza do pet.
     * Usado pela máquina após o banho.
     *
     * @param clean true para limpo, false para sujo.
     */
    public void setClean(boolean clean) {
        this.clean = clean;
    }
}
```
---

# 🛁 Classe `PetMachine`
```java
package PetShop;

/**
 * Representa a máquina de banho do petshop.
 *
 * A máquina possui:
 * - Um estado de limpeza (limpa ou suja)
 * - Um nível de água (máx. 30 litros)
 * - Um nível de shampoo (máx. 10 litros)
 * - Um pet que pode estar dentro da máquina (apenas 1 por vez)
 *
 * Regras principais:
 * - Cada banho consome 10 litros de água e 2 litros de shampoo.
 * - A limpeza da máquina consome 3 litros de água e 1 litro de shampoo.
 * - Só é possível colocar um pet se a máquina estiver limpa.
 * - Se o pet sair sujo, a máquina fica suja.
 * - Abastecimento sempre adiciona 2 litros por vez.
 *
 * author Marcelo Guimarães Carvalho
 * version 1.0
 * since 2025-01-28
 */
public class PetMachine {

    /** Indica se a máquina está limpa (true) ou suja (false). */
    private boolean clean = true;

    /** Quantidade atual de água na máquina (máximo 30 litros). */
    private int water = 30;

    /** Quantidade atual de shampoo na máquina (máximo 10 litros). */
    private int shampoo = 10;

    /** Pet atualmente dentro da máquina (ou null se estiver vazia). */
    private Pet pet = null;

    public int getShampoo() {
        return shampoo;
    }

    /**
     * Realiza o banho do pet.
     * Consome 10 litros de água e 2 litros de shampoo.
     * Marca o pet como limpo.
     */
    public void takeAShower() {
        if (this.pet == null) {
            System.out.println("Coloque o Pet na máquina para iniciar o banho");
            return;
        }
        this.water -= 10;
        this.shampoo -= 2;
        this.pet.setClean(true);
        System.out.printf("O pet %s está limpo.%n", this.pet.getNome());
    }

    /** Adiciona 2 litros de água, respeitando o limite máximo. */
    public void addWater() {
        if (this.water == 30) {
            System.out.println("A Capacidade de água da máquina está no máximo");
            return;
        }
        this.water += 2;
    }

    /** Adiciona 2 litros de shampoo, respeitando o limite máximo. */
    public void addShampoo() {
        if (this.shampoo == 10) {
            System.out.println("A Capacidade de shampo da máquina está no máximo");
            return;
        }
        this.shampoo += 2;
    }

    public int getWater() {
        return water;
    }

    public Pet getPet() {
        return pet;
    }

    public boolean hasPet() {
        return this.pet != null;
    }

    /**
     * Coloca um pet na máquina, desde que:
     * - A máquina esteja limpa
     * - Não haja outro pet dentro
     */
    public void setPet(Pet pet) {
        if (!this.clean) {
            System.out.println("A máquina está suja. para colocar o Pet é necessário limpá-la %n");
            return;
        }
        if (this.hasPet()) {
            System.out.printf("O Pet %s está na máquina neste momento %n", this.pet.getNome());
            return;
        }
        this.pet = pet;
    }

    /**
     * Remove o pet da máquina.
     * Se o pet estiver sujo → máquina fica suja.
     * Se estiver limpo → máquina permanece limpa.
     */
    public void removePet() {
        this.clean = this.pet.isClean();
        if (this.clean)
            System.out.printf("O pet %s está limpo %n", this.pet.getNome());
        else
            System.out.printf("O pet %s não está limpo %n", this.pet.getNome());
        this.pet = null;
    }

    /**
     * Limpa a máquina.
     * Consome 3 litros de água e 1 litro de shampoo.
     */
    public void wash() {
        this.water -= 3;
        this.shampoo -= 1;
        this.clean = true;
        System.out.println("A máquina foi limpa");
    }
}
```
---

# 🖥️ Classe `Main`

```java
package PetShop;

import java.util.Scanner;

/**
 * Sistema de controle da máquina de banho de um petshop.
 * Exibe um menu interativo para o usuário realizar operações.
 */
public class Main {

    static final Scanner entradaDados = new Scanner(System.in);
    private static PetMachine petMachine = new PetMachine();

    public static void main(String[] args) {
        int option = -1;

        do {
            System.out.println("=== Escolha uma das opções: ===");
            System.out.println("1 - Dar banho no Pet");
            System.out.println("2 - Abastecer a máquina com água");
            System.out.println("3 - Abastecer a máquina com shampoo");
            System.out.println("4 - Verificar água na máquina");
            System.out.println("5 - Verificar shampoo na máquina");
            System.out.println("6 - Verificar se tem Pet no banho");
            System.out.println("7 - Colocar Pet na máquina");
            System.out.println("8 - Retirar Pet da máquina");
            System.out.println("9 - Limpar a máquina");
            System.out.println("0 - Sair");

            option = entradaDados.nextInt();

            switch (option) {
                case 1 -> showerPet();
                case 2 -> addWaterInMachine();
                case 3 -> addShampooInMachine();
                case 4 -> verifyWaterMachine();
                case 5 -> verifyShampooMachine();
                case 6 -> checkIfHasPatInMachine();
                case 7 -> setPetInMachine();
                case 8 -> removePet();
                case 9 -> whahMachine();
            }

        } while (option != 0);
    }

    private static void showerPet() {
        petMachine.takeAShower();
    }

    private static void addWaterInMachine() {
        System.out.println("Tentando colocar água na máquina...");
        petMachine.addWater();
    }

    private static void addShampooInMachine() {
        System.out.println("Tentando colocar shampoo na máquina...");
        petMachine.addShampoo();
    }

    private static void verifyWaterMachine() {
        System.out.printf("A máquina está no momento com %d litros de água.%n",
                petMachine.getWater());
    }

    private static void verifyShampooMachine() {
        System.out.printf("A máquina está no momento com %d litros de shampoo.%n",
                petMachine.getShampoo());
    }

    private static void checkIfHasPatInMachine() {
        System.out.println(
                petMachine.hasPet()
                        ? "O pet " + petMachine.getPet().getNome() + " está na máquina."
                        : "Não tem pet na máquina."
        );
    }

    public static void setPetInMachine() {
        if (petMachine.hasPet()) {
            System.out.printf("O Pet %s já está na máquina.%n",
                    petMachine.getPet().getNome());
            return;
        }

        String nome = "";
        while (nome == null || nome.isEmpty()) {
            System.out.print("Informe o nome do pet: ");
            nome = entradaDados.next();
        }

        Pet pet = new Pet(nome);
        petMachine.setPet(pet);

        if (petMachine.hasPet()) {
            System.out.printf("O Pet %s foi colocado na máquina.%n", pet.getNome());
        }
    }

    private static void removePet() {
        petMachine.removePet();
    }

    private static void whahMachine() {
        petMachine.wash();
    }
}
```

# 📘 Exercícios

1. **Conta Bancaria**
2. **Controla Carro**
3. **Petshop**

Cada código está documentado com Javadoc e comentários explicativos.

---

# 1 — Conta Bancaria

```java

```
# 2 — Controla Carro

```java

```
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

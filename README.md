# apresentacao-bim2-2024b-Akunozz

## Similaridade de objetos com operador "==" e método "equals()"

<h2> Operador == </h2>
Este operador compara as referências de memória, ou seja, verifica se os dois objetos ocupam o mesmo local na memória<br>
Útil para tipos primitivos ou para verificar referência de objetos.

<h2> Método equals() </h2>
Determina se dois objetos são logicamente iguais.<br>
É uma função que pode (e deve) ser sobrescrita para comparar o conteúdo de objetos personalizados.

<h3> Código de exemplo:</h3>

```
package exercicio;

public class Pessoa {
    private String nome;

    public Pessoa(String nome){
        this.nome = nome;
    }
}
```

```
package exercicio;

public class Principal {

    public static void main(String[] args){

        Pessoa pessoa1 = new Pessoa("Breno Rosa");
        Pessoa pessoa2 = new Pessoa("Breno Rosa");

        boolean comparacao = pessoa1 == pessoa2;

        System.out.println(comparacao);

    }
}

```

Saída do código:
```
false
```

Utilizando equals() : <br>
Sobrescrevemos o método equals() na nossa classe, comparando os valores do atributo nome.
```
package exercicio;

import java.util.Objects;

public class Pessoa {

    private String nome;

    public Pessoa(String nome){
        this.nome = nome;
    }

    @Override
    public boolean equals(Object o) {
        if (o == null || getClass() != o.getClass()) return false;
        Pessoa pessoa = (Pessoa) o;
        return Objects.equals(nome, pessoa.nome);
    }

    @Override
    public int hashCode() {
        return Objects.hashCode(nome);
    }
}
```

```
package exercicio;

public class Principal {

    public static void main(String[] args){

        Pessoa pessoa1 = new Pessoa("Breno Rosa");
        Pessoa pessoa2 = new Pessoa("Breno Rosa");

        boolean comparacao = pessoa1.equals(pessoa2);

        System.out.println(comparacao);

    }
}
```

Saída do código:
```
true
```

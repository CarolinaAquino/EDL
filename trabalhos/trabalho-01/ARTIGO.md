# Introdução
Smalltalk é uma linguagem única em vários aspectos. Ela foi uma das primeiras linguagens orientadas a objetos, e nenhuma linguagem orientada a objeto antes ou depois do Smalltalk leva o conceito tão longe.

# Origens e Influências
Smalltalk foi o produto da pesquisa conduzida por Alan Kay  no centro de pesquisa de Xerox Palo Alto (PARC). Alan, projetou a maioria das versões iniciais de Smalltalk, que Dan Ingalls implementou. A primeira versão, conhecida como Smalltalk-71, foi criada por Kay em algumas manhãs em uma aposta que uma linguagem de programação baseada na idéia de passagem de mensagens inspirada por Simula poderia ser implementada em "uma página de código".

Uma variante mais atrasada usada realmente para o trabalho de pesquisa ficou conhecida como Smalltalk-72. Sua sintaxe e modelo de execução eram muito diferentes das modernas variantes Smalltalk. Depois de revisões significativas que congelaram alguns aspectos da semântica de execução para ganhar desempenho (adotando um modelo de herança de classe semelhante a Simula como execução), o Smalltalk-76 foi criado. Este sistema tinha um ambiente de desenvolvimento com a maioria das ferramentas agora familiares, incluindo um navegador de código de biblioteca de classe / editor.  
Smalltalk-80 adicionou metaclasses, para ajudar a manter o paradigma de que "tudo é um objeto" associando propriedades e comportamento a classes individuais e até mesmo primitivos como valores inteiros e booleanos (por exemplo, para suportar diferentes formas de Criando instâncias). Essa foi a primeira versão da linguagem disponibilizada fora do PARC, primeiro como Smalltalk-80 Versão 1, dada a um pequeno número de empresas e universidades. Mais tarde (em 1983), uma implementação de disponibilidade geral, conhecida como Smalltalk-80 Versão 2, foi lançada como uma imagem (arquivo independente de plataforma com definições de objeto) e uma especificação de máquina virtual.

Smalltalk era uma das muitas linguagens de programação orientadas a objetos baseadas em Simula. É também uma das linguagens de programação mais influentes. Praticamente todas as linguagens orientadas a objetos que vieram depois - __Flavors, CLOS, Objective-C, Java, Python, Ruby e muitas outras__ - foram influenciadas por Smalltalk. O ambiente altamente produtivo fornecido pelas plataformas Smalltalk os tornou ideais para um desenvolvimento rápido e iterativo.

# Classificação
Smalltalk é uma linguagem de programação orientada a objeto dinamicamente tipada. __Em Smalltalk tudo é objeto: os números, as classes, os métodos, blocos de código, etc__ (exceto as variáveis de instâncias privadas). __Não há tipos primitivos__, ao contrário de outras linguagens orientadas a objeto. Strings, números e caracteres são implementados como classes em Smalltalk, por isso esta linguagem é considerada puramente orientada a objetos. Tecnicamente, todo elemento de Smalltalk é um objeto de primeira ordem.

# Expressividade (Smalltalk x Java)
Tanto smalltalk como java, implementam programação orientada a objetos. Sendo o smalltalk bem mais radical nesse aspecto, nele __tudo é objeto__.  
A estrutura de controle _If_, por exemplo, é apenas uma palavra reservada em java. Já o equivalente em smalltalk, _ifTrue:_, é um método da classe Boolean.  
Outro aspecto importante é que todo o código em smalltalk funciona através da troca de mensagens.

```smalltalk
Transcript show: 5 factorial asString.
```

No exemplo do fatorial, enviamos a mensagem _factorial_ para o objeto _5_ que responde _120_, então a mensagem _show:_ é enviada  para o objeto _Transcript_ com o argumento _120_. A invocação do método _show:_ faz com que os caracteres de seu argumento sejam exibidos no terminal.  
Em java, não utilizaríamos objetos e, muito menos, troca de mensagens para isso.

No exemplo a seguir, são impressas todas as potências de 2 entre 1 e 500. Analisando apenas o cálculo da potência, temos dois objetos envolvidos: _2_ como o receptor da mensagem (sendo a mensagem o método _raisedTo:_ da classe Number) e _i_ como o argumento da mensagem.

```smalltalk
1 to: 500 do: [:i |
Transcript show: '2 elevado a ', (i asString), ' é ', (2 raisedTo: i) asString; cr.
].
```

Na POO em java, quando nós rodamos o programa, a classe é definida, um ou mais objetos são instanciados, e a partir daí podemos chamar os métodos dos objetos.

Em Smalltalk, a abstração é mais semelhante ao mundo real: você possui um “mundo” de classes, cada uma com suas características próprias. Cada classe é praticamente um “processo” sozinho, que se comunica com outras classes ou “processos” usando mensagens. Essa passagem de mensagens, como definiu Alan Kay, é baseada em como as células e neurônios se comunicam um com o outro. Ou seja, em Smalltalk, um objeto não é simplesmente uma forma de abstração, é praticamente um organismo por si só. Isso eleva a palavra “orientação a objeto” a um novo nível, um nível de expressividade em OO que ainda não conseguimos alcançar com java.

# Avaliação Comparativa
A notação do Smalltalk é semelhante à escrita em inglês. Veja o código abaixo:

```smalltalk
Transcript show:'Olá Mundo'; cr.
```

Existe um objeto chamado _Transcript_ que representa um console, isto é, um lugar onde as mensagens são exibidas. Nessa linha é solicitado ao _Transcript_ que seja exibida a string ‘Olá Mundo’, através do método _show:_ que recebe como parâmetro uma string. Ao final é feita outra solicitação ao objeto _Transcript_ (separada por ;) para que pule uma linha através do método _cr_, como o _\n_ em java.

```java
public class hello{
	public static void main(String[] args){
		System.out.print("Ola Mundo\n");
	}
}
```

O _if_ do Java, em Smalltalk é _ifTrue:_, um método declarado na classe Boolean que recebe com parâmetro um bloco de comandos, que em Smalltalk são comandos que estão dentro de colchetes [ ]. Já o _whileTrue:_ é um método definido nas classes BlockClosure e  BlockContext, portanto se o bloco for avaliado e retornar um valor True, então o bloco passado como parâmetro para o whileTrue: será avaliado. O exemplo abaixo já integra vários conceitos:

```smalltalk
| i |
i := 9.
[ i > 0 ] whileTrue: [
	Transcript show: (i asString), ' -> ',
		(i odd ifTrue: ['Ímpar'] ifFalse: ['Par']); 
		cr.
	i := i - 1.
].
```

Na primeira linha é definida a variável temporária _i_, que em Smalltalk não precisa ser definido o tipo.   
Na segunda linha é realizado um comando de atribuição.  
A terceira linha declara um bloco _[ i > 0 ]_ que ao ser avaliado retorna um True ou False, e este bloco recebe a chamada ao método _whileTrue:_ que executará o outro bloco enquanto a condição for verdadeira. 
A partir da quarta linha, concatenação de strings em Smalltalk é realizada através de vírgula, portanto a variável _i_ está sendo convertida para string (_i asString_) e concatenada com a string _' -> '_, que será então concatenada com a string 'Par' ou 'Ímpar'.  
Para selecionar entre a string Par ou Ímpar é chamado o método _odd_ (que retorna true se o número for ímpar) para saber se o número é par ou ímpar, o resultado será um valor True ou False. Como o método _ifTrue:ifFalse:_ está definido na classe Boolean, então podemos chamá-lo a partir do objeto retornado pelo método _odd_. _ifTrue:ifFalse:_ é um método que recebe dois parâmetros, no caso o bloco que contém a string 'Par' e o bloco que contém a string 'Ímpar'. E para terminar, um comando de atribuição para decrementar o valor da variável _i_. A saída deste programa é a seguinte:

  __9 -> Ímpar__  
  __8 -> Par__  
  __7 -> Ímpar__  
  __6 -> Par__  
  __5 -> Ímpar__  
  __4 -> Par__  
  __3 -> Ímpar__  
  __2 -> Par__  
  __1 -> Ímpar__

Veja abaixo o código em java com o mesmo propósito do código anterior em smalltalk.
Nesse exemplo é possível observar as diferenças entre as duas linguagens em relação a declaração de variáveis, atribuição de valores a variáveis, estrutura de repetição, estrutura de controle e finalização de cada instrução (; em java e . em smalltalk).

```java
public class condicao {
	public static void main(String args[]) {
		int i = 9;
		while(i>0){
			if((i % 2)==0)
				System.out.println(i + " -> Par");
			else
				System.out.println(i + " -> Impar");
			i--;
		}
	}
}
```

# Conclusão
Analisando os exemplos anteriores, pode-se notar que o smalltalk em comparação com java, torna-se mais fácil de escrever, tendo muitos métodos para auxiliar na programação e exigindo menos "detalhes". Em relação a leitura, ambas as linguagens tem uma boa capacidade de leitura.  
O grande diferencial entre Smalltalk e a maioria das outras linguagens orientada a objeto é que tudo em smalltalk são objetos, inclusive if, while e for que não são comandos, e sim métodos.  
Smalltalk é relativamente fácil de aprender comparado a linguagens como C++ e ADA. O código-fonte Smalltalk é fácil de ler e de escrever, o que o torna uma ótima linguagem de programação para iniciantes.

# Referências
* https://en.wikipedia.org/wiki/Smalltalk
* https://pt.wikipedia.org/wiki/Smalltalk
* https://smalltalkbrasil.wordpress.com/
* http://www.smalltalk.com.br/blogs/st/
* https://mauricioszabo.wordpress.com/2010/02/19/smalltalk-e-a-nocao-de-objetos/
* https://marciobueno.com/linguagens-programacao/smalltalk-primeiras-linguagens-orientadas-objetos

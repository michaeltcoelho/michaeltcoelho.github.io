##Tipagem dinâmica

`a = 2`

Se você está acostumado a trabalhar com liguagens como C, C++, Java, C# ou afins, deve-se estar perguntando sobre o código acima. Como o Python sabe que deve representar um número? Como ele sabe o que é `a`?

Você já está entrando no mundo da tipagem dinâmica. No python, os tipos são determinados automaticamente em tempo de execução, não em resposta ás declarações previas presente em seu código.

##Atribuições

Não informamos ao Python para utilizar o nome `a` como variável e também não informamos a ele que a atribuição de `3` a `a` deve significar um objeto do tipo inteiro. No Python é natural como segue:

#####Declaração 

Uma variável qualquer, no nosso caso `a`, é criada ao receber um valor pela primeira vez. As atribuições futuras alteram a referência para um valor atribuído. Podemos considerar que as atribuições produzem variáveis.

#####Tipos

Uma variável criada não possui qualquer informação sobre o tipo associado. Em vez disso, o conceito de tipo está presente em objetos e não em variáveis. As variáveis sempre se referem a um objeto em particular, em dado momento específico.

#####Uso

Quando uma variável é utilizada, a mesma é substituida imediamente pelo objeto a que se refere correntemente. Todas as variáveis devem receber um valor explicitamente antes de serem utilizadas no decorrer do código.

Totalmente diferente das linguagem tradicionais, é umas das características e flexibilidade do Python. Para ter um bom entendimento sobre, é necessário ter claro a distinção entre nomes e objetos.

Quando declaramos:

`a = 3`

Conceitualmente…

1. Criar um objeto para representar o valor `3`.
2. Criar uma variável `a`, no caso ela ainda não existia.
3. Vincular a variável `a` ao objeto `3`.

Para uma melhor visualização segue a figura abaixo:

![1](object-reference.png "Nomes e Objetos")

Os vínculos das variáveis para os objetos no Python são chamados de referências, um tipo de associação entre o nome e o objeto. 

Contudo: as variáveis são apenas espaços em memória para armazenar nomes e realizar vínculos com objetos; os objetos são partes da memória para representar um valor que denotam informações `tag` de tipos.

Pelo menos conceitualmente, toda vez que você faz uma declaração no seu código, o Python cria um novo objeto (um trecho de memória) para representar esse valor. O python coloca em cache e reutiliza certos tipos de objetos imutáveis, como inteiros pequenos e strings, como forma de otimização; mas isso funciona como se cada valor fosse um objeto distinto.

Declarando:

`a = 3`

`b = a`

Declarando essas instruções, geramos o cenário capturado na figura abaixo.

![1](object-same-reference.png "Nomes e objetos, b = a")

Na segunda linha o Python cria a variável `b` e atribui a esse nome a variável `a`, ao mesmo tempo a mesma é substituída pelo objeto que a mesma referencia - `3`, agora `b` faz referencia ao mesmo objeto que a variável `a`. As variáveis `a` e `b` fazem referência ao mesmo objeto, isto é chamado de ***referência compartilhada*** no Python - vários nomes referenciando o mesmo objeto.

**O que aconteceria se alterássemos o valor de `a`?**

Assim como em todas as atribuições do Python, isso simplesmente irá criar um novo objeto para representar o novo valor atribuido, mesmo se o valor atribuido ter o mesmo tipo para qual `a` já fazia referencia.

`a = 3`

`b = a`

`a = "abobrinha"`

Podemos ver melhor na figura abaixo:

![1](object-reference-change.png "alterando a = "abobrinha" ")

##Referência e objetos mutáveis

Temos tipos como listas e dicionários no Python que são mutáveis, ou seja, quando realizamos certas operações, ocorrem alterações em objetos (no local) em si, em vez de criar um novo objeto e vinculá-lo. Para objetos que suportam tais alterações, precisamos nos aprofundar mais em ***referência compartilhada***, pois a alteração de um objeto pode afetar outros que o referenciam. 


`lista1 = [1, 2, 3]`

`lista2 = lista1`


Declaramos um a lista `lista1` que é simplesmente uma coleção de outros objetos, nesse caso contém os objetos `1`, `2` e `3`. Podemos acessar os objetos da lista `lista1` pela posição que os objetos ocupam, acessando `lista1[0]` podemos obter o objeto `1`. Logo na segunda linha atribuímos a `lista2`a lista `lista1`, agora as duas listas, `lista1` e `lista2` estão vinculadas ao mesmo objeto.

Escrevendo …

`lista1 = "joaozinho"`

Nossa `lista1` agora está vinculada a um novo objeto que representa `abobrinha`. E a nossa `lista2` que referenciava o mesmo objeto que a `lista1`? A nossa `lista2` ainda está se referindo ao objeto. Agora se alterarmos um objeto que está contido na `lista1`, teremos um efeito radicalmente.

`lista1[0] = "joaozinho"`

`print lista1`

`["joaozinho", 2, 3]`

Agora alteramos um objeto contido na `lista1` em vez de alterarmos a lista `lista1` em si. Essa alteração é aplicada ao objeto do tipo lista no local. Teremos o mesmo resultado para a `lista2`, pois a mesma compartilha o mesmo objeto que a `lista1`.

##Referências e coleta de lixo

Quando nomes referenciam objetos novos, o Python também coleta o objeto antigo caso o mesmo não seja referenciado por nenhum outro nome ou objeto. Essa recuperação automática de objetos é conhecida como ***coletor de lixo***.

Declarando…	

`a = 42`

`a = 'joaozinho'`  coleta `42`

`a = 3.14` coleta `joaozinho`

`a = [1, 2, 3]` coleta `3.14`


Sempre que `a` recebe um objeto, o Python recupera o objeto anterior, contanto que o mesmo objeto a ser recuperado não seja referenciado por nenhum outro nome ou objeto. Dessa maneira o espaço é devolvido automaticamente para o pool de espaços livres, para ser utilizado por um futuro objeto.



###Referências

[http://www.digi.com/wiki/developer/index.php/Python_Garbage_Collection](http://www.digi.com/wiki/developer/index.php/Python_Garbage_Collection)

[http://en.wikibooks.org/wiki/Python_Programming](http://en.wikibooks.org/wiki/Python_Programming)

[http://en.wikibooks.org/wiki/Think_Python](http://en.wikibooks.org/wiki/Think_Python)





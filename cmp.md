# Qué es la programación funcional 

La [programación funcional](https://es.wikipedia.org/wiki/Programaci%C3%B3n_funcional) puede ayudarnos a crear software más robusto, mantenible y fácil de testear. Quizás hayas empezado a oír hablar de lenguajes de programación funcional como [Scala](http://www.scala-lang.org/),[Haskell](https://www.haskell.org/) o [Lisp](https://es.wikipedia.org/wiki/Lisp), pero quizá no sepas todavía que [Java](https://www.java.com/) en su versión 8 permite usar la potencia de la programación funcional sin abandonar su [orientación a objetos](https://es.wikipedia.org/wiki/Programaci%C3%B3n_orientada_a_objetos).

Pero, ¿qué hace que lenguajes como [C](https://es.wikipedia.org/wiki/C_(lenguaje_de_programaci%C3%B3n)), [C++](https://es.wikipedia.org/wiki/C%2B%2B) o Java adopten la programación funcional?
_“Hay dos formas de diseñar software: una forma es hacerlo tan simple que obviamente no haya deficiencias, y la otra es hacerlo tan complicado que no haya deficiencias obvias. El primer método es mucho más difícil”__._

Desde que empiezas a programar con Java te enseñan qué es un lenguaje de programación orientado a objetos y que Java es uno de ellos. Te enseñan a programar de manera [imperativa](https://es.wikipedia.org/wiki/Programaci%C3%B3n_imperativa) y es como has programado desde entonces. Con estas herramientas tienes que crear la mejor solución posible y hasta hoy no ha ido mal. Pero, ¿y si te digo que hay una forma mejor de llegar a esas soluciones?

En la [programación declarativa](https://es.wikipedia.org/wiki/Programaci%C3%B3n_declarativa) no definimos cómo queremos resolver un problema, sino que definimos cuál es el problema. Un ejemplo sencillo para comparar estas dos formas de programar es encontrar en una lista de colores si tenemos el color _“red”__:_

 
 `boolean hasRed = false;`
 `for (String color : colors) {`
   `if (color.equals("red")) {`
      `hasRed = true;`
     `break;`
   `}`
`}`
`System.out.println("Has color red? " + hasRed);`

Aquí vemos cómo estamos definiendo la manera de resolver el problema. Esta forma de hacerlo es muy verbosa y nos hace tener que definir una variable *hasRed* para marcar si se ha encontrado o no, lo que hace que este código sea un poco _“feo”_
¿Y si te digo que ya has usado la forma declarativa?

 `System.out.println(“Has color red?:” + colors.contains(“red”));`
 
Esta solución es más concisa, más clara y más fácil de entender por cualquier persona. No sabemos la implementación que estamos usando ya que eso es cosa del código que hay por debajo. Lo que sí sabemos es exactamente lo que hace ese código: nos dice si _colors_ contiene_“red”_. Por suerte, para este ejemplo el API de Java nos provee del método _contains__,_ que nos ayuda a hacer nuestro código más legible, pero no siempre tendremos esa suerte.

En los casos en los que tengamos que crear nuestros propios métodos podemos usar la programación funcional, que es declarativa y por tanto nos puede ayudar a hacer nuestro código más limpio. Veamos un ejemplo de cómo podemos mejorar nuestro código usando programación funcional.

Dada una lista de números decimales queremos descontar un 20% a todos los que sean mayores de 25 y sumarlos: 

`BigDecimal sum = BigDecimal.ZERO;`
`for(BigDecimal number : numbers) {`
`if (number.compareTo(BigDecimal.valueOf(25)) >0) {`
`sum = sum.add(number.multiply(BigDecimal.valueOf(0.8)));`
`   }`
`   }`
`System.out.println("Total: " + sum);`

Seguro que ese código es muy familiar para todos. Como vemos, estamos creando una variable  sum donde vamos cambiando su valor en función de las condiciones que hemos definido en el enunciado.

Veamos ahora cómo escribir ese código de una manera mucho más clara de forma funcional primero en Java 8:
###### Y el mismo código usando Scala:
`val sum = numbers.filter(_ > 25)`
`.map(_ * .8)`
`.sum`
`  println(sum)`

Este código se puede “leer”. Cualquier persona que se ponga delante de él puede leerlo de la siguiente forma:

-   Filtrar los números mayores de 25.
-   Asignar a cada número un número igual a su 80%.
-   Usar el método _add_ para reducir esa lista.

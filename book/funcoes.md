## Funções

As funções em Clojure, são first-class e podem ser passadas ou retornadas de outras funções. A maioria dos códigos Clojure consiste principalmente em funções puras, portanto, dado um parâmetro input, sempre irá retornar o mesmo output sem causar side effects.

*defn* define o nome da função, por exemplo:
```
;;    name   params         body
;;    -----  ------  -------------------
(defn hello [name] (str "Hello, " name) )
```

A função acima, possui um único parâmetro, no entanto, você pode incluir quantos parâmetros quiser.
```
user=> (greet "students")
"Hello, students"
```

* Multi-arity
  * As funções podem receber diversos parâmetros, quantos vocês quiser (diferentes "arity"). Diferentes "arity", precisam ser definidas no mesmo *defn* - utilizar *defn* mais de uma vez, substituirá a função anterior.

  Cada *arity* é uma lista: ([param] body). Uma *arity* pode invocar outra. O corpo pode conter qualquer número de expressões e o valor de retorno é o resultado da última expressão.

  ```
  (defn messenger
  ([]     (messenger "Hello world!"))
  ([msg]  (println msg)
  ```

  Essa função declara duas *arity* (A primeira com 0 parâmetros, e a segunda com 1 parâmetro). A arity do parâmetro 0 chama a arity de 1 parâmetro com um valor padrão para imprimir. Chamamos essas funções passando o número apropriado de argumentos:

  ```
  user=> (messenger)
  Hello world!
  nil

  user=> (messenger "Hello class!")
  Hello class!
  nil
  ```

* Variadic functions
  * As funções podem definir vários parâmetros - isso é conhecido como uma função "variável". Os parâmetros variáveis ​​devem ocorrer no final da lista de parâmetros. Eles serão coletados em uma sequência para serem utilizados pela função.
  ```
  (defn hello [greeting & who]
  (println greeting who))
  ```
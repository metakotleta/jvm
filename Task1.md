# Задача "Понимание JVM"

``` java 

public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1 локальная переменная i помещается в Stack Memory во фрейм(кадр), созданный под метод main()
        Object o = new Object();        // 2 в heap(куче) выделяется память под объект Object, ссылка(переменная o) на данный объектв heap помещается в Stack Memory 
                                        // ClassLoader подгружает класс Object
        Integer ii = 2;                 // 3 Integer ii = 2 помещается в стэк во фрейм main()
        printAll(o, i, ii);             // 4 в момент вызова метода создаётся фрейм в Stack Memory, 
                                        // в который помещается ссылочная переменная o на ранее созданный объект Object
        System.out.println("finished"); // 7 в ранее созданный фрейм в стэке, куда передадим строку 
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5 в Stack Memory во фрейм printAll() помещается uselessVar. 
                                                    // ранее в этот же фрейм были помещены o,i,ii 
        System.out.println(o.toString() + i + ii);  // 6 создаётся новый фрейм, куда передадим новую сформировавшуюся строку 
    }
}

```


public class JvmComprehension { // Подгрузка классов с помощью ClassLoader в Metaspace

    public static void main(String[] args) { // Создаётся фрейм в стеке под метод main()
        int i = 1;                      // 1 Создание переменной i в фрейме main()
        Object o = new Object();        // 2 Создание объекта класса Object в куче и ссылки на него в фрейме main()
        Integer ii = 2;                 // 3 Создание объекта класса Integer в куче и ссылки на него в фрейме main()
        printAll(o, i, ii);             // 4 Передаём переменную i и ссылки на объекты классов Object и Integer из фрейма main()
        System.out.println("finished"); // 7 Вызов метода println, в который передаётся объект класса String
    }

    private static void printAll(Object o, int i, Integer ii) { // Создаётся фрейм в стеке под метод printAll(), в котором создаётся переменная и ссылки на объекты из полученных данных
        Integer uselessVar = 700;                   // 5 Создание нового объекта класса Integer в куче и ссылки на него в фрейме printAll()
        System.out.println(o.toString() + i + ii);  // 6 Вызов метода println, в который передаётся объект класса Object, у которого вызывается метод toString, а так же ссылки на объекты класса Integer из фрейма printAll(), после чего объекты очищаются сборщиком мусора
    }
}
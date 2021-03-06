Встроенные методы
================
Как упоминалось ранее, Zephir способствует объектно-ориентированному программированию, переменные, 
относящиеся к статическим типам, также могут обрабатываться как объекты.

Сравните эти два метода:

.. code-block:: zephir

    public function binaryToHex(string! s) -> string
    {
        var o = "", n; char ch;

        for ch in range(0, strlen(s)) {
            let n = sprintf("%X", ch);
            if strlen(n) < 2 {
                let o .= "0" . n;
            } else {
                let o .= n;
            }
        }
        return o;
    }

и:

.. code-block:: zephir

    public function binaryToHex(string! s) -> string
    {
        var o = "", n; char ch;

        for ch in range(0, s->length()) {
            let n = ch->toHex();
            if n->length() < 2 {
                let o .= "0" . n;
            } else {
                let o .= n;
            }
        }
        return o;
    }

Оба они имеют одинаковую функциональность, а во втором - объектно-ориентированное программирование. 
Вызывающие методы для статических типизированных переменных не оказывают никакого влияния на производительность, 
поскольку Zephir внутренне преобразует код из объектно-ориентированной версии в процедурную версию.

String
^^^^^^

Доступны следующие встроенные методы строки:

+-------------------+-------------------+----------------------------------------------------------------------------------+
| ООП               | Процедурный       | Описание                                                                         |
+-------------------+-------------------+----------------------------------------------------------------------------------+
| s->length()       | strlen(s)         | Получить длину строки                                                            |
+-------------------+-------------------+----------------------------------------------------------------------------------+
| s->trim()         | trim(s)           | Удалять пробелы (или другие символы) из начала и конца строки                    |
+-------------------+-------------------+----------------------------------------------------------------------------------+
| s->index("foo")   | strpos(s, "foo")  | Найти позицию первого вхождения подстроки в строке                               |
+-------------------+-------------------+----------------------------------------------------------------------------------+
| s->lower()        | strtolower(s)     | Строка в нижнем регистре                                                         |
+-------------------+-------------------+----------------------------------------------------------------------------------+
| s->upper()        | strtoupper(s)     | Строка в верхнем регистре                                                        |
+-------------------+-------------------+----------------------------------------------------------------------------------+

Array
^^^^^

Доступны следующие встроенные методы массива:

+-------------------+---------------------+----------------------------------------------------------------------------------+
| ООП               | Процедурный         | Описание                                                                         |
+-------------------+---------------------+----------------------------------------------------------------------------------+
| a->join(" ")      | join(" ", a)        | Объединение элементов массива в строку                                           |
+-------------------+---------------------+----------------------------------------------------------------------------------+
| a->reverse()      | array_reverse(a)    | Возвращает массив с элементами в обратном порядке                                |
+-------------------+---------------------+----------------------------------------------------------------------------------+

Char
^^^^

Доступны следующие встроенные методы char:

+-------------------+-----------------------------------------------------+
| ООП               | Процедурный                                         |
+-------------------+-----------------------------------------------------+
| ch->toHex()       | sprintf("%X", ch)                                   |
+-------------------+-----------------------------------------------------+

Integer
^^^^^^^

Доступны следующие встроенные методы целочисленного типа:

+-------------------+-----------------------------------------------------+
| ООП               | Процедурный                                         |
+-------------------+-----------------------------------------------------+
| i->abs()          | abs(i)                                              |
+-------------------+-----------------------------------------------------+


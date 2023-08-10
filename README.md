# StepikJavaBasics
### 1.1 История Java и особенности языка
![alt](/img/1.1.jpg)
### 1.3 Переменные, операции, выражения
![alt](/img/1.2.jpg)
### 1.4 Преобразование типов
Порядок расширения задается цепочкой:     
byte -> short-> int-> long -> float -> double.

<table bording=solid 1px ><tr>
<td>Спецификатор формата
Выполняемое форматирование
%s</td><td>
Строковое представление аргумента
%b</td></tr><td>
Логическое (булево) значение аргумента
%c</td><tr><td>
Символьное представление аргумента
%d</td><td>
Десятичное целое значение аргумента
%o</td><tr><td>
Восьмеричное целое значение аргумента
%x</td><td>
Шестнадцатеричное целое значение аргумента
%f</td><tr><td>
Десятичное вещественное значение с плавающей точкой
%e</td><td>
Экспоненциальное представление вещественного аргумента
%g</td><tr><td>
Выбирает более короткое представление из двух: %е или %f
%a</td><td>
Шестнадцатеричное значение с плавающей точкой
%t</td><tr><td>
Время и дата
%n</td><td>
Вставка символа новой строки
%h</td><tr><td>
Хэш-код аргумента
%%</td><td>
Вставка знака %</td><tr><td>
</td>
</table>

### 2.1 Операторы ветвления

**Оператор return**
Этот оператор выхода из метода. Он позволяет вернуть управление в тот метод, который ранее его вызвал. Если этот оператор применяется в теле метода main(), то это означает прекращение выполнения программы.

Используя return, можно после ввода исходных данных сразу проверить их корректность и прекратить программу после вывода соответствующего сообщения. Например, в следующей задаче нужно ввести трехзначное число и найти сумму его нечетных цифр. Но если число не трехзначное, то нужно просто вывести "ERROR" и закончить программу. Избежать вложенных операторов if позволит такой код:
```
public static void main(String[] args) {
        Scanner scan=new Scanner(System.in);
        int number=scan.nextInt();
        if(number<0) number=-number;
        if(number<100||number>999){ //неверные исходные данные
            System.out.println("ERROR");
            return; //прекращение работы программы
        }
        //поиск суммы нечетных цифр
       
}
```
Вообще метод return позволяет не только перейти в вызвавший метод, но и  вернуть в него какое-то значение. Т.е. он используется в формате return значение; Но поскольку метод main() имеет тип void (т.е. не предполагает возврат значения), то return здесь будет без параметра.

#### Задача
Пользователь вводит целое трехзначное число. Вывести сумму его нечетных цифр.

Если число не является трехзначным, вывести "ERROR".

Если нечетных цифр нет, то вывести "NO".

Тестовые данные
Sample Input 1:

367
Sample Output 1:

10
Sample Input 2:

-351
Sample Output 2:

9
#### Решение
String.
```
import java.util.Arrays;
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.nextLine();
        int sum = 0;
        if(a.contains("-")){
            String[] b = a.split("\\-"); // Заводим в массив и вырезаем -
            a=b[1];          //
        }
        if (a.length()>3) {     // Проверка на 3 символа в сканаре
            System.out.println("ERROR");
            return;
        }
        for (int i = 0; i < a.length(); i++) { // Проходимся по стрингу а
            if (a.charAt(i) % 2 != 0) {      // Проверка на нечётное число
                String b = "" + a.charAt(i) ; //  из чара в стринг
                int c = Integer.parseInt (b.trim ()); // из стринга в инт
                sum+=c;                //  сумируем в переменную инт
            }
        }
        if (sum==0){
            System.out.println("NO");
        } else{
        System.out.println(sum);  // вывод суммы
    }}}
```
UPD int
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int a=sc.nextInt(), sum = 0;
        if(a<0) a=-a;
        if(a<100|| a>999){
            System.out.println("ERROR");
            return;
        }
        
        int b = a%100, c1 = a%10, b1 = (b-c1)/10, a1=(a -b)/100;
        if (a1 % 2 !=0){
            sum+=a1;
        }
        if (b1% 2 !=0){
            sum+=b1;
        }
        if (c1% 2 !=0){
            sum+=c1;
        }
     //   System.out.println(b);
      //  System.out.println(c1);
       // System.out.println(b1);
       // System.out.println(a1);
        if(a1 % 2 ==0 && b1 % 2 ==0 && c1 % 2 ==0){
            System.out.println("NO");
        } else {
            System.out.println(sum);
        }
    }}
```

### 2.3 Вложенные циклы

Задача

Пользователь вводит высоту треугольника. Нарисовать треугольник из звездочек, как показано в примере теста. 

Если вводятся некорректные данные (высота  <= 0), то вывести "ERROR".

Тестовые данные
Sample Input:

5
Sample Output:

*****
 ****
  ***
   **
    *

решение
```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        if(a<=0){
            System.out.println("ERROR");
        }
        for (int i = 0; i < a; i++) {
            for (int j = a; j > i; j--) {
                System.out.print("*");
            }
            System.out.println();
            for (int k = 0; k <= i; k++) {
                System.out.print(" ");
            }
        }
    }
}
```
Решение автора курса

```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int height = scan.nextInt();
        if (height <= 0) {
            System.out.println("ERROR");
            return;
        }
        int probel = 0; //количество пробелов в первой строке
        int zvezd = height; //количество звезд в первой строке
        for (int i = 1; i <= height; i++){
            for (int j = 1; j <= probel; j++) { //выводим пробелы
                System.out.print(' ');
            }
            for (int j = 1; j <= zvezd; j++) { //выводим звезды
                System.out.print('*');
            }
            System.out.println(); //переводим курсор
            probel++; //в следующей строке будет пробелов на 1 больше
            zvezd--; //а звезд на 1 меньше
        }
    }
}
```

задача

Пользователь вводит ширину треугольника (от 1 до 9). Изобразить треугольник числами, как показано в примере теста.

Тестовые данные
Sample Input:

5
Sample Output:

55555
4444
333
22
1

решение
```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();

        for (int i = a; i >=1; i--) {
            for (int j = 1; j <=i; j++) {
                System.out.print(i+" ");
            }
            System.out.println();
        }
        }
    }

```

Задача
```
Пользователь вводит два целых числа (границы интервала). Границы могут быть введены некорректно (первое число больше второго). В этом случае нужно границы переставить местами.

Найти в данном интервале первое число с максимальной суммой цифр. Для отрицательного числа при расчете суммы цифр знак не учитывается. Например, сумма цифр -324 равна 9.

Тестовые данные
Sample Input 1:

15 22
Sample Output 1:

19
Sample Input 2:

-16 5
Sample Output 2:

-9
```

Решение
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int a = scan.nextInt();
        int b = scan.nextInt();
        int maxsum = 1;
        int chislosum = 0;
        if (a > b) {
            int c = a;
            a = b;
            b = c;
        }
        for (int chislo = a; chislo <= b; chislo++) {
            int m = Math.abs((chislo % 10) + (chislo / 10));
            if (m > maxsum) {
                maxsum = m;
                chislosum = chislo;
            }
        }
        System.out.println(chislosum);
    }
}
```

РЕшение автора
```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int a = scan.nextInt();
        int b = scan.nextInt();
        if (a > b) {
            int tmp = a;
            a = b;
            b = tmp;
        }
        int max = 0;
        int numberMax = 0;
        while (a <= b) {
            //находим сумму цифр a ->sum
            int sum = 0;
            int tmp = Math.abs(a); //неотрицательная копия
            while (tmp > 0) {
                sum += tmp % 10; //последнюю цифру к сумме
                tmp /= 10; //избавляемся от последней цифры
            }
            //сравниваем ее с максимальной
            if (sum > max) {
                max = sum;
                numberMax = a;
            }
            a++; //переходим к следующему числу диапазона
        }
        System.out.println(numberMax);
    }
}
```

### 2.4 Передача управления из тела цикла

Оператор break  позволяет организовать немедленный выход из цикла или оператора switch в обход любого кода, оставшегося в теле цикла, а также минуя проверку условия цикла. Если break применяется внутри набора вложенных циклов, то он прерывает выполнение только самого внутреннего цикла.

Пример 1. Пользователь вводит последовательность целых чисел, но не более 10. Нужно найти первое отрицательное число в этой последовательности, прекратить ввод и вывести его на консоль. Если таких чисел нет, то вывести "No".
```
import java.util.Scanner;

public class Example9 {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int find = 0; //если отрицательное число не будет найдено, find останется равен 0
        for (int i = 0;i < 10;i++) {
            int number=scan.nextInt();
            if (number < 0) {
                find = number; //запоминаем первое отрицательное число
                break; //прекращаем цикл
            }
        }
        if (find == 0){
            System.out.println("No");
        } else {
            System.out.println(find);
        }
    }
}
```
Кроме обычной формы оператора break (аналогичной языку C++) в Java этот оператор можно использовать еще как «цивилизованный» вариант оператора goto (который в Java вообще отсутствует). Для этого он используется с меткой:

break метка;

Метка – это имя блока кода, в котором встречается этот break. Управление передается за пределы именованного блока. Таким образом, break с меткой можно использовать для выхода из ряда вложенных блоков.

Пример 2.  Имеются три вложенных цикла, первый из которых помечен меткой BLOCK. Оператор break BLOCK; передает управление за пределы самого внешнего цикла (на оператор, который выводит значение суммы). Таким образом, в результате работы этой программы будет напечатано: sum= 26:
```
public class Example8 {
    public static void main(String[] args) {
        int sum = 0;
        int i = 1;
        BLOCK:while (i < 10){
            do{
                for(int k = 0;k < 5;k++){
                    sum += k;
                    if (sum>25) break BLOCK;
                }
            } while (sum < 40);
            i++;
        }
        System.out.println("sum= "+sum); //на этот оператор передает управление break BLOCK
    }
}
```
Оператор continue позволяет организовать досрочное завершение шага итерации (повторения) цикла. При его выполнении происходит переход к следующей итерации, пропуская оставшийся до конца тела цикла код. В циклах while и do-while оператор continue передает управление на проверку условия, а в цикле for сначала выполняются модификации, а затем проверяется условие продолжения цикла.

Пример 3. На консоль выводятся четные числа от 1 до 10:
```
public class Example10 {
    public static void main(String[] args) {
        int i = 0;
        while (i < 10) {
            i++;
            if (i % 2 != 0) continue;//если нечетное, переходим к следующему
            System.out.println(i); //сюда попадаем, если четное
        }
    }
}
```
Оператор continue также можно использовать с меткой, обозначающей тот охватывающий цикл, выполнение которого должно быть продолжено.

Пример 4. Перебираются пары чисел i и j, в которых  от j < i . Каждое из чисел изменяется от 0 до 4.

Внимание!  Существует более простой способ решения этой задачи. Данный  пример просто иллюстрирует continue с меткой.
```
public class Example11 {
    public static void main(String[] args) {
        int i;
        ONE: for (i = 0; i < 5; i++) {
            for (int j = 0; j < 5; j++) {
                if (i == j) continue ONE;
                System.out.printf("i=%d j=%d \n", i, j);
            }
        }
    }
}
На консоль выводится:

i=1 j=0 
i=2 j=0 
i=2 j=1 
i=3 j=0 
i=3 j=1 
i=3 j=2 
i=4 j=0 
i=4 j=1 
i=4 j=2 
i=4 j=3 
```
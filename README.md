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

### 3.1 Методы в Java

Бональный метод c doble
```
class main{
    public static void main(String[] args) {
        double a= 13.47, b = 1.347, c = 134.7;
        double result = mixi(a,b,c);
        System.out.println(result);
    }
    public static double mixi(double x,double y, double z){
        double max = x>y ? x : y;
        max = z>max ? z : max;
        return max;
    }
}
```
c SB
```
class main{
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("data");
        mixi(sb);
        System.out.println(sb);
    }
    public static void mixi(StringBuilder s){
        s.append(".txt");
    }
}
```


**Задание** : Пользователь вводит границы диапозона целыч не отрицательных чисел, нужно вевести из этого диапозона число с макс. суммой цифр.
  Если таких чисел 2 то , первое из них.
```
package New;

import java.util.Scanner;

public class Ex {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();
        int res = mixi(a,b);
        System.out.println(res);
    }

    public static int mixi(int x,int y) {
        x = Math.min(x, y);
        y = Math.max(x, y);

        int max = x;
        int mSum = sum(x);
        x++;
        while (x<=y){
            int suma = sum(x);
            if (suma > mSum){
                mSum=suma;
                max=x;
            }
            x++;
        }
        return max;
    }

    public static int sum(int zero){
        int sum =0;
        while (zero != 0){
            sum += zero %10;
            zero/=10;
        }
        return sum;
    }
}

```

### Задача

Напишите статический метод isSimple(), который возвращает true, если аргумент является простым числом, и false - в противном случае.

Простым называется целое положительное число, которое не имеет других делителей, кроме единицы и себя самого.

Отрицательные числа не могут быть простыми (поэтому функция должна возвращать false). Простыми также не являются числа 0 и 1.

В методе main продемонстрировано использование метода isSimple(). Этот код менять нельзя!

Тестовые данные
Номер теста	Входные данные	Выходные данные
1	1 13 23 67 10	false true true true false
2	-5 6 9 29 5	false false false true true
3	127 69 -3 0 7	true false false false true
Sample Input:

1 13 23 67 10
Sample Output:

false true true true false

### Решение
Моё
```
import java.math.BigInteger;
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        for (int i = 0; i < 5; i++) {
            int number = scan.nextInt();
            isSimple(number);
        }
    }
    public static int isSimple(int iteger){
        int a = iteger;
        BigInteger bigInteger = BigInteger.valueOf(a);
        boolean probablePrime = bigInteger.isProbablePrime((int) Math.log(a));
        if (a == 1 || a<0 || a == 0){
            probablePrime = false;
        }
        System.out.print(probablePrime+" ");
        return iteger;
    }
}
```
Автора курса
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        for (int i = 0; i < 5; i++) {
            int number = scan.nextInt();
            System.out.print(isSimple(number) + " ");
        }
    }
    // put your code here
    
    static boolean isSimple(int n) {
       if (n <= 0 || n == 1) {
           return false;
       }
       for (int i = 2; i < n; i++) {
           if (n % i == 0) {
               return false;
           }
       }
       return true;
    }
}
```

задача 

Напишите статический  метод printDivider(), который выводит все делители натурального числа через пробел (включая единицу и само число). Метод не возвращает никакого значения!

Пример использования этого метода в main() менять нельзя!

Тестовые данные
Sample Input:

246
Sample Output:

1 2 3 6 41 82 123 246

решение
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int number = scan.nextInt();
        printDivider(number);
    }
    public static void printDivider(int a){
        for (int i = 1; i <=a ; i++) {
            if(a%i==0){
                System.out.print(i+" ");
            }
        }
    }
}
```
задача 

Напишите статический метод maxNumberDivider(), который в заданном диапазоне находит число с наибольшим количеством делителей.

Метод main() менять нельзя!

Совет: сделайте отдельный  метод, который подсчитывает количество делителей числа, а затем вызывайте его в методе maxNumberDivider().

Тестовые данные
Sample Input:

530 545
Sample Output:

540

решение
моё
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int a = scan.nextInt();
        int b = scan.nextInt();
        int max = maxNumberDivider(a, b);
        System.out.println(max);
    }
    public static int maxNumberDivider(int a,int b){
    int max = 0;
    int count = 0;
        for (int i = a; i < b; i++) {
          int h = printDivider(i);
          if (h>count){
              count = h;
              max = i;
          }
        }
        return max;
    }

    public static int printDivider(int a){
        int count = 0;
        for (int i = 1; i <=a ; i++) {
            if(a%i==0){
                count++;
            }
}
       return count;
    }
}
```

автора курса
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int a = scan.nextInt();
        int b = scan.nextInt();
        int max = maxNumberDivider(a, b);
        System.out.println(max);
    }
    // put your code here
    static int maxNumberDivider(int a, int b) {
        if (a > b) {
            int tmp = a;
            a = b;
            b = tmp;
        }
        int max = a;
        int kolMax = kolDivider(a);
        a++;
        while (a <= b) {
            if (kolDivider(a) > kolMax) {
                kolMax = kolDivider(a);
                max = a;
            }
            a++;
        }
        return max;
    }

    static int kolDivider(int a) {
        int kol = 0;
        for (int i = 1; i <= a; i++) {
            if (a % i == 0) {
                kol++;
            }
        }
        return kol;
    }

}
```

Задача 

Напишите две перегрузки статического  метода square() для вычисления площади прямоугольника. В одном случае в метод передаются две стороны прямоугольника, а в другом - одна сторона квадрата (все - вещественные числа).

В методе main() вводится сначала целое число:

1 означает, что нужно вычислить площадь квадрата. И затем следует ввод одного вещественного числа (стороны квадрата)
2 означает, что нужно вычислить площадь прямоугольника. Затем следует ввод двух сторон прямоугольника.
Выводимую площадь нужно представить с двумя знаками после десятичной точки.

Тестовые данные
Sample Input 1:

2 4.4 3.2
Sample Output 1:

14.08
Sample Input 2:

1 5.5
Sample Output 2:

30.25

решение 

```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        double b =sc.nextDouble() ;
        if (a == 1){
            square(a,b);
        }else {
            double c =sc.nextDouble();
            square(a,b,c);
        }
    }
    static void square(int a, double b, double c ){
           double q =b*c;
           System.out.printf("%.2f",q);
    }
    static void square(int a, double b){

            double q = Math.pow(b,2);
            System.out.printf("%.2f",q);
    }
}
```

Задача
```
Напишите четыре перегрузки статического метода average(), который находит среднее арифметическое

 двух вещественных чисел;
трех вещественных чисел;
двух целых чисел
трех целых чисел
В методе main() показано использование методов average() - его менять нельзя!

Подумайте, можно ли сократить число перегрузок? Если да, то какие методы можно удалить?

Тестовые данные
Sample Input:

3 4 8
7.2 0.3 4.8
Sample Output:

3.50 5.00
3.75 4.10
```

Решение
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int a = scan.nextInt();
        int b = scan.nextInt();
        int c = scan.nextInt();
        double x = scan.nextDouble();
        double y = scan.nextDouble();
        double z = scan.nextDouble();
        System.out.printf("%.2f %.2f\n", average(a, b), average(a, b, c));
        System.out.printf("%.2f %.2f\n", average(x, y),average(x, y, z));
    }
//    public static double average(double a, double b){
//        double q = (a+b)/2;
//        return q;
//    }

    public static double average(double x, double y){
        double q = (x+y)/2;
        return q;
    }
    public static double average(double x, double y, double z){
        double q = (x+y+z)/3;
        return q;
    }
}

/// 3 4 8
///  7,2 0,3 4,8
```

Запись со сканера в массив и вывод его .

```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
       Scanner sc = new Scanner(System.in);
       int a = sc.nextInt();
       int[] b = new int[a];
        for (int i = 0; i < b.length ; i++) {
            b[i] = sc.nextInt();
        }

        for(int el:b){
            System.out.print(el+" ");

        }
       System.out.println("\n"+b.length);
    }
}

```

random       
int
```
public static void main(String[] args) {
    Scanner scan = new Scanner(System.in);
    int[] a= new int[6];
    long seed = scan.nextLong(); //вводим начальное значение генератора
    Random rand = new Random(seed); //Создаем объект класса Random
    for(int i = 0; i < a.length; i++){
         a[i] = rand.nextInt(-5, 6); //числа от -5 до 5
         System.out.print(a[i] + " ");
    }
    System.out.println();
}
```
doble
```
 public static void main(String[] args) {
     Scanner scan = new Scanner(System.in);
     long seed = scan.nextLong(); //вводим начальное значение генератора
     Random rand = new Random(seed); //Создаем объект класса Random
     double[] b = new double[10];
     for(int i = 0; i < b.length; i++){
         b[i] = rand.nextDouble(10., 20.); //от 10.0 до 20.0
         System.out.printf("%.1f ",b[i]);
     }
     System.out.println();
}
```

```
import java.util.Arrays;
import java.util.Random;
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int gen = sc.nextInt();
// Создание массива, рандом числами и вывод в консоль
        Random r = new Random(gen);
        int[] a = new int[n];
        for (int i = 0; i <a.length ; i++) {
            a[i] = r.nextInt(-10,11);
            System.out.print(a[i]+ " ");
        }
        System.out.println();
        // Сумма элементов массива
        int sun = 0;
        for (int el: a){
            sun+=el;
        }
        System.out.println("Cумма равна:"+sun);
        // Подсчет количества элементов в массиве, удовлетворяющих некоторому условию
        int kol = 0;
        for (int el: a){
            if(el == 0 ){
                kol++;
            }
        }

        System.out.println("Колличество нулей: "+kol);

        // Перебор элементов с четными (нечетными) индексами
        // 1 вар
        /*   double p = 1;
        for (int i = 0; i <a.length ; i++) {
            if(i%2!=0){
                p *= a[i];
            }
        }
        System.out.println("Произведения с нечет индексами "+p);
*/
        double p = 1;
        for (int i = 1; i <a.length ; i+=2) {
                p *= a[i];
        }
        System.out.printf("Произведения с нечет индексами %.2f",p);
        // Поиск максимального значения в массиве
        int max = a[0];
        int imax = 0;
        for (int i = 0; i <a.length ; i++) {
            if (a[i]>=max){
                max = a[i];
                imax = i;
            }
        }
        System.out.println("\nМаксимум = "+max+"\nА его индек "+ imax);

    }
}

```

Как отзеркалить массив массив местами.
```
import java.util.Random;
import java.util.Scanner;
import java.util.stream.IntStream;

class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int gen = sc.nextInt();
// Создание массива, рандом числами и вывод в консоль
        Random r = new Random(gen);
        int[] a = new int[n];
        for (int i = 0; i <a.length ; i++) {
            a[i] = r.nextInt(-5, 16);
            System.out.print(a[i]+" ");
        }
        System.out.println();
        int[] b = IntStream.rangeClosed(1, a.length).map(i -> a[a.length-i]).toArray();
        for (int i = 0; i <b.length ; i++) {
            System.out.print(b[i]+" ");
        }
    }}
```
## Задача
Массив из целых чисел заполнить случайными значениями от -5 до 5 (включая обе границы) Пользователь вводит размер массива, а затем начальное значение генератора случайных чисел.

Вывести исходный массив на консоль в одной строке, разделяя элементы пробелами. Пробел должен быть в том числе и после последнего элемента массива.

Найти сумму положительных элементов массива и произведение отрицательных элементов. Произведение быстро растет, поэтому оно должно иметь тип double.

C новой строки вывести результаты программы через пробел (сначала сумму, а потом произведение). 

Тестовые данные
Sample Input:

10 7
Sample Output:

-3 5 5 -3 1 -1 0 2 5 5 
23 -9.0
## Решения
```
import java.util.Arrays;
import java.util.Random;
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int gen = sc.nextInt();
// Создание массива, рандом числами и вывод в консоль
        Random r = new Random(gen);
        int[] a = new int[n];
        for (int i = 0; i <a.length ; i++) {
            a[i] = r.nextInt(-5, 6);
            System.out.print(a[i]+" ");
        }
        int sun = 0;
        double minus = 1;
        for (int el: a){
            if(el>=0){
            sun+=el;}
            if(el<0){
                minus*=el;
            }
        }
        System.out.println("\n"+sun+" "+minus);
    }}
```
Автора курса
```
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt();
        int beg = scan.nextInt();
        Random rand = new Random(beg);
        int[] mas = new int[n];
        for(int i = 0; i < mas.length; i++) {
            mas[i] = rand.nextInt(-5,6);
            System.out.print(mas[i] + " ");
        }
        System.out.println();
        int sum = 0;
        double product = 1;
        for (int el:mas) {
            if(el > 0){
                sum += el;
            }
            if(el < 0) {
                product *= el;
            }
        }
        System.out.println(sum + " " + product);
    }
}
```

## Задача
Массив из вещественных чисел заполнить случайными значениями от 0 до 5 (не включая). Пользователь вводит размер массива, а затем начальное значение генератора случайных чисел.

Вывести исходный массив на консоль в одной строке, разделяя элементы пробелами. Пробел должен быть в том числе и после последнего элемента массива. 

Найти среднее арифметическое элементов массива и вывести его с новой строки. Заменить все элементы, большие среднего, его значением.

C новой строки вывести преобразованный массив. Элементы отделяются пробелами. 

Все вещественные числа при выводе округляются до двух знаков после десятичной точки.

Тестовые данные
Sample Input:

10 45
Sample Output:

3.63 4.35 1.50 3.77 1.29 3.07 2.09 4.80 4.70 3.77 
3.30
3.30 3.30 1.50 3.30 1.29 3.07 2.09 3.30 3.30 3.30
## Решения
```
import java.util.Arrays;
import java.util.Random;
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int gen = sc.nextInt();
// Создание массива, рандом числами и вывод в консоль
        Random r = new Random(gen);
        double[] a = new double[n];
        double sum = 0;
        for (int i = 0; i <a.length ; i++) {
            a[i] = r.nextDouble(0, 5);
            System.out.printf("%.2f ",a[i]);
            sum+=a[i];
        }

        System.out.printf("\n%.2f",sum/n);
        System.out.println();

        for (int i = 0; i < a.length; i++) {
           if(a[i]>sum/n){
               a[i]=sum/n;
           }
            System.out.printf("%.2f ",a[i]);
        }



    }}
```

## Задача
Массив целых неотрицательных чисел вводится с консоли. Сначала пользователь вводит количество элементов массива, а потом сами элементы.

Найти последний минимальный элемент и заменить его  на -1. 

Преобразованный массив вывести на консоль, отделяя элементы пробелами.

Тестовые данные
Sample Input:

8
2 11 2 15 6 2 20 7
Sample Output:

2 11 2 15 6 -1 20 7
## Решения
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int[] b = new int[a];
        for (int i = 0; i < b.length ; i++) {
            b[i] = sc.nextInt();
        }


        int min = b[0];
        int minInd = 0;
        for (int i = 0; i <b.length ; i++) {
            if (b[i]<=min){
                min = b[i];
                minInd=i;
            }
        }
        b[minInd]=-1;
        for(int el:b) {
            System.out.print(el + " ");
        }
    }
}
```

## Задача
Массив из целых чисел заполнить случайными значениями от -5 до 15 (включая обе границы) Пользователь вводит размер массива, а затем начальное значение генератора случайных чисел.

Вывести исходный массив на консоль в одной строке, разделяя элементы пробелами. Пробел должен быть в том числе и после последнего элемента массива.

Поменять местами первый максимальный и последний отрицательный элементы. Если отрицательных элементов нет в массиве, то он должен остаться без изменения.

C новой строки вывести измененный массив, отделяя элементы пробелами.

Тестовые данные
Sample Input:

10 77
Sample Output:

7 -5 -1 5 -3 8 2 -1 -3 -3 
7 -5 -1 5 -3 -3 2 -1 -3 8
## Решения
```
import java.lang.reflect.Array;
import java.util.Arrays;
import java.util.Collections;
import java.util.Random;
import java.util.Scanner;
import java.util.stream.IntStream;

class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int gen = sc.nextInt();
// Создание массива, рандом числами и вывод в консоль
        Random r = new Random(gen);
        int[] a = new int[n];
        for (int i = 0; i <a.length ; i++) {
            a[i] = r.nextInt(-5, 16);
            System.out.print(a[i]+" ");
        }
        
        System.out.println();
        
        int min = a[0];
        int minInd = 0;
        int max = a[0];
        int imax = 0;
        for (int i = 0; i <a.length ; i++) {
            if (a[i]>=max){
                max = a[i];
                imax = i;
            }
            if(a[i]<0){
                min = a[i];
                minInd = i;
            }
        }

        int tmp = a[minInd];
        a[minInd]=a[imax];
        a[imax] = tmp;

        for (int i = 0; i <a.length ; i++) {
            System.out.print(a[i]+" ");
        }
        }
    }
```
Автора курса
```
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int[] a = new int[scan.nextInt()];
        Random rand = new Random(scan.nextLong());
        for(int i = 0; i < a.length; i++) {
            a[i] = rand.nextInt(-5, 16);
            System.out.print(a[i] + " ");
        }
        System.out.println();
        int imax = 0;
        int ineg = -1;
        for(int i=0; i < a.length; i++) {
            if (a[i] > a[imax]) {
                imax = i;
            }
            if (a[i] < 0) {
                ineg = i;
            }
        }
        if(ineg != -1) { //отрицательные есть
            int tmp = a[ineg];
            a[ineg] = a[imax];
            a[imax] = tmp;
        }
        for(int i = 0; i < a.length; i++) {
            System.out.print(a[i] + " ");
        }
        System.out.println();
    }
}
```












## Задача

## Решения
```

```

## Задача

## Решения
```

```
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
**Статические методы Arrays.**

**Метод Arrays.toString()**
String toString(Object[] a)
Этот метод принимает ссылку на массив (перегружен для всех базовых типов данных), а возвращает строковое представление массива. Например:
```
int[] mas = {1, 2, -3, 4, 25, 6, 17, -1, 9, 6};
String str=Arrays.toString(mas);
System.out.println(str);
```
На консоль будет выведено:
```
[1, 2, -3, 4, 25, 6, 17, -1, 9, 6]
```

**Метод Arrays.sort()**
void sort(Object[] a)
Выполняет сортировку (упорядочивание) массива по возрастанию. Может может применяться только к таким массивам,  для элементов которых реализована операция сравнения  (на больше-меньше). Для всех базовых типов и типа String это выполняется.

Реализует быструю сортировку (QuickSort).

Отсортируем массив mas и выведем его на консоль:
```
Arrays.sort(mas);
System.out.println(Arrays.toString(mas));
Получим упорядоченный по возрастанию массив:

[-3, -1, 1, 2, 4, 6, 6, 9, 17, 25]
```
Для массивов примитивных типов отсортировать массив по убыванию методом Arrays.sort() не получиться. А вот для массива строк - пожалуйста!  Для этого нужно вторым аргументом в метод sort() передать метод Collections.reverseOrder() (импортировать класс Collections тоже нужно, разумеется).
```
String[] list = {"Даша", "Яна", "Андрюха", "Ромка"};
Arrays.sort(list, Collections.reverseOrder());
System.out.println(Arrays.toString(list));
На консоли получим:

[Яна, Ромка, Даша, Андрюха]
```
Если нужно отсортировать только часть массива, то используется следующая перегрузка метода sort():

void sort(Object[] a, int fromIndex, int toIndex)
Сортируется часть массива a от fromIndex (включая) до toIndex (не включая).
```
int[] mas = {1, 2, -3, 4, 25, 6, 17, -1, 9, 6};
Arrays.sort(mas, 3, 8);
System.out.println(Arrays.toString(mas));
Будет выведено на консоль (отсортированную часть массива я выделила красным цветом:

[1, 2, -3, -1, 4, 6, 17, 25, 9, 6]
```

**Метод Arrays.binarySearch()**
 int binarySearch​(Object[] a, Object key)
Методом бинарного поиска находит в массиве a  индекс элемента key.  Массив a должен быть предварительно отсортирован! Если в массиве таких элементов несколько, то находится индекс одного из них (какого именно - не гарантируется). Если искомый элемент в массиве отсутствует, то метод вернет отрицательное число.
```
int[] mas = {1, 2, -3, 4, 25, 6, 17, -1, 9, 6};
Arrays.sort(mas);
System.out.println(Arrays.toString(mas));
int ind = Arrays.binarySearch(mas, 5);
if(ind >= 0) {
     System.out.println("Индекс элемента = " + ind);
}else{
     System.out.println("Элемент отсутствует");
}
```
Поскольку значения 5 нет в массиве, будет выведено "Элемент отсутствует".

**Метод Arrays.fill()**
void fill(Object[] a, Object val)
Заполняет массив a одинаковыми значениями val.  Работает только с одномерными массивами.

Например, вещественный массив b заполняется значениями 2.5:
```
double[] b = new double[5];
Arrays.fill(b, 2.5);
System.out.println(Arrays.toString(b));
Получаем:

[2.5, 2.5, 2.5, 2.5, 2.5]
```
Заполнить можно не только весь массив, но и его часть: от индекса fromIndex до индекса toIndex (не включая):

void fill(Object[] a, int fromIndex, int toIndex, Object val)
Если применить к полученному ранее массиву b следующий код:
```
Arrays.fill(b, 2, 4, 0.8);
System.out.println(Arrays.toString(b));
То на консоли получим:

[2.5, 2.5, 0.8, 0.8, 2.5]

```
**Метод Arrays.copyOf()**
int[] copyOf(int[] original, int newLength)
Создает новый массив и копирует в него элементы массива original. Параметр newLength - это длина нового массива. Если она меньше длины исходного массива original, то лишние элементы игнорируются. Если больше - то в конце элементы заполняются нулями.

Существуют перегрузки этого метода для всех базовых типов. Для ссылочных типов нужно понимать, что копируются в новый массив только ссылки, а сами объекты, на которые они ссылаются, остаются те же.
```
int[] mas = {1, 2, -3, 4, 25, 6, 17, -1, 9, 6};
int[] c = Arrays.copyOf(mas, 5);
System.out.println(Arrays.toString(c));
На консоли получим:

[1, 2, -3, 4, 25]

int[] mas = {1, 2, -3, 4, 25, 6, 17, -1, 9, 6};
int[] d = Arrays.copyOf(mas, 15);
System.out.println(Arrays.toString(d));
Получаем:

[1, 2, -3, 4, 25, 6, 17, -1, 9, 6, 0, 0, 0, 0, 0]

Пример со строками:

String[] list = {"Даша","Яна", "Андрюха","Ромка"};
String[] list2 = Arrays.copyOf(list,3);
System.out.println(Arrays.toString(list2));
На консоли получаем:

[Даша, Яна, Андрюха]
```
А вот как это выглядит в памяти:
![alt](/img/111.png)

 **Метод Arrays.copyOfRange()**
int[] copyOfRange(int[] original, int from, int to)
Создает  массив и копирует в него элементы массива original с индекса from до индекса to (как обычно, не включая этот элемент). Аналогично методу copyOf() существуют перегрузки для различных типов элементов массива.
```
int[] mas = {1, 2, -3, 4, 25, 6, 17, -1, 9, 6};
int[] d = Arrays.copyOfRange(mas, 4,8);
System.out.println(Arrays.toString(d));
Получаем на консоли:

[25, 6, 17, -1]
```
С остальными методами класса Arrays рекомендую познакомиться в официальной документации по Java:  [vot](https://docs.oracle.com/javase/7/docs/api/java/util/Arrays.html)




## Задача
Пользователь вводит размер массива и начальное значение генератора случайных чисел.

Затем он вводит контрольный элемент (целое число).

Создать массив заданного размера и заполнить его случайными числами от 2 до 15. Отсортировать массив по возрастанию. Распечатать отсортированный массив, используя метод toString() - в квадратных скобках, элементы через запятую.

Найти в отсортированном массиве индекс контрольного элемента и удалить все элементы после него (создать новый массив нужного размера).

Если контрольный элемент отсутствовал в массиве, то вывести "ERROR". В противном случае распечатать полученный массив методом toString().

Тестовые данные
Sample Input:

8 11
10
Sample Output:

[5, 6, 7, 10, 11, 13, 14, 15]
[5, 6, 7, 10]
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
        Random r = new Random(gen);
        int[] a = new int[n];
        int con = sc.nextInt();


        for (int i = 0; i <a.length ; i++) {
            a[i] = r.nextInt(2, 16);
        }
        Arrays.sort(a);
        System.out.println(Arrays.toString(a));

       int find = Arrays.binarySearch(a,con);
       if(find<0){
           System.out.println("ERROR");
           return;
       }

        int[] b = Arrays.copyOf(a,find+1);
        System.out.println(Arrays.toString(b));
        }
        }

```

## Задача
Пользователь вводит размер массива и начальное значение генератора случайных чисел. 

Создать массив  вещественных чисел заданного размера и заполнить его случайными числами от 0 до 2. Распечатать исходный массив, используя метод toString() - в квадратных скобках, элементы через запятую.

С новой строки вывести на консоль сумму максимального и минимального элементов массива.

Тестовые данные
Sample Input:

5 25
Sample Output:

[1.4631897195641836, 0.10745131965527377, 1.2906709676610488, 0.14895347726291952, 0.012141832026828503]
1.4753315515910121
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
        Random r = new Random(gen);
        int[] a = new int[n];
        int q = sc.nextInt(), e = sc.nextInt();

        for (int i = 0; i <a.length ; i++) {
            a[i] = r.nextInt(10, 21);
        }

        System.out.println(Arrays.toString(a));

        Arrays.sort(a,q,e+1);

        System.out.println(Arrays.toString(a));


        }
        }
```

# 4.3 Двумерные массивы

int[][] a = new int[3][4]; // создается массив из 3 строк и 4 столбцов

![alt](/img/13478.jpg)

```
int[][] array = {{3,5},{6,7},{9,10}};
int[][] ar = new int[][]{{1,2,3},{4,5,6},{7,8,9}};
```

Для перебора строк и столбцов двумерного массива обычно используются вложенные циклы. Пример заполнения двумерного массива случайными числами и вывод его на консоль в виде таблицы:
```
public class Example5 {
    public static void main(String[] args) {
        Random rand = new Random();
        int[][] a = new int[3][4];
        for (int i = 0; i < a.length; i++){ //a.length - количество строк
            for (int j = 0; j < a[i].length; j++) { //a[i].length - размер i-й строки
                a[i][j] = rand.nextInt(-10, 11);
                System.out.print(a[i][j] + "\t");
            }
            System.out.println();
        }
    }
}
```
С помощью метода Arrays.toString() не получится получить и вывести двумерный массив (будут выводиться непонятные идентификаторы - это имена объектов - вложенных массивов).

В отличие от не динамических массивов языка C++, память под двумерный массив не выделяется одним сплошным фрагментом. При объявлении массива a, показанном выше, создается массив ссылочных переменных, которые, в свою очередь, ссылаются на массивы - строки. Эти строки могут размещаться в разных местах динамической памяти:

Синтаксис многомерных массивов предусматривает отложенную инициализацию. И вложенные массивы (т.е. строки) могут быть разного размера:
```
int[][] b = new int[3][]; //создается массив из 3 х массивов
b[0] = new int [2]; //первая строка из 2 х элементов
b[1] = new int [4]; //вторая строка из 4 х элементов
b[2] = new int [3]; //третья строка из 3 х элементов
//все элементы по умолчанию инициализируются нулями
for (int i = 0; i < b.length; i++){ //b.length равно 3
    for (int j = 0; j < b[i].length; j++) { //b[i].length - длина текущей строки
          System.out.print(b[i][j] + "\t");
    }
    System.out.println();
}
```
 В результате на консоли мы увидим:

0    0    
0    0    0    0    
0    0    0 

## Пример

Пример. Пользователь вводит количество строк и столбцов двумерного массива, а затем начальное значение генератора случайных чисел. Создать целочисленный массив указанной размерности и инициализировать его случайными числами от 0 до 20. Массив вывести на консоль в виде таблицы, элементы которой отделяются знаками табуляции. 

Найти среднее арифметическое элементов массива и подсчитать количество элементов, меньших этого среднего. Вывести с новой строки среднее арифметическое (округленное до 2-х знаков после десятичной точки) и, через пробел, найденное количество.
```
import java.util.Random;
import java.util.Scanner;

public class Example6 {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int[][] array = new int[scan.nextInt()][scan.nextInt()];
        Random rand = new Random(scan.nextLong());
        double average = 0;
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                array[i][j] = rand.nextInt(21);
                System.out.print(array[i][j] + "\t");
                average += array[i][j];
            }
            System.out.println();
        }
        average /= (array.length*array[0].length); 
        int kol = 0;
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                if ( array[i][j] < average) {
                    kol++;
                }
            }
        }
        System.out.printf("%.2f %d", average, kol);
    }
}
```

## Задача
Пользователь вводит количество строк и столбцов двумерного массива, а затем начальное значение генератора случайных чисел. Создать целочисленный массив указанной размерности и инициализировать его случайными числами от -5 до 4. Массив вывести на консоль в виде таблицы, элементы которой отделяются знаками табуляции. Знак табуляции должен быть и  в конце каждой строки.

Найти максимальный элемент и подсчитать, сколько раз он встречается в массиве. Вывести максимальный элемент и найденное количество с  новой строки через пробел.

Тестовые данные
Sample Input:

4 5 100
Sample Output:

0	-5	-1	3	-4	
1	1	3	-2	-2	
-3	2	1	2	-3	
4	-5	3	-2	4	
4 2
## Решения
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int[][] array = new int[scan.nextInt()][scan.nextInt()];
        Random rand = new Random(scan.nextLong());
        int average = 0;
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                array[i][j] = rand.nextInt(-5,5);
                System.out.print(array[i][j] + "\t");

            }
            System.out.println();
        }

        int kol = 0;
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                if(array[i][j]>average){
                    average = array [i][j];
                }
                }
            }
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                if(array[i][j]==average){
                    kol++;
                }
            }
        }

        System.out.printf("%d %d", average, kol);
    }
}
## Задача
Пользователь вводит количество строк и столбцов двумерного массива, а затем начальное значение генератора случайных чисел. Создать массив целых чисел указанной размерности и инициализировать его случайными числами от -10 до 10. Массив вывести на консоль в виде таблицы, элементы которой отделяются знаками табуляции. Знак табуляции должен быть и  в конце каждой строки.

Вывести пустую строку после двумерного массива.

Для каждого столбца найти сумму положительных элементов и вывести на консоль, отделяя пробелами.

Тестовые данные
Sample Input:

4 5 89
Sample Output:

-3	-9	8	-6	2	
9	1	-4	-4	-5	
-10	5	-6	3	-3	
-2	7	-4	1	-4	

9 13 8 4 2 
## Решения
моё
```
import java.util.Arrays;
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int[][] array = new int[scan.nextInt()][scan.nextInt()];
        Random rand = new Random(scan.nextLong());
        int average = 0;
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                array[i][j] = rand.nextInt(-10, 11);
                System.out.print(array[i][j] + "\t");

            }
            System.out.println();
        }
        System.out.print("\n");
        int count = 0;
        for (int i = 0; i < array[0].length; i++) {
            for (int j = 0; j < array.length; j++) {
                if (array[j][i]>0){
                    count += array[j][i];
                }
            }
            System.out.print(count+" ");
            count =0;
        }
    }
}


```
Преподователя
```
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int[][] mas = new int[scan.nextInt()][scan.nextInt()];
        Random rand = new Random(scan.nextLong());
        for (int i = 0; i < mas.length; i++) {
            for (int j = 0; j < mas[i].length; j++) {
                mas[i][j] = rand.nextInt(-10, 11);
                System.out.print(mas[i][j] + "\t");
            }
            System.out.println();
        }
        System.out.println();
        for (int j = 0; j < mas[0].length; j++) { //количество столбцов одинаковое
            int sum = 0;
            for (int i = 0; i < mas.length; i++) {
                if (mas[i][j] > 0) {
                    sum += mas[i][j];
                }
            }
            System.out.print(sum + " ");
        }
    }
}

```
## Задача
Пользователь вводит количество строк и столбцов двумерного массива, а затем начальное значение генератора случайных чисел. Создать массив целых чисел указанной размерности и инициализировать его случайными числами от -10 до 10. Массив вывести на консоль в виде таблицы, элементы которой отделяются знаками табуляции. Знак табуляции должен быть и  в конце каждой строки.

В каждой строке найти первый отрицательный элемент и вывести индекс соответствующего столбца или слово "NO", если он отсутствует.

Тестовые данные
Sample Input:

4 3 100
Sample Output:

6	0	-6	
2	-9	-4	
7	7	3	
0	-9	-8	
2
1
NO
1

## Решения
моё
```
import java.util.Arrays;
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int[][] array = new int[scan.nextInt()][scan.nextInt()];
        Random rand = new Random(scan.nextLong());
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                array[i][j] = rand.nextInt(-10, 11);
                System.out.print(array[i][j] + "\t");

            }
            System.out.println();
        }

        for (int i = 0; i <array.length ; i++) {
            int count = -1;
            for (int j = 0; j <array[i].length ; j++) {
                if(array[i][j]<=count){
                    count = j;
                    break;
                }
            }
            if (count>=0){
            System.out.println(count);
            count = 0;
            }else {
                System.out.println("NO");
            }

        }

    }
}

```
преподователя

```
import java.util.Random;
import java.util.Scanner;

public class Main{
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int[][] mas = new int[scan.nextInt()][scan.nextInt()];
        Random rand = new Random(scan.nextLong());
        for (int i = 0; i < mas.length; i++) {
            for (int j = 0; j < mas[i].length; j++) {
                mas[i][j] = rand.nextInt(-10, 11);
                System.out.print(mas[i][j] + "\t");
            }
            System.out.println();
        }
        for (int i = 0; i < mas.length; i++) {
            int find =-1;
            for (int j = 0; j < mas[i].length; j++) {
                if (mas[i][j] < 0) {
                    find = j;
                    break;
                }
            }
            if (find == -1) {
                System.out.println("No");
            } else {
                System.out.println(find);
            }
        }

    }
}

```
## 4.4 Массивы и методы
Пример
```
import java.util.Random;

public class Main {
    public static void main(String[] args) {
        int[] a = new int[7];
        init(a);
        print(a);
        int[] b = reduce(a,4); //обрезаем до 4-х элементов
        print(b);
}
    public static void init(int[] mas){    // иницилизируем массив
        Random rand = new Random();
        for(int i = 0; i < mas.length; i++){
            mas[i] = rand.nextInt(11);
        }
    }
    public static void print(int[] mas) {      // выводим массив
        for(int i = 0; i < mas.length; i++){
            System.out.print(mas[i] + " ");
        }
        System.out.println();
    }
    public static int[] reduce(int[] mas, int limit){
    if (limit <0 || limit > mas.length) {
            return mas;
    }
    int[] result = new int[limit];//выделяем память под массив
    for (int i = 0; i < limit; i++){//переписываем часть исходно массива
        result[i]=mas[i];
    }
    return result; //возврат ссылки на новый массив
}
}
```
## Задача
Индекс максимума
Напишите три статических метода  для работы с одномерным массивом целых чисел:

1) init()  - заполнение массива случайными числами от -3 до 5;

2) print() - вывод массива на консоль в строку, отделяя элементы пробелами;

3) findMax() - поиск индекса первого максимального элемента в одномерном массиве.

Пользователь вводит количество элементов одномерного массива и начальное значение генератора случайных чисел. 

Выводится на консоль сформированный массив, и затем с новой строки - найденный индекс первого максимального элемента  в массиве.

Код метода main() менять нельзя!

Тестовые данные
Sample Input:

10 15
Sample Output:

0 -1 -2 0 -2 2 2 4 2 -2 
7
## Решения
```
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int[] ar = new int[scan.nextInt()];
        long seed = scan.nextLong();
        init(ar,seed);
        print(ar);
        int ind = findMax(ar);
        System.out.println(ind);

    }
    public static void init(int[] mas, long s){    // иницилизируем массив
        Random rand = new Random(s);
        for(int i = 0; i < mas.length; i++){
            mas[i] = rand.nextInt(-3,6);
        }
    }
    public static void print(int[] mas) {      // выводим массив
        for(int i = 0; i < mas.length; i++){
            System.out.print(mas[i] + " ");
        }
        System.out.println();
    }
    public static int findMax(int[] mas){
        int count = -1, in = 0;
        for (int i = 0; i <mas.length ; i++) {
            if(count<mas[i]){
                in = i;
                count=mas[i];
            }
        }
        return in; //возврат ссылки на новый массив
    }
}
```
**Двумерные массивы и методы**
Ссылка на двумерный массив может быть параметром и результатом метода совершенно  аналогично одномерному массиву.

Пример. В методе insertRow() выполняется вставка новой строки c индексом k в уже существующий массив mas. Строка заполняется нулями. Метод возвращает ссылку на новый массив. При этом возможны два варианта создания нового массива:

1) полностью отдельная копия массива с добавленной строкой. С исходным массивом никакой связи уже не будет:
```
public static int[][] insertRow(int[][] mas, int k) {
        if (k < 0 || k > mas.length) {
            return mas;
        }
        int[][] b = new int[mas.length + 1][mas[0].length];
        for (int i = 0; i < k; i++) { //переписываем все до k-й строки
            for (int j = 0; j < mas[i].length; j++) {
                b[i][j] = mas[i][j];
            }
        }
        for (int i = k; i < mas.length; i++) { //переписываем от k-й строки до конца
            for (int j = 0; j < mas[i].length; j++) {
                b[i + 1][j] = mas[i][j];
            }
        }
        //вставка строки
        b[k] = new int[mas[0].length]; //количество столбцов из любой строки возьмем
        return b;
    }
```
Пример вызова из main():
```
public static void main(String[] args) {
    int[][] a = new int[3][2];
    init(a); //код этих методов
    print(a); //опускаю
    System.out.println();
    int[][] result = insertRow(a,2);
    print(result);
}
```
В итоге в памяти после вызова insertRow() cформируется такая картина:

![alt](/img/oned.png)

2) Создается новый массив ссылок на строки. А массивы - строки используются прежние. Этот способ можно использовать только тогда, когда исходный массив уже не потребуется.
```
public static int[][] insertRow(int[][] mas, int k) {
    if (k < 0 || k > mas.length) {
        return mas;
    }
    int[][] b = new int[mas.length+1][];
    for (int i = 0; i < k; i++) {//переписываем все до k-й строки
        b[i] = mas[i];
    }
    for (int i = k; i < mas.length; i++) { //переписываем от k-й строки до конца
        b[i+1] = mas[i];
    }
    //вставка строки
    b[k] = new int[mas[0].length]; //количество столбцов из любой строки возьмем
    return b;
}
```
В итоге получим в памяти такую картинку:

![alt](/img/twoimg.png)

## Задача
Максимумы в строках
Напишите три статических метода для работы с двумерным массивом:

1) initArray() - инициализирует двумерный массив случайными числами от 0 до 10;

2) printArray() - выводит двумерный массив на консоль в виде таблицы (элементы строках отделяются знаками табуляции, и знак табуляции должен быть в конце каждой строки)

3)  printMaxIndex() - для каждой строки двумерного массива выводит индекс первого максимального элемента. Элементы отделяются пробелами.

В методе main() вводятся три целых числа: количество строк и количество столбцов массива, а затем начальное значение генератора случайных чисел.

Двумерный массив создается и выводится, а затем выводятся индексы максимальных элементов. Код метода main() менять нельзя!

P.S. Желательно при реализации метода printMaxIndex() использовать вызов метода findMax(), который был написан на предыдущем шаге.

Тестовые данные
Sample Input:

3 4 88
Sample Output:

1	10	2	8	
9	8	2	9	
3	2	9	0	

1 0 2 
## Решение
моё
```
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int[][] mas = new int[scan.nextInt()][scan.nextInt()];
        long seed = scan.nextLong();
        initArray(mas, seed);
        printArray(mas);
        System.out.println();
        printMaxIndex(mas);
    }
    public static void initArray(int[][] mas, long a){
        Random rand = new Random(a);
        for (int i = 0; i < mas.length; i++) {
            for (int j = 0; j <mas[i].length ; j++) {
                mas[i][j] = rand.nextInt(0,11);
            }
        }
    }

    public static void printArray(int[][] a){
        for (int i = 0; i <a.length ; i++) {
            for (int j = 0; j <a[i].length ; j++) {
                System.out.print(a[i][j]+ "\t");
            }
            System.out.println();
        }
    }
    public static void printMaxIndex(int[][] a){
        for (int i = 0; i < a.length; i++) {
            System.out.print(findMax(a[i])+" ");
        }
    }

    public static int findMax(int[] mas){
        int count = -1, in = 0;
        for (int i = 0; i <mas.length ; i++) {
            if(count<mas[i]){
                in = i;
                count=mas[i];
            }
        }
        return in; //возврат ссылки на новый массив
    }
}
```
Автора курса
```
import java.util.Scanner;
import java.util.Random;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int[][] mas = new int[scan.nextInt()][scan.nextInt()];
        long seed = scan.nextLong();
        initArray(mas, seed);
        printArray(mas);
        System.out.println();
        printMaxIndex(mas);
    }
   public static void initArray(int[][] a, long seed){
        Random rand = new Random(seed);
        for (int i = 0; i < a.length; i++) {
            for (int j = 0; j < a[i].length; j++) {
                a[i][j] = rand.nextInt(11);
            }
        }
    }
    public static void printArray(int[][] a){
        for (int i = 0; i < a.length; i++) {
            for (int j = 0; j < a[i].length; j++) {
                System.out.print(a[i][j] + "\t");
            }
            System.out.println();
        }

    }
    public static void printMaxIndex(int[][] a){
        for (int i = 0; i < a.length; i++){
            System.out.print(findMax(a[i]) + " ");
        }
    }
    public static int findMax(int[] ar){
        int find = 0;
        for (int i = 1; i < ar.length; i++) {
            if (ar[i] > ar[find]) {
                find = i;
            }
        }
        return find;
    }
}
```

## Задача
Напишите четыре статических метода  для работы с одномерным массивом целых чисел:

1) init()  - заполнение массива случайными числами от -3 до 5;

2) print() - вывод массива на консоль в строку, отделяя элементы пробелами;

3) findMax() - поиск индекса первого максимального элемента в одномерном массиве.

4) reduceAfterMax() - создает новый массив, удаляя все элементы после первого максимума.

Первые три метода уже были созданы на шаге 2.

В main() пользователь вводит количество элементов одномерного массива и начальное значение генератора случайных чисел. 

Выводится на консоль сформированный массив, и затем с новой строки  - сформированный массив с удаленной частью.

Код метода main() менять нельзя!

Тестовые данные
Sample Input:

10 99
Sample Output:

1 2 3 3 0 5 4 5 2 5 
1 2 3 3 0 5 
## Решение
```
import java.util.Arrays;
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int[] ar = new int[scan.nextInt()];
        long seed = scan.nextLong();
        init(ar, seed);
        print(ar);
      int[] b = reduceAfterMax(ar);
       print(b);
    }
    public static void init(int[] mas, long s){    // иницилизируем массив
        Random rand = new Random(s);
        for(int i = 0; i < mas.length; i++){
            mas[i] = rand.nextInt(-3,6);
        }
    }
    public static void print(int[] mas) {      // выводим массив
        for(int i = 0; i < mas.length; i++){
            System.out.print(mas[i] + " ");
        }
        System.out.println();
    }

    public static int[] reduceAfterMax(int[] a){
        int b = findMax(a);
        a = Arrays.copyOf(a,b+1);
        return a;
    }

    public static int findMax(int[] mas){
        int count = -1, in = 0;
        for (int i = 0; i <mas.length ; i++) {
            if(count<mas[i]){
                in = i;
                count=mas[i];
            }
        }
        return in; //возврат ссылки на новый массив
    }
}

```
автора курса 
```
import java.util.Scanner;
import java.util.Random;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int[] ar = new int[scan.nextInt()];
        long seed = scan.nextLong();
        init(ar, seed);
        print(ar);
        int[] b = reduceAfterMax(ar);
        print(b);
    }
   public static void init(int[] ar, long seed){
        Random rand = new Random(seed);
        for (int i = 0; i < ar.length; i++) {
            ar[i] = rand.nextInt(-3, 6);
        }

    }
    public static void print(int[] ar){
        for (int i = 0; i < ar.length; i++) {
            System.out.print(ar[i] + " ");
        }
        System.out.println();
    }
    public static int findMax(int[] ar){
        int find = 0;
        for (int i = 1; i < ar.length; i++) {
            if (ar[i] > ar[find]) {
                find = i;
            }
        }
        return find;
    }
    public static int[] reduceAfterMax(int[] ar) {
        int find = findMax(ar);
        int[] b = new int[find+1];
        for (int i=0; i <= find; i++) {
            b[i] = ar[i];
        }
        return b;
    }
}
```

## Задача
Удаление строк
Напишите три статических метода для работы с двумерным массивом:

1) initArray() - инициализирует двумерный массив случайными числами от 0 до 10;

2) printArray() - выводит двумерный массив на консоль в виде таблицы (элементы строках отделяются знаками табуляции, и знак табуляции должен быть в конце каждой строки)

3)  deleteRow() - создает новый двумерный массив из исходного (первый параметр метода), удаляя строку, индекс которой передается в качестве второго параметра. Если индекс неверный (отрицательный или больше последнего индекса строк), то ничего не происходит.

В методе main() вводятся четыре целых числа: количество строк и количество столбцов массива, начальное значение генератора случайных чисел и номер строки для удаления.

Двумерный массив создается и выводится в виде таблицы. Затем выводится новый массив. Код метода main() менять нельзя!

Тестовые данные
Sample Input:

4 3 77 2
Sample Output:

9	6	7	
9	4	2	
6	5	5	
6	0	9	

9	6	7	
9	4	2	
6	0	9
## Решение
```
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
       Scanner scan = new Scanner(System.in);
        int[][] mas = new int[scan.nextInt()][scan.nextInt()];
        long seed = scan.nextLong();
        int ind = scan.nextInt();
        initArray(mas, seed);
        printArray(mas);
        System.out.println();
        mas = deleteRow(mas, ind);
        printArray(mas);
    }
   public static int[][] deleteRow(int[][] a, int ind){
        if (ind < 0 || ind >= a.length){
            return a;
        }
        int[][] b = new int[a.length-1][];
        //первая версия - когда старый массив сохранять не нужно
//        for (int i = 0; i < ind; i++) { //переписываем ссылки до удаляемой строки
//            b[i] = a[i];
//        }
//        for (int i = ind + 1; i < a.length; i++) { //переписываем ссылки после удаляемой строки
//            b[i - 1] = a[i];
//        }
        //вторая версия - когда старый массив не должен измениться, 
        // копируем все элементы
        for (int i = 0; i < ind; i++) { 
            b[i] = new int[a[i].length];
            for(int j = 0; j < a[i].length; j++) {
                b[i][j] = a[i][j];
            }
        }
        for (int i = ind + 1; i < a.length; i++) {
            b[i-1] = new int[a[i].length];
            for (int j = 0; j < a[i].length; j++) {
                b[i-1][j] = a[i][j];
            }
        }
        return b;
    }
    public static void initArray(int[][] a, long seed){
        Random rand = new Random(seed);
        for( int i = 0; i < a.length; i++) {
            for (int j = 0; j < a[i].length; j++) {
                a[i][j] = rand.nextInt(11);
            }
        }
    }
    public static void printArray(int[][] a){
        for( int i = 0; i < a.length; i++) {
            for (int j = 0; j < a[i].length; j++) {
                System.out.print(a[i][j] + "\t");
            }
            System.out.println();
        }

    }
}
```

## 5.1 Класс String

Класс String
Любая символьная строка (в том числе и строковый литерал) по умолчанию является объектом класса String. Например, в следующем операторе: 
```
System.out.println("I love Java"); 
```
символьная строка "I love Java" является объектом класса String.

Объекты класса String являются неизменяемыми после их создания. Но всегда можно создать новую символьную строку, которая содержит нужные изменения. Кроме того, в Java определены  другие классы (StringBuffer и StringBuilder), которые допускают изменение символьных строк.

Класс String входит в пакет java.lang, который подключается в любую java-программу по умолчанию. Поэтому его не нужно импортировать.

String -  ссылочный тип. Описание String st; создает в стековой памяти переменную для хранения ссылки на объект-строку. А сам объект (который будет размещен в динамической памяти) еще не создан. Рассмотрим различные способы создания объекта-строки.

Создание строк
1)    Инициализировать строку строковым литералом:
```
String myString = "Это тестовая строка";
```
2)    Можно также воспользоваться операцией new:
```
String s = new String(); //создание пустой строки
String name = new String("Вася");
```
3)    Создать строку на основе массива символов:
```
char chars[] = {'a', 'b', 'c'};
String s2 = new String(chars);
System.out.println(s2); //выводит abc
```
4)    Создать строку на основе части массива символов:
```
String(char chars[], int начальныйИндекс, int числоСимволов);
```
Пример:
```
char chars2[] = {'a', 'b', 'c', 'd', 'e', 'f'};
String s3 = new String(chars2, 2, 3);
System.out.println(s3); //выводит cde
```
5)    Создать строку с указанием кодировки (если пока не понимаете этот код, просто пропустите - исключения мы изучим в следующем курсе)
```
try{
    String s5 = new String(s3.getBytes(), "UTF-8");
    System.out.println(s5);
}catch(UnsupportedEncodingException exc){
    System.out.println("Кодировка не поддерживается");
}
```
Для объектов класса  String определена одна операция: +, предназначенная для сцепления (конкатенации) двух символьных строк. Например, в результате приведенной ниже операции переменной str присваивается символьная строка "Мне нравится Java." .
```
String str = "Мне " + "нравится " + "Java.";
```
Статические методы класса String
static String valueOf(значение) — преобразование переменной базового типа к строке;
 String str = String.valueOf(0.5);
static String format(String format, Object… args)— генерирует форматированную строку. Используемые спецификаторы форматирования в целом аналогичны спецификаторам в языке С++. Такое же форматирование выполняется и при использовании метода printf() (https://stepik.org/edit-lesson/813895/step/1) Имеется  ряд удобных спецификаторов для преобразования времени и даты. Подробнее про спецификаторы форматирования можно прочесть здесь: https://docs.oracle.com/javase/7/docs/api/java/util/Formatter.html
```
String result = String.format("Жили у бабуси %d веселых гуся", 2);
System.out.println(result);
double x = 3.1415;
String out = String.format("x=%6.3f", x);
System.out.println(out);
```
Сравнение строк
Переменная типа String имеет ссылочный тип. Поэтому операция сравнения (==) двух переменных типа String вернет true только в том случае, если эти ссылки указывают на один и тот же объект.

При создании строки операцией new каждому создаваемому объекту String выделяется своя область памяти в куче. Переменные типа String получают в качестве значения разные ссылки, и результат их сравнения (==) будет false.
```
String s3 = new String("Ivan");
String s4 = new String("Ivan");
System.out.println(s3 == s4); // false
```
 Для сравнения содержимого строк следует использовать метод equals(), который для строк из примера выше вернет true:
```
System.out.println(s3.equals(s4)); // true
```
Если нужно сравнивать строки на больше-меньше, то используется метод 
```
int compareTo(String s)
```
Метод вызывается от имени одной из сравниваемых строк, а вторая строка передается ему в качестве параметра. Если первая строка больше, то метод возвращает положительное число, если она меньше, то отрицательное число, и 0 - если строки равны.

Сравнение строк выполняется в лексикографическом порядке. Сравниваются первые символы обоих строк. Если код символа больше, то вся строка считается больше. Если символы одинаковые, то далее сравниваются вторые символы строк, и т.д. Если одна строка закончится раньше другой (при одинаковых символах), то она считается меньше.
```
String ss3 = new String("Ivan");
String ss5=new String("Petr");
if(ss3.compareTo(ss5) > 0){
      System.out.println("Первая строка больше");
}else if(ss3.compareTo(ss5) < 0){
      System.out.println("Первая строка меньше"); //будет этот вывод
}else{
      System.out.println("Строки равны");
}
```
## задача
Введите три строки (могут содержать пробелы). Выведите их в порядке возрастания. 

Тестовые данные
Sample Input:

Hello, world!
Hello, sky!
By-by, baby!
Sample Output:

By-by, baby!
Hello, sky!
Hello, world!
## решение
моё
```
import java.util.Arrays;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String[] a = new String[3];
        for (int i = 0; i < a.length ; i++) {
            a[i] = sc.nextLine();
        }
        Arrays.sort(a);
        for (int i = 0; i < a.length ; i++) {
            System.out.println(a[i]);
        }
    }
}
```
автора
```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String str1 = scan.nextLine();
        String str2 = scan.nextLine();
        String str3 = scan.nextLine();
        if (str1.compareTo(str2) > 0) {
            String tmp = str1;
            str1 = str2;
            str2 = tmp;
        }
        if (str2.compareTo(str3) > 0) {
            String tmp = str2;
            str2 = str3;
            str3 = tmp;
        }
        if (str1.compareTo(str2) > 0) {
            String tmp = str1;
            str1 = str2;
            str2 = tmp;
        }
        System.out.println(str1);
        System.out.println(str2);
        System.out.println(str3);

    }
}
```
## 5.1 Класс String
 Методы экземпляра класса String:
String concat(String s) (аналог «+») — слияние строк;
boolean equals(Object ob) — сравнение строк с учетом регистра;
boolean equalsIgnoreCase(String s) — сравнение строк без учета регистра;
int compareTo(String s) и compareToIgnoreCase(String s) — лексикографическое сравнение строк с учетом и без учета их регистра. Метод осуществляет вычитание кодов первых различных символов вызывающей и передаваемой в метод строки и возвращает целое значение. Метод возвращает значение нуль в случае, когда equals() возвращает значение true;
boolean contentEquals(StringBuffer ob) — сравнение строки и содержимого объекта типа StringBuffer;
String substring(int n, int m) — извлечение из строки подстроки начиная с индекса n и заканчивая индексом m (не включая). Нумерация символов в строке начинается с нуля;
String substring(int n) — извлечение из строки подстроки, начиная с позиции n до конца строки;
int length() — определение длины строки;
int indexOf(char ch)— определение позиции символа  в строке. Возвращает индекс первого появления символа, либо -1, если символ не обнаружен. Аналогично перегруженный метод int indexOf(String str)  поиска индекса начала подстроки str.
int indexOf(char ch, int n), int indexOf(String str, int n) — определение позиции символа  или подстроки, поиск вправо начинается с позиции n. Возвращает -1, если символ/подстрока не обнаружен;
int lastIndexOf(char ch), int lastIndexOf(String str) — определение последней позиции символа или подстроки. Возвращает -1, если символ/подстрока не обнаружен;
int lastIndexOf(char ch, int n), int lastIndexOf(String str, int n) — определение позиции символа  или подстроки, поиск влево начинается с позиции n. Возвращает -1, если символ/подстрока не обнаружен;
String toUpperCase()/toLowerCase() — преобразование всех символов вызывающей строки в верхний/нижний регистр;
String replace(char с1, char с2) — замена в строке всех вхождений первого символа вторым символом. Есть перегрузка этого метода для замены одной подстроки другой:: String replace(String str1, String str2)
String intern() — заносит строку в «пул» литералов и возвращает ее объектную ссылку. Пример использования этого метода показан далее.
String trim() — удаление всех пробелов в начале и конце строки;
char charAt(int position) — возвращение символа из указанной позиции (нумерация с нуля);
boolean isEmpty() — возвращает true, если длина строки равна 0 (пустая строка);
void getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin) — извлечение символов строки от символа с индексом srcBegin до символа с индексом srcEnd  (не включая) в массив символов dst , размещение в котором начинается с индекса dstBegin;
String[] split(String regex) — поиск вхождения в строку заданного регулярного выражения (разделителя) и деление исходной строки в соответствии с этим на массив строк.
String[] split(String regex, int limit) — деление исходной строки на массив строк, используя разделитель regex (регулярное выражение). Параметр limit означает максимальное количество строк, которое должно быть получено.
Поскольку литерал является объектом класса String, от его имени можно вызывать все эти методы. 
```
System.out.println("abc".length()); //будет выведено 3
```
Во всех случаях вызова методов, изменяющих строку, создается новый объект типа String. Сохранить произведенные изменения можно только с применением оператора присваивания, т. е. установкой ссылки на вновь созданный объект.
```
import java.util.Scanner;
public class Runner10 {
    public static void main(String[] args) {
        String sample="   Testing strings   ";
        sample = sample.trim(); //удаление пробелов в начале и в конце
        System.out.println("|"+sample+"|");
        System.out.println(sample.charAt(3)); //символ с индексом 3 - это t
        System.out.println(sample.charAt(sample.length() - 1)); //последний символ - это s
        String sub = sample.substring(3, 7); //выделение подстроки ting
        System.out.println(sub);
        String changed = sample.replace('s', 'z'); //замена символов s на z
        System.out.println(changed);
        changed = changed.replace("z", ""); //удаление символов z
        System.out.println(changed);
        int findFirst = sample.indexOf('i'); //поиск символа с начала строки
        System.out.println(findFirst); //выводит 4
        int findLast = sample.lastIndexOf('i'); //поиск символа с конца строки
        System.out.println(findLast); //выводит 11
    }
}
```
 Особенности создания строковых литералов
При создании строковых литералов они все размещаются в специальном месте динамической памяти, называемом “пул строк”. При первом упоминании строкового литерала в программе создается новый объект класса String в пуле строк. При повторном использовании этого же литерала новый объект не создается, а переменной присваивается ссылка на ранее созданный объект.

Это правило работает и в случае, если литерал является вычисляемым. То есть компилятор воспринимает литералы "Java" и "J" + "ava" как эквивалентные.
```
public class Example2 {
    public static void main(String[] args) {
        String s1 = "Ivan";
        String s2 = "Ivan";
        String s3 = new String("Ivan");
        String s4 = new String(s1);
        System.out.println(s1 == s2); // true
        System.out.println(s3 == s4); // false
        System.out.println(s1 == s3); // false
        System.out.println(s1.equals(s2)); //true
        System.out.println(s1.equals(s3)); // true
    }
}
```
Первые три вызова println() выводят результат сравнения ссылок, а последние два – сравнение содержимого объектов. Очевидно, что содержимое всех объектов будет одинаковое, поэтому в двух последних случаях выводится true.

 Ссылки s1 и s2 будут равны по следующей причине. При инициализации s2 просматривается пул литералов. Поскольку в нем уже находится соответствующий литерал (он был туда помещен при инициализации s1), то новый литерал не создается, а s2 получает ссылку на уже существующий литерал (т.е. такую же ссылку, как и s1).

При создании s3 происходит вызов конструктора, т. е. выделение памяти происходит раньше инициализации, и в этом случае в куче создается новый объект. Аналогично новый объект создается при создании s4. Схема распределения памяти показана на рисунке:

   ![alt](/img/adasd%D0%B0%D0%BD%D0%B8%D1%8E.png)

Существует возможность сэкономить память и переопределить ссылку с объекта на литерал при помощи вызова метода intern():
```
s3 = s3.intern();
//после этого
System.out.println(s1 == s3); // true
```
Вызов метода intern() организует поиск в «пуле литералов» соответствующего значению объекта s3 элемента, и при положительном результате возвращает ссылку на найденный литерал, а при отрицательном — заносит значение в пул и возвращает ссылку на него. Результат выполнения проиллюстрирован на рисунке:

![alt](/img/dasdasdrn().png)


## задача
Введите строку (в ней возможны пробелы). Замените в ней каждый символ «;»   на пару символов «.,»

Тестовые данные
Sample Input:

hello;; by!; ;;
Sample Output:

hello.,., by!., .,.,
## решение
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        s = s.replace(";",".,");
        System.out.println(s);
    }
}
```

## задача
Пользователь вводит три строки, которые содержат части кодового слова. Каждая вводимая строка может содержать пробелы и заканчивается символом перехода на новую строку ('\n').

Части кодового слова выделены внутри строки знаками ';'. Нужно соединить эти части в одну строку и вывести эту строку на консоль. 

Замечание: поскольку предполагается, что кодовое слово будет как-то использовано в дальнейшем, недостаточно его просто вывести на консоль по частям. Нужно именно сформировать его в виде одной строки, а затем уже выводить!

Тестовые данные
Sample Input:

To be or ;not; to be?
tes;ting; is good
I like ;ham; more then eggs
Sample Output:

nottingham
## решение
```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.nextLine(), b = sc.nextLine(), c = sc.nextLine();
        a = a.substring((a.indexOf(";")+1),a.lastIndexOf(";"));
        b = b.substring((b.indexOf(";")+1),b.lastIndexOf(";"));
        c = c.substring((c.indexOf(";")+1),c.lastIndexOf(";"));
        System.out.println(a+b+c);
    }
    }

```

## задача
Напишите метод, который проверяет, что строка является адресом почты gmail.com (т.е. в конце строки "@gmail.com", и знак @ только один).

Метод main()  менять нельзя!

Тестовые данные
Sample Input 1:

petr.ivanov@gmail.com
Sample Output 1:

YES
Sample Input 2:

ivanov@petr@gmail.com
Sample Output 2:

NO
## решение
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String str = scan.nextLine();
        if (isGMailAddress(str)) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }
    }

    public static boolean isGMailAddress(String a) {
        String b;
        b = a.substring(a.length()-10,a.length());
        if (a.contains("@gmail.com") && b.equals("@gmail.com")) {
            int count = 0;
            for (int i = 0; i < a.length(); i++) {
                if (a.charAt(i) == (char) 64) {
                    count++;
                }
            }
            if (count == 1) {
                return true;
            } else {
                return false;
            }
        } else {
            return false;
        }
    }
    }

```

## задача
Напишите статический метод, который проверяет, есть ли в конце строки подстрока ".com". Если да, то он возвращает часть строки без этого фрагмента. Если нет, то он возвращает строку без изменения.

Тестовые данные
Sample Input 1:

intel.com.think.com
Sample Output 1:

intel.com.think
Sample Input 2:

stepik.org
Sample Output 2:

stepik.org
## решение
```
import java.util.Scanner;

class Main {
        public static void main(String[] args) {
            Scanner scan = new Scanner(System.in);
            String str = scan.nextLine();
            System.out.println(delCom(str));
        }

        public static String delCom(String a) {
        String b;
        b = a.substring(a.length()-4,a.length());
        if (a.contains(".com") && b.equals(".com")) {
        a = a.substring(0,a.length()-4);
        return a;
        } else {
            return a;
        }
    }
    }

```
**Пример** решения задачи.
Пользователь вводит строку,  состоящую из слов, разделенных одним или несколькими пробелами.  Пробелы могут быть также в начале и в конце слова.

Сформируйте новую строку, в которой слова исходной строки разделены ровно одним пробелом. Пробелы в начале и в конце слова тоже должны быть удалены. Для проверки этого выведите строку, обрамленную "палочками".
```
import java.util.Scanner;

public class Example4 {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String str = scan.nextLine();
        str=str.trim(); //удаляем пробелы в начале и в конце
        String[] words = str.split(" +"); //формируем массив слов без пробелов
        String result = ""; //создаем пустую строку
        for(String word:words){ //перебираем слова в массиве строк
            result += word; //присоединяем очередное слово к итоговой строке
            result += " "; //добавляем один пробел
        }
        //получился лишний пробел в конце, удаляем его:
        result = result.trim();
        System.out.println("|"+result+"|");
    }
}
```

## задача
Ввести строку из слов, разделенных пробелами. Между словами может быть любое количество пробелов. Также пробелы могут быть перед первым и после последнего слова.

Найти и распечатать первое слово максимальной длины.

Тестовые данные
Sample Input:

   Свиристелки прилетели     и    запели в унисон   
Sample Output:

Свиристелки
## решение
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String str = scan.nextLine();
        str=str.trim(); //удаляем пробелы в начале и в конце
        String[] words = str.split(" +"); //формируем массив слов без пробелов
        int result = 0; //создаем пустую строку
        int ind = 0;
        for (int i = 0; i < words.length; i++) {
            if(result<words[i].length()){
                result = words[i].length();
                ind = i;
            }
        }
        System.out.println(words[ind]);
        }
}
```
Автор курса
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String str = scan.nextLine();
        str = str.trim(); //удаляем пробелы в начале и в конце
        String[] words = str.split(" +"); //формируем массив слов без пробелов
        int imax = 0; //индекс слова макс длины
        for (int i = 0; i < words.length; i++) { //перебираем слова в массиве строк
            if (words[i].length() > words[imax].length()) {
                imax = i;
            }
        }
        System.out.println(words[imax]);
    }
}
```

## задача
Ввести текст из слов, разделенных пробелами. Между словами может быть любое количество пробелов. Также пробелы могут быть перед первым и после последнего слова.

Также ввести контрольное слово.

Удалить из текста все появления данного слова (но не как части другого слова!)

Также удалить все лишние пробелы между словами и в начале и в конце строки.

Тестовые данные
Sample Input:

A good    dog deserves a    good bone or goodness
good
Sample Output:

A dog deserves a bone or goodness
## решение
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String text = scan.nextLine();
        String word = scan.next();
        text = text.trim();
        String[] words = text.split(" +"); //нужно группировать пробелы
        String result = "";
        for (String item:words) {
            if (!item.equals(word)) {
                result += item;
                result += " ";
            }
        }
        result = result.trim();
        System.out.println(result);
    }
}
```

## задача
Введите строку, состоящую из слов, отделенных ровно одним пробелом.

Замените первую букву каждого слова на прописную. Выведите полученную строку.

Тестовые данные
Sample Input:

one apple a day keeps a doctor away
Sample Output:

One Apple A Day Keeps A Doctor Away
## решение
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String str = scan.nextLine();
        str=str.trim(); //удаляем пробелы в начале и в конце
        String[] words = str.split(" "); //формируем массив слов без пробелов
        for (int i = 0; i < words.length; i++) {
            String s = words[i].substring(0,1).toUpperCase() + words[i].substring(1);
            System.out.print(s+" ");
        }
    }
}
```

## 5.2 Классы StringBuffer и StringBuilder

**Классы  StringBuffer и  StringBuilder**
Классы StringBuilder и StringBuffer по своему предназначению близки к классу String. При этом содержимое и размеры объектов классов StringBuilder и StringBuffer можно изменять.

Основное отличие этих классов связано с использованием в многопоточных приложениях. StringBuffer обеспечивает потоко -безопасность, а StringBuilder – нет. При этом класс StringBuilder  дает более высокую скорость обработки. Его следует применять, если многопоточность не используется.

Рассмотрим более подробно класс StringBuilder (класс StringBuffer полностью аналогичен).

Объект класса  StringBuilder нельзя создавать с помощью строковых литералов, только с помощью операции new.
```
//StringBuilder sb = "test"; //ошибка
StringBuilder sb1 = new StringBuilder("test");
```
В конструктор класса StringBuilder можно передать объект класса String, другой объект StringBuilder, а также целое число, которое означает емкость буфера символов.

Дело в том, что "внутри" класса StringBuilder находится массив символов, который по мере необходимости автоматически увеличивается в размере. Количество зарезервированных под символы мест называется емкостью (capacity). Емкость всегда выделяется с некоторым запасом. Если создается StringBuilder конструктором по умолчанию (без параметров), то обычно резервируется емкость в 16 символов. 
```
StringBuilder sb2 = new StringBuilder(); //по умолчанию емкость 16
StringBuilder sb3 = new StringBuilder(50); //емкость 50
StringBuilder sb4 = new StringBuilder(sb1); //на основе другого StringBuilder
```
Объекты классов StringBuilder и String можно преобразовывать друг в друга.
```
String str = sb1.toString(); //преобразование в строку
StringBuilder sb5 = new StringBuilder(str); //преобразование в StringBuilder
```
Текущую емкость объекта StringBuilder можно получить методом int capacity(), а текущую длину, т.е. фактическое количество символов - методом int length()
```
StringBuilder sb1 = new StringBuilder("test");
System.out.println(sb1.capacity()); // выводит 20
System.out.println(sb1.length()); //выводит 4
```
Изменить минимальную емкость объекта StringBuilder можно методом 
```
void ensureCapacity(int minimum). При этом это именно минимальная емкость, а текущая емкость может оказаться и больше.
```
```
StringBuilder sb2 = new StringBuilder(); //по умолчанию емкость 16 
System.out.println(sb2.capacity()); //выводит 16
sb2.ensureCapacity(32);
System.out.println(sb2.capacity()); //выводит 34
```
Текущую длину строки тоже можно изменить методом void setLength(int length). Однако с этим методом нужно быть очень осторожным. Если существующая длина строки больше указанной в методе, то он обрежет строку до нужного размера. А если текущая длина строки меньше заданной - то дополнит непечатаемыми символами.
```
StringBuilder sb1 = new StringBuilder("test");
sb1.setLength(20);
System.out.println(sb1);
Выведется: 
```


 **Сравнение объектов StringBuilder**
Для класса StringBuilder не переопределен метод equals(), т. е. сравнить его помощью содержимое двух объектов невозможно. При идентичном содержимом размеры буфера каждого могут отличаться, поэтому их сравнение на равенство будет неоднозначным. Метод equals() в классе StringBuilder есть (он есть в любом классе), но он сравнивает сами ссылочные переменные, т.е. его использование ничем не будет отличаться от проверки на равенство:
```
StringBuilder s1 = new StringBuilder("Java");
StringBuilder s2 = new StringBuilder("Java");
System.out.println( s1 == s2); //false, т.к. разные ссылочные переменные
System.out.println(s1.equals(s2)); //тоже false, т.к. метод equals()
//также сравнивает ссылочные переменные
s2 = s1; //ссылки теперь одинаковые
System.out.println(s1 == s2); //true
System.out.println(s1.equals(s2)); //true
```
Как же проверить на равенство содержимое двух объектов StringBuilder ??  Для этого можно один из них преобразовать в строку  методом  toString(), а затем использовать метод  contentEquals() класса String для проверки на равенство содержимого строки и второго объекта StringBuilder:
```
StringBuffer s1 = new StringBuffer("Java");
StringBuffer s2 = new StringBuffer("Java");
System.out.println(str1.toString().contentEquals(str2)); //true
```
Что касается метода compareTo() в классе StringBuilder, то он работает так, как ожидается. Поэтому  для объектов s1 и s2 из предыдущего примера результат этого метода будет 0:
```
System.out.println(s1.compareTo(s2)==0); //true
```
Также существование метода compareTo() означает, что объекты StringBuilder можно сортировать:
```
StringBuilder[] list = {new StringBuilder("Tom"), new StringBuilder("Andrew"),
         new StringBuilder("Max")};
Arrays.sort(list);
for (int i = 0; i < list.length; i++) {
    System.out.print(list[i] + " ");
}
Выводится:  Andrew Max Tom 
```
**Методы класса**  **StringBuilder**
Методы этого класса изменяют сам объект StringBuilder, а не создают новый!

StringBuilder append(String str) — добавление к содержимому объекта строкового представления аргумента. Возвращает ссылку на этот же объект. Параметром может быть не только строка, но и значение любого другого типа, который автоматически преобразуется в строку
```
StringBuilder sb = new StringBuilder("test"); // создание объекта
sb.append('-').append("test"); // добавление значений цепочкой
sb.append(1); // добавление строки, полученную преобр.-ем числа
System.out.println(sb);
Результат: test-test1
```

Обратите внимание, что ссылочной переменной sb не нужно ничего присваивать (как мы делали в случае с классом String)!
```
StringBuilder insert(int offset, String str) — вставка символа, объекта или строки в указанную позицию;
StringBuilder sbb = new StringBuilder("I java!");
sbb.insert(2, "love "); // 2 - индекс символа,
// начиная с которого будет вставлена строк
sbb.insert(0,100);
sbb.insert(3,"% ");
System.out.println(sbb.toString());
Результат:     100% I love java!
```
```
StringBuilder deleteCharAt(int index) — удаление символа;
StringBuider delete(int start, int end) — удаление подстроки от индекса start до индекса end (не включая);
StringBuilder phrases = new StringBuilder("I do not like java!");
phrases.delete(2, 9);
System.out.println(phrases);
Результат: I like java!
```
```
StringBuilder reverse() — изменение порядка символов на обратный.
StringBuilder st = new StringBuilder("palindrome");
st.reverse();
System.out.println(st);
Результат: emordnilap
```
В классе StringBuilder присутствуют также методы, аналогичные методам класса String, такие как replace(), substring(), charAt(), length(), getChars(), indexOf() и др.

Есть некоторые особенности использования этих методов, в отличие от класса String. Например, в метод indexOf() нельзя передать символ, а только строку:
```
StringBuilder test = new StringBuilder("abracadabra");
//int ind = test.indexOf('c'); //ошибка
int ind = test.indexOf("c");
System.out.println(ind); //выводит 4
```
Другой пример - метод substring() возвращает не StringBuilder (как можно было бы подумать), а String:
```
//StringBuilder tt = test.substring(4,9); //ошибка
String tt = test.substring(4,9);
System.out.println(tt); //ввводит cadab
```
А метод replace() вообще работает по-другому: 
```
StringBuilder test = new StringBuilder("abracadabra");
test.replace(2,5,"XX"); //с индекса 2 по 4 включительно
//заменяется на XX
System.out.println(test); //выводит abXXadabra
```
Таким образом, при использовании этих методов нужно обращаться к документации, либо пользоваться подсказками, которые дает Intellij Idea!

Если в цикле  мы делаем конкатенацию строк  типа  String  операцией + , то это может привести к проблемам с производительностью. Ведь постоянно создаются новые строки, а старые какое-то время занимают память (пока их не уберет сборщик мусора).  В такой ситуации предпочтительнее использовать объект класса StringBuilder.

Пример. С консоли вводится строка, содержащая несколько слов, разделенных пробелами. Пробелы могут быть также перед первым и после последнего слова. Нужно удалить лишние пробелы в начале и в конце строки, а между словами оставить ровно один пробел.
```
import java.util.Scanner;

public class Example5 {
    public static void main(String[] args) {
        String data;
        System.out.println("Введите исходную строку");
        Scanner scan = new Scanner(System.in);
        data = scan.nextLine();
        data = data.trim();//удаление пробелов в начале и в конце
        String[] words = data.split(" +"); //разделение на слова
        // собрать из слов строку с одним пробелом между
        StringBuilder sb = new StringBuilder(words[0]);
        for(int i = 1; i < words.length; i++) {
            sb.append(" ").append(words[i]);
        }
        System.out.println("|" + sb.toString() + "|");// можно просто sb -
        // преобразование в строку будет автоматически
    }
}
```
И последнее, что хотелось бы упомянуть: с осторожностью используйте ссылочные переменные типа StringBuilder, которые указывают на один и тот же объект! Ведь  если Вы изменяете этот объект, пользуясь одной ссылкой, то результат получаете и по другой ссылке  тоже:
```
StringBuilder ex1 = new StringBuilder("Java");
StringBuilder ex2 = ex1;
ex2.append(" International");
System.out.println(ex1); //выводит Java International
```
## задачка
Пользователь вводит строку из слов, разделенных пробелами.  Заменить все слова, которые содержат букву z на слово "ERROR". Также удалить все лишние пробелы в начале и в конце строки. Между словами оставить ровно один пробел. 

Тестовые данные
Sample Input:

   mama   zlobno   myla    puzzle  and    ramy   
Sample Output:

mama ERROR myla ERROR and ramy
## решение
```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        String data;
        Scanner scan = new Scanner(System.in);
        data = scan.nextLine();
        data = data.trim();//удаление пробелов в начале и в конце
        String[] words = data.split(" +"); //разделение на слова
        // собрать из слов строку с одним пробелом между
        StringBuilder sb = new StringBuilder(words[0]);
        for(int i = 1; i < words.length; i++) {
            if (words[i].contains("z")){
                sb.append(" ").append("ERROR");
            } else {
                sb.append(" ").append(words[i]);
            }
        }
        System.out.println(sb.toString().trim());// можно просто sb -
        // преобразование в строку будет автоматически
    }
}
```
автора
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String str = scan.nextLine();
        String[] words = str.split(" +");
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < words.length; i++) {
            if (words[i].indexOf('z') != -1) {
                sb.append(" ERROR");
            } else {
                sb.append(" ").append(words[i]);
            }
        }
        System.out.println(sb);

    }
}
```
## задачка
Пользователь вводит строку из слов, разделенных одним пробелом. Переставить слова местами так, чтобы каждое следующее слово начиналось с буквы, которой заканчивается предыдущее слово (существование такого слова в тестах гарантируется).

Тестовые данные
Sample Input:

trolli emodji road tiger dog insert game
Sample Output:

trolli insert tiger road dog game emodji
## решение
автора
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String str = scan.nextLine();
        String[] words = str.split(" +");
        StringBuilder sb = new StringBuilder(words[0]);
        for (int i = 1; i < words.length; i++) {
            char simb = sb.charAt(sb.length() - 1);
            for (int j = 1; j < words.length; j++) {
                if(words[j].charAt(0) == simb){
                    sb.append(" ").append(words[j]);
                    break;
                }
            }
         }
         System.out.println(sb);
    }
}
```

## задачка
Напишите метод primer(), который принимает два целых числа и возвращает строку, представляющую собой пример на сложение (см. тест). Используйте для формирования результата StringBuilder!

Исходный код метода main менять нельзя!

Тестовые данные
Sample Input:

8 11
Sample Output:

8 + 11 = 19
## решение

```
import java.util.Scanner;

    class Testing {
        public static void main(String[] args) {
            Scanner scan = new Scanner(System.in);
            int a = scan.nextInt();
            int b = scan.nextInt();
            String str = primer(a, b);
            System.out.println(str);
        }
        public static String primer(int a, int b){
            StringBuilder q = new StringBuilder();
            q.append(a).append(" + ").append(b).append(" = ").append(a+b);
            String s = q.toString();
            return s;
        }
}
```

## задачка
Пользователь вводит строку, в которой среди других символов содержатся символы цифр. Сформируйте строку, которая "представляет" сумму этих цифр. Выведите полученную строку на консоль. 

Если в исходной строке цифр нет, то должно быть выведено ERROR.

Р.S.  Преобразовать символ в число можно вычитанием кода символа '0'

Тестовые данные
Sample Input:

ab34c#5i02k tolkien25
Sample Output:

3+4+5+0+2+2+5=21
## решение
моё
```
import java.util.Arrays;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();
        StringBuilder myNumbers = new StringBuilder();
        int count = 0;
        for (int i = 0; i < str.length(); i++) {
            if (Character.isDigit(str.charAt(i))) {
                myNumbers.append(str.charAt(i));
            }
        }
        if (myNumbers.isEmpty()) {
            System.out.println("ERROR");
        } else {
            String my = myNumbers.toString();
            String[] arr = my.split("");
            StringBuilder alfa = new StringBuilder();
            for (int i = 0; i < arr.length; i++) {
                int j = myNumbers.length() - 1;
                count += Integer.parseInt(arr[i]);
                if (j == i) {
                    alfa.append(arr[i]);
                } else {
                    alfa.append(arr[i]).append("+");
                }
            }

            alfa.append("=").append(count);

            System.out.println(alfa);
        }
    }
}
```

автора
```
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String str = scan.nextLine();
        StringBuilder result = new StringBuilder();
        int summa = 0;
        for (int i = 0; i < str.length(); i++) {
            if (str.charAt(i) >= '0' &&  str.charAt(i) <= '9'){
                summa += str.charAt(i) - '0';
                result.append(str.charAt(i)).append('+');
            }
        }
        if (!result.isEmpty()) {
            result.replace(result.length() - 1, result.length(), "=");
            result.append(summa);
            System.out.println(result);
        } else {
            System.out.println("ERROR");
        }
    }

}
```
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

### 2.2 Операторы цикла


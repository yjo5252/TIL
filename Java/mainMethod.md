# main keywords Questions


* override / overload 
* static 한 경우에 다른 클래스에서 그 문자를 사용하면 어떤 결과가 나오나?
* private한 변수를 set과 get 그리고 생성자를 만드는 것으로 관리 가능한가? 
* DecimalFormat 클래스 / df.format(변수)
* class를 선언, 생성, 변수, 생성자, 메소드 
* static 변수? 클래스?
* abstract 추상 메소드로 추상 클래스 내에서 선언할 수 있다. + 상속
* final 변수 메소드는 서브 클래스에서 overriding 될 수 없다. + 상속
* synchronized 스레드를 동기화할 수 있는 기법을 위해 사용 + 다중스레드 

* 라이브러리 클래스의 함수 / 인자 
* 예상문제 / 연습문제 


# IO 
## 출력 
### System.out 
* System.out.println();
* System.out.printf("%d", n);
    * 실수형, 문자형 자료 출력 가능 

### StringBuilder 
* 출력해야 하는 것이 많은 경우에는, 매번 출력하는 것보다 <b> StringBuilder를 이용해 문자열을 만들고 한번에 출력</b>하는 것이 속도면에서 좋다. 
```java
// 수행시간 3X, 메모리 3Y
import java.util.Scanner;

puglic class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        for (int i = 1; i <= a; i++)
            System.out.prinln(i);    
    }
}
```

``` java
// 수행시간 X, 메모리 Y
import java.util.Scanner;

public class Main{
    public static void main(String[] args). {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        StringBuilder sb = new StringBuilder();
        for (int i = 1; i <= a; i++)
            sb.append(i + "\n");
        System.out.println(sb);
    } 
}
```

## 입력 
### Scanner 
* next[자료형]을 이용해서 입력을 받을 수 있고,
* hasNex[자료형]을 이용해서 입력할 수 있는 자료형이 있는지 구할 수 있다. 
* 두 수 입력 
```java
public class Main{
    public static void main(String[] args) }{
        Scanner scanner = new Scanner(System.in);
        int a, b;
        a = scanner.nextInt();
        b = scanner.nextInt();
        System.out.println(a + b); 
    }
}
```
* 입력에서 정수가 주어지는 동안 계속 입력 받음 
```java
public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int sum = 0;
        while(scanner.hasNextInt()){
            sum += scanner.nextInt();
        }
        System.out.println(sum);
    }
}
```
* <b>정수와 문자열을 동시에 처리 </b>
    * 1의 뒤에 줄바꿈 \n이 존재하기 때문에, 줄바꿈을 읽어들여 hi를 읽지 못한다. 
    * 따라서, nextLine()으로 다음 문장을 읽기 전에, scanner.NextLine(); 줄바꿈을 입력받는 코드를 한 줄 작성해야 올바른 의도대로 코딩을 할 수 있다. 
```
<입력> 
1
hi
```
``` java
public class Min{
  public static void main(String[] args){
      Scanner sc = new Scanner(System.in);
      int n = sc.nextInt();
      sc.nextLine();
      String s = sc.nextLine();
      System.out.pringln(n + "\n" + s);
  }
}
```

## BufferedReader
* Scanner는 매우 편리하지만 속도가 느리기 때문에, 많이 받아야 하는 경우에는 BufferedReader를 사용하는 것이 훨씬 좋다. 
* bufferedReader에서는 read와 readLine만 있기 때문에 정수는 파싱을 해야한다. 
```java
public class Main {
    public static void main(String[] args) throws IOException{
        BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
        String[] line = bf.readLine().split(" ");
        String a = line[0] + line[1];
        String b = line[2] + line[3];
        long result = Long.valueOf(a) + Long.valueOf(b);
        System.out.pringln(result);
    } 
}
```
```
input: 10 20 30 40 
output: 4060
```

## StringTokenizer
* 문자열을 토큰으로 잘라야 할 때 사용하면 편하다. 
* 수 N개의 합을 구하는 문제 
    * 입력받은 수 N개의 합을 출력한다. 
    * 예제입력:
    ```
    1 2 3 4 5
    ```
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main{
    public static void main(String[] args) throws IOExcpetion{
        BufferedReader bf = new BufferedReader(new InputStreamReader(System.in);
        String line = bf.readLine();
        StringTokenizer st = new StringTokenizer(line, " ");
        int sum = 0;
        while(st.hasNextTokens())
            sum += Integer.valueOf(st.nextToken());
        System.out.println(sum);        
    }
}
```
```
15
```
* 문자열 S에 포함되어 있는 자연수의 합을 출력하라
    * 입력
```
10, 20, 30, 40, 50
```
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main{
    public static void main(String[] args) trhows IOException{
        BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
        String line = bf.readLine();
        StringTokenizer st = new StringTokenizer(line, ",");
        int sum = 0;
        while(st.hasNextTokens())
            sum += Integer.valueOf(st.nextToken());
        System.out.println(sum);
    }
}
```

```
150
```



# 정보올림피아드 문제 해결

> 각자 알고리즘에 대해 공부한 내용에 대한 문제와 풀이 답안을 공유합니다. 
> 스터디 참여자 : 이승주, 박주연, 이동준

#### Index
* [1. 이진수 문제](#ch-1)
* [2. 숫자 사각형 문제](#ch-2)

---

<br/>

### 이진수 문제 <a id="ch-1">1</a>
![사진](https://github.com/poketred12/AlgorithmSolution/blob/master/study_img/%EC%9D%B4%EC%A7%84%EC%88%98%EB%AC%B8%EC%A0%9C_2814.JPG?raw=true)

---

<br/>

```
import java.util.*;
 
 
public class Main {
     
    public static void main(String[] args) {
     
    String number,reverse;
    int count;
    int total = 0;
    Scanner input = new Scanner(System.in);
    //System.out.println("이진수 입력 "); 
    number = input.next();
     
    reverse = reverseString(number);
     
    //System.out.println("number 값은 : "+number);
    count = number.length();
      
     for(int i = 0; i<count; i++){
         
         if(reverse.charAt(i)=='1'){
    //       System.out.println("1인 인덱스는 : "+i);
             total = total+ (int)Math.pow(2, i);
         }else{
        //   System.out.println("0인 인덱스는 : "+i);
         }
         
     }
     System.out.println(total);
         
    }
    public static String reverseString(String s){
        return (new StringBuffer(s)).reverse().toString();
    }
}
```

<br/>

### 숫자 사각형 문제 <a id="ch-2">2</a>
![사진](https://github.com/poketred12/AlgorithmSolution/blob/master/study_img/%EC%88%AB%EC%9E%90%EC%82%AC%EA%B0%81%ED%98%95_2046.JPG?raw=true)

---

```
import java.util.*;
 
public class Main {
    static int n;
    static int m;
     
    public static void main(String[] args) {
        // TODO Auto-generated method stub
 
 
        Scanner input = new Scanner(System.in);
        //System.out.println("사각형의 너ㅣ와 높이를 입력 하세요");
        n=input.nextInt(); // 한변 길이
        m = input.nextInt(); //  종류
         
        switch(m){
         
        case 1 : mode1(n); break;
        case 2 : mode2(n); break;
        case 3 : mode3(n); break;
        //default : System.out.println(" 1~ 3중에 입력 하세요~");
         
        }
         
    }
         
 
    static public void mode1(int n){ 
    int count  = 1;
        for(int i = 1; i<=n; i++){
             
            for(int j =1; j<=n; j++){
                System.out.printf("%d ",count);
            }
            count++;
            System.out.println();
        }
         
    }
         
    static public void mode2(int n){
        int count = 1;
    // 타임 오버 될거임 .. 바꿔야 함..
        for(int i = 1; i<=n; i++){
            if(i%2!=0){
                for(int j=1; j<=n; j++){
                    System.out.printf("%d ",j);
                }
                System.out.println();
            }else if(i%2==0){
                for(int k=n; k>0; k--){
                    System.out.printf("%d ",k);
                }
                System.out.println();
            }
             
        }// 전체  for문
    }
     
    static public void mode3(int n){
         
        for(int i = 1; i<=n; i++){
            int count = 1;
            for(int j=i; j<=n*i;j++){
                j=i*count;
                System.out.printf("%d ",j);
                count++;
            }
            System.out.println();
        }
         
    }
}
```

<br/>
---

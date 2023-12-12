23년 12월 7일 
교재 C언어 본색 (박정민)을 참고하며 기록한 내용 
컴파일러 : devc++(64비트 환경)
포인터와 배열파트 부터 복습시작.



<details>
<summary> 예제 4-14</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[2][3] = {10,20,30,40,50,60};
int *p =NULL;

p= array;

printf("%x %x %x \n",&p[0],&p[1],&p[2]);
printf("%x %x %x \n",&p[3],&p[4],&p[5]);// ref
// p[0]= *(p+0)
printf("%d %d %d",p[0],p[1],p[2]);// value


}
// 2차원 배열을 1차원 포인터변수로 참조 하는 방법에대한 예제. 

```

</div>
</details>

---

<details>
<summary> 예제 4-15</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[2][3] = {10,20,30,40,50,60};
int *p =NULL;// int **p 도 에러남 사용법 안맞음 (1차원 포인터변수를 저장하는 변수이므로) 

p= array;

printf("%d %d %d \n",p[0][0],p[0][1],p[0][2]);// error ! 
// why?-> 


}
// 2차원 배열을 참조 하는 방법에대한 탐구 예제. 

```

</div>
</details>


---

<details>
<summary> 예제 4-16</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array1[2][3] = {10,20,30,40,50,60};
int (*p) [3]=NULL;// 배열 포인터 변수

p= array1;


printf("%d %d %d \n",p[0][0],p[0][1],p[0][2]);// 배열포인터 변수 사용 



}
// 2차원 배열을 참조 하는 방법에대한 탐구 예제. 

```

</div>
</details>

---

<details>
<summary> 예제 4-17</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[2][3] = {10,20,30,40,50,60};
int (*p) [3]=NULL;// 배열 포인터 변수
p= array;


printf("%x %x %x",&array[0][0],&array[0][1],&array[0][2]);// array[][]= value 
printf("%x %x %x",&array[1][0],&array[1][1],&array[1][2]);


printf("%x %x %x",&p[0][0],&p[0][1],&p[0][2]);// address
printf("%x %x %x",&p[1][0],&p[1][1],&p[1][2]);


printf("%d %d %d",*&array[0][0],*&array[0][1],*&array[0][2]);// 값
printf("%d %d %d",*&array[1][0],*&array[1][1],*&array[1][2]);

printf("%x %x %x"*,&p[0][0],*&p[0][1],*&p[0][2]);// 값 
printf("%x %x %x",*&p[1][0],*&p[1][1],*&p[1][2]);



}
// 2차원 배열을 참조 하는 방법에대한 탐구 예제. 

```

</div>
</details>

---


<details>
<summary> 예제 4-18</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[2][3] = {10,20,30,40,50,60};
int (*p) [3]=NULL;// 배열 포인터 변수
p= array;


printf("%x %x %x",&p[0][0],&p[0][1],&p[0][2]); // 2차원 배열 참조-> 값을 품는 주소값
printf("%x %x %x",&p[1][0],&p[1][1],&p[1][2]);

printf("%x %x \n",p,p+1);// 주소값(시작주소 에서의 이동)
printf("%x %x \n",p[0],p[1]);// 주소값 p[N]= *(p+N)
printf("%x %x\n",*(p+0),*p(p+1));   상등 

printf("%d %d %d \n",*p(p[0]+0),*p(p[0]+1),*p(p[0]+2));
printf("%d %d %d \n",*p(p[1]+0),*p(p[1]+1),*p(p[1]+2));

printf("%d %d %d \n",*p(*(p+0)+0),*p(*(p+0)+1),*p(*(p+0)+2));
printf("%d %d %d \n",*p(*(p+1)+0),*p(*(p+1)+1),*p(*(p+1)+2));

// p[0]= *(p+0)

return 0;

}
// 2차원 배열을 참조 하는 방법에대한 탐구 예제. 

```

</div>
</details>

---


<details>
<summary> 예제 4-19</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){


int a=10,b=20;,c=30;
int* ap=null;
int* bp=null;
int* cp= null;// 포인터 변수 개수가 많다.. 일일히..

ap=&a;
bp=&b;
cp=&c;

printf("%d %d %d",a,b,c);
printf("%d %d %d",*ap,*bp,*cp);// value 

printf("%x %x %x",&a,&b,&c);
printf("%x %x %x",ap,bp,cp);// 저장된 주소
printf("%x %x %x",&ap,&bp,&cp);// 변수의 주소 

return 0;
}
// 배열포인터변수에 이어서 포인터 배열의 선언 (두개는 다름) 배열포인터변수는 배열 형태가 잡혀지는 변수이고 포인터 배열은 주소를 저장하는 연속적인 저장소인 배열이다.  

```

</div>
</details>

---

<details>
<summary> 예제 4-20</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){


int a=10,b=20;,c=30;
//int* ap=null;
//int* bp=null;
//int* cp= null;// 포인터 변수 개수가 많다.. 일일히..(4-19 예제임)

int * ap[3]= {null,null,null};

ap[0]=&a;
ap[1]=&b;
ap[2]=&c;


printf("%x %x %x \n",&a,&b,&c);
printf("%x %x %x \n",ap[0],ap[1],ap[2]);
printf("%x %x %x \n",*(ap+0),*(ap+1),*(ap+2));

//밑에는 값 출력하는 코드 *&상쇄되는거 생략
printf("%d %d %d \n",**(ap+0),**(ap+1),**(ap+2));




return 0;
}
// 포인터배열을 통해서 초기화 및 참조를 하는 예제. 

```

</div>
</details>

---

<details>
<summary> 예제 4-21</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){


int a=10,b=20;,c=30;

int * ap[3]= {null,null,null};// 포인터 배열 

ap[0]=&a;
ap[1]=&b;
ap[2]=&c;

int array[2][3]={10,20,30,40,50,60};
int (*p) [3]=null;// 배열포인터 


printf("%x %x %x \n",&a,&b,&c);
printf("%x %x %x \n",ap[0],ap[1],ap[2]);
printf("%x %x %x \n",*(ap+0),*(ap+1),*(ap+2));

printf("%x %x %x \n",&a,&b,&c);
printf("%x %x %x \n",&a,&b,&c);
printf("%x %x %x \n",&a,&b,&c);

p=array;

printf("%d %d %d \n",p[0][0],p[0][1],p[0][2]);
printf("%d %d %d \n",p[1][0],p[1][1],p[1][2]);

printf("%d %d %d \n",*(p[0]+0),*(p[0]+1),*(p[0]+2));
printf("%d %d %d \n",*(p[1]+0),*(p[1]+1),*(p[1]+2));// *(*(p+0)+0)== *(p[0]+0)== p[0][0]

printf("%d %d %d \n",*(*(p+0)+0),*(*(p+0)+0),*(*(p+0)+0);
//생략~ 남은 좌표그냥 출력하는 코드임. 

return 0;
}
// 배열포인터(특정 열단위 배열 주소 저장 가능 )와 포인터배열(주소 저장 가능 )의 차이점을 알아보는 예제. 

```

</div>
</details>

---
<details>
<summary> 예제 4-22</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

char array[]= {'A','B','C','D'};

printf("const char: %c %c %c %c",'A','B','C','D');

printf("const char: %c %c %c %c",array[0],array[1],array[2],array[3]);

// ... 변경후 다시 출력해보고 사이즈 측정하는 코드 생략.


return 0;
}
// 문자배열 예제.

```

</div>
</details>

---

<details>
<summary> 예제 4-23</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

char array[]= {'A','B','C','D'};
char* p= null;

p=array;

// p[0], *(p+0) 으로 출력해보는 코드 생략.



return 0;
}
// 포인터변수로 문자배열 접근 가능 

```

</div>
</details>

---

<details>
<summary> 예제 4-24</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

char array[]= "acac";
// %c %d 로 출력하는 코드 생략-> 각각 소문자 아스키코드 출력 


return 0;
}
// 문자열배열은 ""로 넣는다.

```

</div>
</details>

---

<details>
<summary> 예제 4-25</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

char array[]= {'A','B','C','D','\0'};// 널문자 관련 예제인듯하다.




return 0;
}
// 널문자는 항상 뒤에 있지만 보이지 않는다. -> %d 로 출력시 0 출력. ~ 널문자 마지막에 입력해 놓으면 문자열로 인식됨.

```

</div>
</details>

---
//4-26예제는 %s 사용법이므로 pass(굳이 쓴다면 시작주소를 기반으로 문자열 출력한다쯤?)

---

4-27예제는 널문자의 유무로 문자배열과 문자열 배열에 대한 %s연산자의 차이점을 보임.
4-28 예제는 문자열은 수정가능함을 보임(값의 변경으로 변경함 arr[0]='Z')

// %s 는 종료문자 널문자를 만날때까지 출력하는 연산자이다.

---
<details>
<summary> 예제 4-30</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

char array[]="ABCD";// 문자열 저장.
char* p= "ABCD";// 문자열 상수시작주소 부여 

p[0]='X';;// 상수는 불변
array[0]='X';// 변경가능

p=array;// 상수말고 배열주소 담음.
array=array+1;// 상수이므로 변경 안됨. 

return 0;
}
// 포인터변수로 문자배열 접근 가능 

```

</div>
</details>

---

<details>
<summary> 예제 4-31</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

char* p =&"ABCD";
printf("%x \n",P);// 시작주소 출력 
// p+4..까지



return 0;
}
// 상수의 메모리상의 시작주소 출력 

```

</div>
</details>

---

<details>
<summary> 예제 4-32</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

char* p="good morning";
char* q="c-language";
char* array[2]={"gm","c-l"};


printf("%s \n",p);
printf("%s \n",q);

printf("%s \n",array[0]);
printf("%s \n",array[1]);

printf("%s \n",p+5);
printf("%s \n",p+2);

printf("%s \n",array[0]+5);
printf("%s \n",array[1]+2);

return 0;
}
// 문자열 상수의 시작주소를 저장하는 포인터배열을 활용.

```

</div>
</details>

---

<details>
<summary> 예제 4-34,35</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

char* const p=&a;// p=&a에 대한 상수화 -> 다른주소 저장 금지(주소고정)
const char* p;// 포인터변수의 상수화 -> 값의 변경 금지(값 고정)
const char* const p=&a;-> 둘다 
//안전성과 읽기속성 부여 



return 0;
}
// 문자열 상수의 시작주소를 저장하는 포인터배열을 활용.

```

</div>
</details>

포인터 파트 4 끝
파트 5 포인터와 함수 그리고 void형 포인터 단원 시작.



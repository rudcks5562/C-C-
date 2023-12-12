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


printf("%x %x %x",&array[0][0],&array[0][1],&array[0][2]);// array[][]= 
printf("%x %x %x",&array[1][0],&array[1][1],&array[1][2]);


printf("%x %x %x",&p[0][0],&p[0][1],&p[0][2]);
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

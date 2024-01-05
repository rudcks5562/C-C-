## 구조체 파트 진행

<details>
<summary> 예제1-1</summary>
<div markdown="1">

```
#include<stdio.h>

struct group{
  int a;
  double b;

};

int main(void){

  struct group g1;

g1.a=10;
g1.b=1.1234;

printf("g1.a = %d \n",g1.a);
printf("g1.b= %lf\n",g1.b);

return 0;

}

// group이라는 구조체를 정의하여 구조체 변수 g1을 통해 멤버변수 a와 b에 접근하여 데이터를 저장 및 출력하는 예제.

```

</div>
</details>

---


<details>
<summary> 예제1-2,3,4</summary>
<div markdown="1">

```
#include<stdio.h>

struct group{
  int a;
  double b;

};

int main(void){

  struct group g1;

  scanf("%d %lf,&g1.a,&g1.b");// scanf 를 통한 입력

struct group g2={10,20.0};// 기존 예제는 점에대한 예제(x,y)이나 예제를 묶기위해 응용하여 작성한 부분임. 교재와 다른 부분.
// 구조체 변수 초기화 방법.
// 단 초기화는 괄호를 사용할 경우 선언과 동시에 사용해줘야하며 그 외에는  따로 재정의 해주는 방법이 존재함.
// struct group g3;
// g3={1,2.0}-> error!
// g3.a=1 -> clear

return 0;

}

// group이라는 구조체를 정의하여 구조체 변수 g1을 통해 멤버변수 a와 b에 접근하여 데이터를 저장 및 출력하는 예제.

```

</div>
</details>


---


<details>
<summary> 예제1-5,6</summary>
<div markdown="1">

```
#include<stdio.h>

struct point{
  int x;
  int y;

};

int main(void){

  struct point p1={10,20};
  struct point p2= {0,0};


p2=p1;// 구조체 변수의 복사.

printf("%d %d",p1.x,p1.y);
printf("%d %d",p2.x,p2.y);

// 만약 구조체 변수간의 덧셈이나 뺄셈이 가능할까? -> error!! 오직 대입연산만 가능 사용자정의 자료형이기 때문이다. 


return 0;

}


```

</div>
</details>


---

<details>
<summary> 예제1-7,8</summary>
<div markdown="1">

```
#include<stdio.h>

struct score{
  double math;
  double english;
  double total;

};
struct student{

int no;
struct score s;

}


int main(void){

struct student stu;
stu.no=20101323;
stu.s.math=90;
stu.s.english=80;
stu.s.total= stu.s.math+stu.s.english;
// struct student stu= {20101323,{80,90,0}};  초기화방법2 ,단 대괄호를 생략하여도 순차적으로 멤버변수에 대입되어진다. 

  printf("%d \n ",stu.no);
  printf("%lf \n",stu.s.total);

//중첩 구조체, 구조체 안에 구조체가 있는 형태의 예제이다. 


return 0;

}


```

</div>
</details>


---


<details>
<summary> 예제1-9</summary>
<div markdown="1">

```
#include<stdio.h>

typedef struct score{
  double math;
  double english;
  double total;

} SCORE;// typedef 사용법 1
 struct student{

int no;
SCORE s;

} ;

typedef struct student STUDENT;// 사용법 2


int main(void){

STUDENT stu={10,{90,90,0}};



// 재정의 typedef를 사용해 간결한 코드를 작성하는 예제. -> 구조체 정의와 동시에 재정의 사용, 또는 하단에 작성하는 방법중 택일하여 사용하도록 한다.


return 0;

}


```

</div>
</details>


---


<details>
<summary> 예제1-10,11,12,13,14</summary>
<div markdown="1">

```
#include<stdio.h>

struct student{
  char no[10];
  char name[20];
  double math;
  double english;
  double total;

};

typedef struct student STU;

int main(){

STU s1={"1","chan",90,90,0};
STU s2={"2","lostbeef",920,920,0};
STU s3={"3","goats",190,390,0};

printf("%s %d",s1.name,s1.math);// .연산자를 사용하여 구조체 멤버 배열에 접근 가능하다.

STU st[3]={
{"1","chan",90,90,0},
{"1","chan",90,90,0},
{"1","chan",90,90,0}
};
// 구조체 변수로 배열을 사용하는 방법이다.
//접근은 배열과 동일하게 인덱스나 0번주소+숫자로 접근한다.


//단 배열멤버를 초기화 할때 선언 이후 초기화를 하거나 재입력시
// st[0].no="?"; 처럼 단순한 변수에 대입하듯 사용하면 안된다. 배열시작주소= 배열이름인데 문자열을 넣으려하면 당연히 에러가 난다. 이 때는 strcpy를 사용해 넣는것이 편하다.
// strcpy(st[0].no,"11112");

return;
}

```

</div>
</details>

---

## 중요 멤버변수로 포인터 사용, 구조체변수로 포인터사용, 자기참조 구조체와 외부참조 구조체 파트 시작.
---

<details>
<summary> 1-15,16</summary>
<div markdown="1">

```
struct point {
int* x;
int* y;
};

struct point2{
int* x;
int** y;
};


int main(){
struct point p1;

struct point2 p2;

int num1=4;
int num2=5;


p1.x= &num1;
p1.y= &num2;

p2.x=&num1;
p2.y=&p1.x;// &(&num1)==4 성립.


printf("%d %d \n",*p1.x,*p1.y);
// 연산자의 우선순의가 .이 높기 때문에 p1.y=&num2 , *(&num2) , 서로 상쇄됨*&, num2=p1.y성립 

}

```

</div>
</details>

---


//17예제는 구조체변수 주소랑 멤버변수 1번째꺼 주소랑 같다는 소리.<배열이랑 같다>






<details>
<summary> 코드</summary>
<div markdown="1">

```

```

</div>
</details>

23년 12월 7일 
교재 C언어 본색 (박정민)을 참고하며 기록한 내용 
컴파일러 : devc++(64비트 환경)
포인터와 배열파트 부터 복습시작.~ 배열파트 끝나고 함수와 void포인터 파트 시작

<details>
<summary> 예제 5-5 </summary>
<div markdown="1">

```
#include<stdio.h>
int func(int* p);

void main(){

int array[2][4]={10,20,30,40,50,60,70,80};
  func(array);
return 0;

//주소의 의한 호출이 지역변수를 복사하는 과정을 거치지 않기 때문에 비교적 성능이 우수함.(데이터를 함수에 전달-> 구조체나 배열같은 것)

}
int func(int* p){// 변수 a값을 i에 복사하는 값(메모리공간에 저장된 값)에의한 참조 

printf("%d %d \n",p[1],p[5]);// 출력됨. 포인터변수 p는 1차원 포인터변수이기 때문에 1차원배열처럼 접근할 수 있음.
printf("%d %d" \n,p[0][1],p[1][1]);// error 왜냐하면 2차원배열처럼 접근 안됨-> 접근 가능케 하려면 포인터 변수 p를 배열 포인터로 변경하여 int (*p) [4]의 꼴로 변경해야한다.


}


```

</div>
</details>

---


<details>
<summary> 예제 5-6,7 </summary>
<div markdown="1">

```
#include<stdio.h>
int* input();

void main(){

int * p= NULL;
p=input();
printf("%d \n",*p);




}
int* input(){// 변수 a값을 i에 복사하는 값(메모리공간에 저장된 값)에의한 참조 

static int num1;
scanf("%d",&num1);
return &num1;

}

// 주소를 반환하는 함수를 사용하는 예제.. 배열이나 구조체를 반환할 때에도 주소값을 반환할 필요성이 있다.(성능을 위해)
//지역변수 num1의 주소가 반환되서 경고가 뜬다. 이를 해결하기 위해서는 정적변수를 활용한다.(static)

```

</div>
</details>

---

<details>
<summary> 예제 5-8,9</summary>
<div markdown="1">

```
#include<stdio.h>
int* func();

void main(){

int* p=NULL;
p=func();

  printf("%d\n",p[1]);
  printf("%d\n",*(p+1));



return 0;



}
int* func(){

int array[]={10,20,30,40};// static add! -> no error
 return array;

}


```
//배열 또한 지역변수에 선언되어 메모리상에서 함수가 종료되면 사라지게된다 하지만 static을사용해 정적변수로 만들면 메모리에 계속 존재하기 때문에 사용 가능하다.
</div>
</details>



---


<details>
<summary> 예제 5-10 </summary>
<div markdown="1">

```
#include<stdio.h>
char* string1(void);
char* string2(void);

void main(){

char* p1=NULL;
char* p2=NULL;

p1=string1();
p2=string2();

printf("%s \n",p1);
printf("%s \n",p2);

return ;


}

char* string1(void){
  static char str[]="Good";
  return str;
}
char* string2(void){
  static char str[]="morning";
return str;

}


// 문자열의 시작주소를 받아와서 출력하는 예제. 
// 같은 이름의 static변수를 써놓는다면 ? -> 일단 구글링을 해본 결과 데이터영역에 올라가지기만한다.. 라고 적혀있다.-> gpt선생께 물어본 결과 다른 함수 스택프레임에 같은 이름으로 존재한다..(독립된 영역을 각기 차지한다)로 결론..


```

</div>
</details>

---

<details>
<summary> 5-14,15</summary>
<div markdown="1">

```
#include<stdio.h>
int main (void){

char c=3;
double d=3.1;

void* vx= NULL;

vx=&c;
printf("%x \n",vx);
// printf("%d \n",*vx); ~ error
printf("%d \n",*(char*)vx);// 강제 형변환을 통해 값을 출력할 수 있다. //변경도 가능하다! *(char*)vx=5;

vx=&d;
printf("%x \n",vx);
// printf("%lf \n",*vx); ~ error

// void형 포인터는 모든 자료형의 주소를 저장할 수 있으나 값을 변경할 수 없다.

}




```

</div>
</details>


---


### 큰 2단원 끝!





<details>
<summary> 코드</summary>
<div markdown="1">

```

```

</div>
</details>

23년 12월 7일 
교재 C언어 본색 (박정민)을 참고하며 기록한 내용 
컴파일러 : devc++(64비트 환경)
포인터와 배열파트 부터 복습시작.~ 배열파트 끝나고 함수와 void포인터 파트 시작

<details>
<summary> 예제 5-1 </summary>
<div markdown="1">

```
#include<stdio.h>
int func(int i);

void main(){

  int a=10;
int result=0;

result= func(a);
printf("%d \n",result);
printf("%d \n",a);
//결과 result=11, a=10 이고 위 결과로 추론할 수 있는 것은 값에 의한 참조는 서로 다른 메모리를 쓰기 때문에 공간적인 여유가 있을 때 사용할 수 있다.


}
int func(int i){// 변수 a값을 i에 복사하는 값(메모리공간에 저장된 값)에의한 참조 
i=i+1;
return i;

}

// 값에의한 호출을 이해하기 위한 예제.
// 변수 a와 i는 다른 메모리공간을 가졌었기 때문에 두 변수에 임의로 변화를 가하여도 나머지 한 변수가 영향을 받지 않았음.

```

</div>
</details>

---

<details>
<summary> 예제 5-2 </summary>
<div markdown="1">

```
#include<stdio.h>
int func(int* i);

void main(){

  int a=10;
int result=0;

result= func(&a);
printf("%d \n",result);
printf("%d \n",a);


}
int func(int* i){// 변수 a값을 i에 복사하는 값(메모리공간에 저장된 값)에의한 참조 
*i=*i+1;
return *i;

}

// 값에의한 호출을 이해하기 위한 예제.
// 변수 a와 i는 다른 메모리공간을 가졌었기 때문에 두 변수에 임의로 변화를 가하여도 나머지 한 변수가 영향을 받지 않았음.
// 값의 참조는 매개변수가 스택에 쌓이기 때문에 시간과 메모리가 더 들어간다. 하지만 주소에 의한 참조는 매개변수로써 복사를 하지 않아도 되기에 더 유용히 사용 가능하다.
```

</div>
</details>


---

<details>
<summary> 예제 5-3 </summary>
<div markdown="1">

```
#include<stdio.h>
int func(int*p,int num);

void main(){

int array[]={10,20,30,40,50,60,70,80};
func(array,sizeof(array)/sizeof(int));
return 0;




}
int func(int* p, int num){// 변수 a값을 i에 복사하는 값(메모리공간에 저장된 값)에의한 참조 

int i;
for(int =0;i<num;i++){
printf("%d %d \n",p[i],*(p+i));

}

}

// 주소에의한 참조를 이용한 배열 접근 예제.

```

</div>
</details>

---

<details>
<summary> 예제 5-4 </summary>
<div markdown="1">

```
#include<stdio.h>

int func(int (*p) [4],int num1,int num2);

void main(){

int array[2][4]={10,20,30,40,50,60,70,80};
func(array,sizeof(array)/16,sizeof(array)/8);
return 0;




}
int func(int (*p) [4], int num1,int num2){// 변수 a값을 i에 복사하는 값(메모리공간에 저장된 값)에의한 참조 

int i,j;// 14일 4시 32분 기록 밑에서부터 수정요망 
for(int =0;i<num;i++){
printf("%d %d \n",p[i],*(p+i));

}

}

// 주소에의한 참조를 이용한 배열 접근 예제.

```

</div>
</details>


















---
<details>
<summary> 코드</summary>
<div markdown="1">

```

```

</div>
</details>

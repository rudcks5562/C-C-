23년 12월 7일 
교재 C언어 본색 (박정민)을 참고하며 기록한 내용 
컴파일러 : devc++(64비트 환경)
포인터와 배열파트 부터 복습시작.



<details>
<summary> 예제 4-1</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[3] = {10,20,30};

printf("%x %x %x \n",array,array+0,&array[0])// 0번원소 주소값
printf("%x %x %x \n",array,array+0,&array[0])// 1번원소 주소값
printf("%x %x %x \n",array,array+0,&array[0])// 2번원소 주소값

printf("%d %d %d \n",sizeof(array),sizeof(array+0),sizeof(&array[0]));

}
//결과는 각원소의 주소값이 나오며 마지막줄은 현 64비트 환경의 int자료형은 8바이트이므로 각기 8*3,8,8의 크기로 출력이됨.
// 본 예제는 배열이름은 시작주소로 활용가능함을 보이기 위한 예제임.
```

</div>
</details>




---

<details>
<summary> 예제 4-2</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[3] = {10,20,30};

printf("%x %x %x \n",*array,*(array+0),*&array[0])// 0번원소 주소값
printf("%d %d \n",*(array+1),*&array[0])// 1번원소 값
printf("%d %d  \n",*(array+2),*&array[2])// 2번원소 값

//printf("%d %d %d \n",sizeof(array),sizeof(array+0),sizeof(&array[0]));

}
//결과는 각원소의 값이 나옴
// 본 예제는 4-1의 부분적 변형으로 *연산자를 주소값에 사용하면 값을 호출하는 간접접근에 대한 예제이다.
```

</div>
</details>



---
<details>
<summary> 예제 4-3</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[3] = {10,20,30};

printf("%d %d %d,*(array+0),*&array[0],array[0]);// 모두 같은 값이 나온다.
//... 생략 
}
// 본 예제는 값을 보이기 위해서는 3개의 방법 -> array[num], *(array+N),*&array[num]의 방법을 사용가능하다 *&은 서로 상쇄됨.
```

</div>
</details>

---

<details>
<summary> 예제 4-4</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[3] = {10,20,30};

int* p= NULL;

p=array;

printf("%x %x %x \n",p,p+0,&p[0]);
printf("%x %x \n",p+1,&p[1]);
printf("%x %x \n",p+2,&p[2]);

}

// 본 예제는 포인터변수 p가 배열 array와 연결되면 p를 배열처럼 사용 가능함을 보이기 위한 예제임. &p[0]= p+0
```

</div>
</details>


---

<details>
<summary> 예제 4-5</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[3] = {10,20,30};

int* p= NULL;

p=array;

printf("%d %d %d \n",*p,*(p+0),*&p[0]);
printf("%d %d \n",*(p+1),*&p[1]);// *(p+1)-> *&p[1]->p[1]
printf("%d %d \n",*(p+2),*&p[2]);

}

// 본 예제는 포인터변수 p가 배열 array와 연결되면 p를 배열처럼 사용 가능함을 보이기 위한 예제임. &p[0]= p+0 , 거기에서 값을 추출하는 방법. 
```

</div>
</details>

---

<details>
<summary> 예제 4-6</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[3] = {10,20,30};
int i=0;
int* p= NULL;

p=array;

for(i=0;i<3;i++){

printf("%d %d %d \n",*(p+i),*&p[i],p[i]);

}
for(i=0;i<3;i++){

printf("%d %d %d \n",*(array+i),*&array[i],array[i]);

}
// 같은 결과


}

// 본 예제는 포인터변수 p가 배열 array와 연결되면 p를 배열처럼 사용 가능함을 보이기 위한 예제임. p[0]= p+0
```

</div>
</details>


---
<details>
<summary> 예제 4-7</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[3] = {10,20,30};
int i=0;
int* p= NULL;

p=array;

printf("%d %d %d \n",array[0],array[1],array[2]);
printf("%d %d %d \n",*(array+0),*(array+1),*(array+2));
printf("%d %d %d \n",p[0],p[1],p[2]);
printf("%d %d %d \n",*(p+0),*(p+1),*(p+2));


// 같은 결과 






}

// 본 예제는 8(4) 바이트 포인터 변수로 12바이트 공간의 배열에 모두 접근 가능함을 보이는 예제임.
```

</div>
</details>
---

<details>
<summary> 예제 4-8</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[3] = {10,20,30};
int i=0;
int* p= NULL;

p=array;
printf("%d %d %d \n",p[0],p[1],p[2]);
printf("%d %d %d \n",*p,*(p+1),*(p+2));
p= array+1;
printf("%d %d %d \n",p[-1],p[0],p[1]);
printf("%d %d %d \n",*(p-1),*p,*(p+1));

// 같은 결과 






}

// 본 예제는 주소의 가감산을 활용한 배열접근 방법에 대한 예제임. *연산자를 쓰든, []를 쓰든 자유 
```

</div>
</details>

---
<details>
<summary> 예제 4-9</summary>
<div markdown="1">

```

#include<stdio.h>
int main(void){

int array[3] = {10,20,30};
int i=0;
int* p= NULL;

p=array;
printf("%d %d %d \n",p[0],p[1],p[2]);
printf("%d %d %d \n",*p,*(p+1),*(p+2));
p= p+1;
printf("%d %d %d \n",p[-1],p[0],p[1]);
printf("%d %d %d \n",*(p-1),*p,*(p+1));

// 같은 결과 






}

// 본 예제는 주소의 가감산을 활용한 배열접근 방법에 대한 예제임. *연산자를 쓰든, []를 쓰든 자유 + p에 대한 연산이든 array에 대한 연산이든 주소값의 가감에 대한 결과는 동일
```

</div>
</details>





<details>
<summary> 코드</summary>
<div markdown="1">

```

```

</div>
</details>

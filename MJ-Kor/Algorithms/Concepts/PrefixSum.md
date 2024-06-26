## 누적합(Prefix Sum) 알고리즘

>  **문제 상황**

크기가 $N$인 정수 배열 $A$가 있고, 해당 배열 $A$를 사용하여 구간합 연산을 최대 $M$번 수행해야 하는 경우
<br><br>

> **아이디어**

배열 $A$에 들어있는 값이 바뀌지 않는다는 점을 이용한다. 배열이 변하지 않으니 구간의 합도 당연히 변하지 않는다. 
<br><br>
따라서, 앞에서부터 차례대로 누적된 합을 구해놓고 이를 이용해서 구간의 합을 구할 수 있다.
<br><br>

> **구현 및 시간 복잡도**

```java
// 누적합 배열 S 생성
for (int i = 1; i <= n; i++){
  s[i] = s[i - 1] + a[i];
}

// 구간 l, r의 합 구하기
int answer = S[r] - S[l - 1]
```

누적 합을 저장할 배열 $S$는 $O(N)$에 구할 수 있다.
<br><br>

> **기존 알고리즘과 비교**

누적합을 사용하지 않고 단순 반복문으로 구간합을 $M$번 구할 경우 시간 복잡도는 $O(MN)$이 된다.
<br><br>
하지만 누적합을 사용할 경우, 구간합을 구하는 경우는 뺄셈 연산 한 번만 하면 되기 때문에 $O(N + M)$의 시간 복잡도를 가진다.

```java
// 기존 알고리즘으로 M번의 구간합 구하기

int sum = 0;

for (int j = l; j <= r ; j++){
  sum += a[j];
}

for (int j = l2; j <= r2 ; j++){
  sum += a[j];
}

for (int j = l3; j <= r3 ; j++){
  sum += a[j];
}
// 앞으로 M - 3번 반복


// 누적합 알고리즘으로 M번의 구간합 구하기

for (int i = 1; i <= n; i++){
  s[i] = s[i - 1] + a[i];
}

sum += S[r] - S[l - 1];
sum += S[r] - S[l - 1];
sum += S[r] - S[l - 1];
// 앞으로 M - 3번 반복
```


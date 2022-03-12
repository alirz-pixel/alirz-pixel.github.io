---
title: "[AtCoder] Beginner Contest 243 (A, B, C)"
excerpt: "링크 : https://atcoder.jp/contests/abc243"

categories: 
 - Alogithm
tags:
 - [AtCoder, Contet]

toc: true
toc_sticky: true

date: 2022-03-13
last_modified_at: 2022-03-13
---

<style>
    h3, h4 {border-top: 0.25px solid #51555d54; padding-top: 16px;}
    .info_link {color:white; text-decoration: none;}
    .info_link:visited {color:white; text-decoration: none;}
    .info_link:hover {color:#8cd2d5;}
</style>

``결과 : D번까지 solve(30:09)  ||  패널티 : 1회    `` <br>
``최종결과 - 시간 : 35:09  ||  Performance : 1342점 ``

## A - Shampoo
<table>
    <tr>
        <td>난이도</td>
        <td>브론즈</td>
    </tr>
    <tr>
        <td>분류</td>
        <td>구현 or 시뮬레이션</td>
    </tr>
    <tr>
        <td>사용언어</td>
        <td>cpp</td>
    </tr>
    <tr>
        <td>제출시도</td>
        <td>1회</td>
    </tr>
    <tr>
        <td>제출시간</td>
        <td>2분 50초</td>
    </tr>
</table>


### 문제 설명
<p>
    <a href="https://atcoder.jp/contests/abc243/tasks/abc243_a" class="info_link">
        A - Shampoo 문제 보러가기
    </a>
</p>

#### 문제 정의
매일 밤 다카하시네 집에서는 전원이 [``아버지``, ``어머니``, ``다카하시``] 순으로 머리를 감습니다. <br> 이때 [``아버지`` => A 리터, ``어머니`` => B 리터, ``다카하시`` => C 리터] 순으로 각각 사용한다고 했을 때, <br> 마지막으로 샴푸를 쓰는 사람은 누구일까요? (누구 차례에 샴푸가 부족할까요?)

#### 입력 및 제약
<table>
    <tr>
        <td>조건 1</td>
        <td>1 ≤ V, A, B, C ≤ 10<sup>5</sup> </td>
    </tr>
    <tr>
        <td>조건 2</td>
        <td>모든 값은 정수이다.</td>
    </tr>
    <tr>
        <td>입력</td>
        <td>V &nbsp; &nbsp; A &nbsp; &nbsp; B &nbsp; &nbsp; C</td>
    </tr>
</table>


#### 출력
아버지 차례에 부족하다면 : ``F`` <br>
어머니 차례에 부족하다면 : ``M`` <br>
다카하시군 차례에 부족하다면 : ``T`` &nbsp; 를 출력하세요 <br><br>



![image](https://user-images.githubusercontent.com/74577714/158030601-04379e31-5d68-46b7-b419-b8a9a20a22b3.png)


### 내 풀이
 내 풀이는 ``O(V)``의 ``시간복잡도``를 가지는 방식으로 실제로 다카하시네 집에서 샴푸를 사용하는 것을 코드로 옮겨 적었다. 

 ```cpp
 #include <iostream>

using namespace std;

int main() {
	int V, A, B, C;
	cin >> V >> A >> B >> C;

	while (1) {
		if (V < A) {
			cout << "F";
			break;
		}
		V -= A;

		if (V < B) {
			cout << "M";
			break;
		}
		V -= B;

		if (V < C) {
			cout << "T";
			break;
		}
		V -= C;
	}

	return 0;
}
 ```

### 해설 풀이
 ``내 풀이`` 처럼 while문을 사용할 필요 없이 ``V % (A + B + C)``를 하게 되면, 마지막으로 사용하게 될 사람을 ``O(1)``의 시간복잡도로 구할 수 있게 된다.

  ```cpp
#include <iostream>

using namespace std;

int main() {
	int V, A, B, C;
	cin >> V >> A >> B >> C;

	V %= (A + B + C);

	char ans;
	if (V < A) {
		ans = 'F';
	}
	else if (V < A + B) {
		ans = 'M';
	}
	else {
		ans = 'T';
	}

	cout << ans;

	return 0;
}
 ```


## B - Hit and Blow
<table>
    <tr>
        <td>난이도</td>
        <td>브론즈</td>
    </tr>
    <tr>
        <td>분류</td>
        <td>구현 or 시뮬레이션</td>
    </tr>
    <tr>
        <td>사용언어</td>
        <td>cpp</td>
    </tr>
    <tr>
        <td>제출시도</td>
        <td>1회</td>
    </tr>
    <tr>
        <td>제출시간</td>
        <td>8분 11초</td>
    </tr>
</table>

### 문제 설명
<p>
    <a href="https://atcoder.jp/contests/abc243/tasks/abc243_b" class="info_link">
        B - Hit and Blow 문제 보러가기
    </a>
</p>

#### 문제 정의
숫자 야구 게임이라고 생각하면 편하다. <br>
&nbsp; (1) A<sub>i</sub> = B<sub>i</sub>를 채우는 ``i의 개수``  (=> A의 요소가 B에도 있으며, 그 위치가 서로 같은 것의 개수) <br>
&nbsp; (2) A<sub>i</sub> = B<sub>j</sub>, i ≠ j 인 ``(i, j)의 쌍의 개수`` (=> A의 요소가 B에 있으나, 그 위치가 서로 다른 것의 개수) <br>


#### 입력 및 제약
<table>
    <tr>
        <td>조건 1</td>
        <td>1 ≤ N ≤ 1000</td>
    </tr>
    <tr>
        <td>조건 2</td>
        <td>1 ≤ A<sub>i</sub>, B<sub>i</sub> ≤ 10<sup>9</sup></td>
    </tr>
    <tr>
        <td>조건 3</td>
        <td>A<sub>1</sub>, A<sub>2</sub>, ..., A<sub>n</sub>은 모두 다르다 (B 또한 마찬가지)</td>
    </tr>
    <tr>
        <td>입력</td>
        <td> <code>사진 참고</code> </td>
    </tr>
</table>

#### 출력
첫째 줄에는 ``(1)``을 만족하는 개수 <br>
둘째 줄에는 ``(2)``를 만족하는 개수 <br><br>

![image](https://user-images.githubusercontent.com/74577714/158031979-69f96911-1426-4ab5-a5a5-b0ae7bde6404.png)


### 내 풀이
``(1)`` 조건의 경우, 단순히 A[i] 와 B[i]가 같은지만 확인하면 된다. <br>
``(2)`` 조건의 경우, A[i]의 값이 B에 포함되어 있는지 확인을 해야한다. 이 경우를 위해 B의 요소들을 ``map``에 저장하면 O(log N) 시간만에 찾아낼 수 있다.

``` cpp
#include <iostream>
#include <vector>
#include <map>

using namespace std;

int main() {
	int N;
	cin >> N;

	// A 입력받기
	vector<int> A(N);
	for (auto& i : A) {
		cin >> i;
	}

	// B 입력받기
	vector<int> B(N);
	map<int, bool> B_loc;
	for (auto& i : B) {
		cin >> i;
		B_loc[i] = true; // (2) 조건을 위한 map 설정
	}


	// solve();
	int first = 0, sec = 0;

	for (int i = 0; i < N; i++) {
		// 위치가 같은 경우
		if (A[i] == B[i]) {
			first++;
		}
		// 위치는 다르지만, B에도 있는 경우
		else if (B_loc[A[i]]) {
			sec++;
		}
	}

	cout << first << "\n" << sec;

	return 0;
}
```

### 해설
 ``내 풀이``와 많이 유사하여 추가적으로 작성하지 않았습니다.


## C - Collision 2
<table>
    <tr>
        <td>난이도</td>
        <td>실버</td>
    </tr>
    <tr>
        <td>분류</td>
        <td>정렬</td>
    </tr>
    <tr>
        <td>사용언어</td>
        <td>cpp</td>
    </tr>
    <tr>
        <td>제출시도</td>
        <td>1회</td>
    </tr>
    <tr>
        <td>제출시간</td>
        <td>20분 32초</td>
    </tr>
</table>

### 문제 설명
<p>
    <a href="https://atcoder.jp/contests/abc243/tasks/abc243_c" class="info_link">
        C - Collision 2 문제 보러가기
    </a>
</p>


#### 문제 정의
xy 좌표 평면에 N명의 사람이 있으며, 각각의 사람은 (X<sub>i</sub>, Y<sub>i</sub>)에 있습니다. <br>
그리고 사람 i에 대해 S<sub>i</sub> = R이면 오른쪽으로, S<sub>i</sub> = L이면 왼쪽으로 같은 속도로 이동합니다. <br>
``(오른쪽은 x축의 양의 방향, 왼쪽은 x축의 음의 방향입니다.)`` <br>
만약, 반대 방향으로 이동하는 사람끼리 부딪힌다면(만난다면),  이것을 ``충돌`` 이라고 합니다. <br>
해당 입력에 대해 ``충돌``이 발생하는지 확인하십시오.


#### 입력 및 제약
<table>
    <tr>
        <td>조건 1</td>
        <td>2 ≤ N ≤ 2 x 10<sup>5</sup></td>
    </tr>
    <tr>
        <td>조건 2</td>
        <td>1 ≤ X<sub>i</sub>, Y<sub>i</sub> ≤ 10<sup>9</sup></td>
    </tr>
    <tr>
        <td>조건 3</td>
        <td>i ≠ j 라면 (X<sub>i</sub>, Y<sub>i</sub>) ≠ (X<sub>j</sub>, Y<sub>j</sub>) 이다.</td>
    </tr>
    <tr>
        <td>조건 4</td>
        <td>S의 값은 <code>i 또는 j</code>이며, N의 길이를 가지고 있습니다.</td>
    </tr>
    <tr>
        <td>입력</td>
        <td> <code>사진 참고</code> </td>
    </tr>
</table>

#### 출력
``충돌``이 발생했다면 ``Yes``, 발생하지 않았다면 ``No``를 출력하십시오. <br><br>

![image](https://user-images.githubusercontent.com/74577714/158033125-6e5ab2e7-cb51-4d3c-bb27-f4fd6b8b93e7.png)

### 내 풀이
중요 팁 : ``충돌``이 발생하기 위해선 무조건 ``y``는 같아야 한다. <br>
그리고 ``y``가 같은 사람들 중에서 비교적 ``x``의 위치가 작은 사람이 ``R``이고 비교적 ``x``의 위치가 큰 사람이 ``L``일 경우, ``충돌``이 발생하게 된다.

따라서 map의 key를 ``y``로 두고 ``x``의 값들을 value로 두어 빠르게 y좌표가 같은 사람들을 찾을 수 있도록 하였다.
그리고 오름차순으로 정렬하여 ``충돌``이 가능한지 판단한다

```cpp
#include <algorithm>
#include <iostream>
#include <map>
#include <vector>
#include <string>

using namespace std;

int main() {
	string S;
	int N;
	cin >> N;

	int x, y;
	map<int, vector<pair<int, int>>> loc;
	for (int i = 0; i < N; i++) {
		cin >> x >> y;
		loc[y].push_back({ x, i });
	}
	cin >> S;

	// 충돌이 발생하였는가?
	bool is_true = false;
	for (auto& i : loc) {
		// 충돌을 하려면 사람은 2명 이상이 있어야 함.
		if (i.second.size() > 1) {
			// 정렬
			sort(i.second.begin(), i.second.end(), less<pair<int, int>>());

			// 투 포인터
			int left = 0;
			int right = i.second.size() - 1;

			while (left < right) {
				// 충돌 발생하는 조건에 성립
				if (S[i.second[left].second] == 'R' && S[i.second[right].second] == 'L') {
					is_true = true;
					break;
				}
				// left 증가
				if (S[i.second[left].second] != 'R') {
					left++;
					continue;
				}
				// right 감소
				if (S[i.second[right].second] != 'L') {
					right--;
					continue;
				}
			}

            // 충돌 발생
			if (is_true) {
				break;
			}
		}
	}

    // 충돌 발생
	if (is_true) {
		cout << "Yes";
	}
	else {
		cout << "No";
	}

	return 0;
}
```


### 다른 사람 풀이
``내 풀이`` 처럼 굳이 map을 쓸 필요 없이 모든 사람의 ``x`` 좌표에 대해 오름차순으로 정렬한다. <br>
그 후, i와 i + 1을 비교하며 ``y``가 같고 ``S[i] == R && S[i + 1] == L``인지만 확인해 주면 된다... <br><br>


``*주의 : 이해하기 쉽도록 매크로를 제거하여 shalekberli님께서 작성하신 코드와 다릅니다`` <br>
``*주의 : 이 코드는 제가 작성한 코드가 아닙니다.`` <br>
```cpp
// 출처 : shalekberli(Shahin Alekberli)
// 링크 : https://atcoder.jp/contests/abc243/submissions/30089288

#include <algorithm>
#include <iostream>
#include <vector>
#define F first
#define S second

using namespace std;
using pii = pair<int, int>;

bool cmp(pair<pii, char>& a, pair<pii, char>& b) {
	if (a.F.S == b.F.S) {
		return a.F.F < b.F.F;
	}
	return a.F.S < b.F.S;
}

void solve() {
	int n; cin >> n;
	vector<pair<pii, char>> a(n);
	for (int i = 0; i < n; i++) {
		cin >> a[i].F.F >> a[i].F.S;
	}

	string s; cin >> s;
	for (int i = 0; i < n; i++) {
		a[i].S = s[i];
	}

	sort(a.begin(), a.end(), cmp);
	for (int i = 1; i <= n - 1; i++) {
		if (a[i].F.S == a[i - 1].F.S && a[i].F.F >= a[i - 1].F.F && a[i].S == 'L' && a[i - 1].S == 'R') {
			cout << "Yes" << endl;
			return;
		}
	}
	cout << "No" << endl;
}


int main() {
	solve();

	return 0;
}
```
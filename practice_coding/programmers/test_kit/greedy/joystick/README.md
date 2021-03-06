### 조이스틱
https://programmers.co.kr/learn/courses/30/lessons/42860


#### 문제 요약
* 초기값은 AAA와 같은 형식인 이름을 원하는 이름으로 조이스틱을 이용해서 만들려고 한다
* 조이스틱 조작법은 다음과 같다
    * 위 : 다음 알파벳
    * 아래 : 이전 알파벳(A에서 눌렀으면 Z)
    * 좌 : 커서를 이전으로 이동(맨 앞이었으면 맨 뒤로)
    * 우 : 커서를 다음으로 이동
* ex. JAZ를 만들기 위해서는
    * AAA -> JAA : 위로 9번
    * J|AA -> JAA| : (커서를 맨 뒤로 좌로) 1번
    * JAA -> JAZ : 아래로 1번
    * 총 11번

#### 문제 풀이 과정
* [1차 제출 코드](Solution1.java) - 11개 중 6개 성공
    * 너무 단순하게 생각해서 낭패봤다
    * 알파벳 바꾸는 것에 드는 횟수
        * N 이전이면 '위'를 누르는 것이 횟수가 적고
        * N 이후이면 '아래'를 누르는 것이 횟수가 적고
        * N이면 '위'던 '아래'던 횟수 동일
    * 커서 이동에 드는 횟수(이 생각이 잘못 됐었다...!)
        * '오른쪽'으로만 가던지
        * ~~'왼쪽'으로만 가던지 : 두 번째부터 A가 연속으로 있는 횟수만큼 절약된다~~

* [2차 제출 코드](Solution2.java) - 성공
    * 알파벳 바꾸는 것에 드는 횟수는 위와 동일
    * 커서 이동의 경우는 다음과 같음
        * A가 연속으로 나오는 가장 긴 구간을 구한다
        * 위 구간이 나오기 전까지의 길이를 a, 위 구간의 길이를 b, 위 구간 이후의 길이를 c라고 해보자
        * b가 0이면
            * A가 연속으로 나오는 구간이 없으므로 무조건 '오른쪽'으로 간다 : len - 1
        * a가 0이면
            * 왼쪽으로 가는 경우 드는 횟수 : c
            * 오른쪽으로만 가는 경우 드는 횟수 : b + c - 1
            * c < b + c - 1일 때(b > 1일 때) 왼쪽으로 가는 것이 이득이다
        * c가 0이면
            * 오른쪽으로만 가면 됨 : a - 1
        * 그 외
            * 오른쪽으로 갔다가 왼쪽으로 가는 경우 드는 횟수 : 2 * (a - 1) + c
            * 오른쪽으로만 가는 경우 드는 횟수 : a + b + c - 1
            * a - b < 1 일때 오른쪽으로 갔다가 왼쪽으로 가는 것이 이득
    * 아직도 의문점
        * 커서를 이동할 때 맨 마지막에서 오른쪽으로 이동하면 맨 처음으로 돌아온다는 조건이 없어서 최솟값은 아니지 않나...
        * 다른 사람 제출한 엄청 간결한 답을 봤는데 이해가 안간다...

    
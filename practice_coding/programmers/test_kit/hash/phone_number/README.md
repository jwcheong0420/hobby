### 전화번호 목록
https://programmers.co.kr/learn/courses/30/lessons/42577

#### 문제 요약
* 전화번호 배열(phone_book)에 있는 번호들 중, 한 번호가 다른 번호의 접두어일 경우 false를 return


#### 문제 풀이 과정
* 1차 - 정확성 & 효율성 통과
    * [1차 제출 코드](Solution1.java)
        * phone_book을 Arrays.sort()로 정렬한다
            * ["119", "97674223", "1195524421"] 이던 배열이 ["119", "1195524421", "97674223"]와 같이 정렬됨
        * phone_book을 for loop으로 돌면서 phone_book[i+1]이 phone_book[i]를 포함하는 지 확인
        * 시간 복잡도 : O(n log n)
            * Arrays.sort()의 시간 복잡도가 O(n log n)
    * 이 문제가 왜 hash인건지 잘 모르겠어서 머리를 싸매다가 결국 정렬로 풀었다
        * 근데 이거 제출하고나서 다른 사람들 답안 확인했는데 이렇게 풀거나 이중 for문 돌거나ㅋㅋㅋㅋ
        * hash로 하더라도 결국 이중 for문 도는 수 밖에 없으므로 이렇게 정렬을 하고 인접한 element만 확인하는 게 이득인 듯
    * 아뿔싸 문제점을 발견했다
        * contains()가 아니라 startsWith()를 사용해서 체크했어야 한다. 왜 통과했냐ㅋㅋㅋㅋ
* 2차 - 정확성 & 효율성 통과
    * [2차 제출 코드](Solution2.java)
    * 1차에서 contains()를 startsWith()로 바꾸었다
        * 테스트 케이스에 ["534", "34"]일 때 예상값 true를 추가해서 통과하는 것 확인
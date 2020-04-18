---
layout: post
title: "[프로그래머스] N-Queen (java) Backtracking"
tags:
  - Algorithum
  - 프로그래머스
  - Backtracking
  - 대각선 공식

date: 2020-04-18 16:00:00
comments: true
---



###   N-Queen (Re, 프로그래머스 > Backtracking)

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12952 )

## 문제설명

가로, 세로 길이가 n인 정사각형으로된 체스판이 있습니다. 체스판 위의 n개의 퀸이 서로를 공격할 수 없도록 배치하고 싶습니다.

예를 들어서 n이 4인경우 다음과 같이 퀸을 배치하면 n개의 퀸은 서로를 한번에 공격 할 수 없습니다.

![Imgur](https://i.imgur.com/lt2zdK6.png)
![Imgur](https://i.imgur.com/5c5EUrq.png)

체스판의 가로 세로의 세로의 길이 n이 매개변수로 주어질 때, n개의 퀸이 조건에 만족 하도록 배치할 수 있는 방법의 수를 return하는 solution함수를 완성해주세요.

##### 제한사항

- 퀸(Queen)은 가로, 세로, 대각선으로 이동할 수 있습니다.
- n은 12이하의 자연수 입니다.

------

##### 입출력 예

| n    | result |
| ---- | ------ |
| 4    | 2      |

<br>

## 풀이

```java
class Solution {
    static int answer = 0;
    static int nn =0;
    static int cols[];
    
    static public boolean isPossible(int lev){
        for(int i=0 ;i<lev; i++){//lev행 전까지 다 돌아본다
            if(cols[i] == cols[lev]) // lev전까지 내가 가지고온 값을 가지고있다면
                return false;
            if(Math.abs(lev-i) == Math.abs(cols[lev] - cols[i])) //대각선이어도
                return false;
        }
        
        return true;
    }
    
    static public void queen(int lev){
        if(lev == nn)
            answer++;
        else{
            for(int i=0; i<nn; i++){
                cols[lev] = i; // 들어온 lev에 i 넣어보고 , i는 여기에만 필요
                if(isPossible(lev)) // lev전까지 i가 안겹치면 == 가능하면
                    queen(lev+1);
            }
        }
    }
    
    public int solution(int n) {
        cols = new int[n];
        nn= n;
        
        queen(0); //0층 검사하러 ㄱㄱ
        
        return answer;
    }
}
```

#### 후기 (20min)

생각이 안나서 다시 푼 문제...! <br>

```java
//대각선 공식
	Math.abs(lev-i) == Math.abs(cols[lev] - cols[i])
```

* queen은 한층에 하나만 놓일 수 있다.

* 따라서 이 개념을 가지고 해결한다

* queen() 함수에서는 

  * 현재 들어온 lev에 0부터 n-1까지 다 넣어보며 ispossible한지를 확인하고
  *  가능하면 다음레벨을 검사하러 queen(lev+1)을 넣는다

  * 또 lev가 n-1까지만 가능하면 다음 queen()을 타고 들어가고 n이되면 answer++해준다

* isPossible() 함수에서는

  * 0부터 현재 들어온 lev까지의 cols[]에 lev[i]의 값과 같은 값이 있으면 false
  * 혹은 대각선에 같은 숫자가 있으면 false
  * 나머지는 true 
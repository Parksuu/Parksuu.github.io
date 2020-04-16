---
layout: post
title: "[프로그래머스] JadenCase 문자열 만들기 (java) 문자열_String"
tags:
  - Algorithum
  - 프로그래머스
  - 문자열_String
  - ETC) 문자열 관련 함수 사용법

date: 2020-01-15 22:00:00
comments: true
---



###  JadenCase 문자열 만들기 (programers > lev2 > 문자열_String)

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12951)

## 문제설명

JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

##### 제한 조건

- s는 길이 1 이상인 문자열입니다.
- s는 알파벳과 공백문자(" ")로 이루어져 있습니다.
- 첫 문자가 영문이 아닐때에는 이어지는 영문은 소문자로 씁니다. ( 첫번째 입출력 예 참고 )

##### 입출력 예

| s                     | return                |
| --------------------- | --------------------- |
| 3people unFollowed me | 3people Unfollowed Me |
| for the last week     | For The Last Week<br> |

<br>

## 풀이

```java
    	static public String solution(String s) {
		String a = "";  
		s = s.toLowerCase();
		
		boolean check = false; // i+1이 문자가 아니라는 뜻
		
		for(int i=0;i<s.length()-1;i++) {
			if(s.charAt(i) == ' ') {
				if(i==0)
					a = a + " ";
				//i+1 추가
				if(s.charAt(i+1) != ' ' && check==false) {
					a = a + String.valueOf(s.charAt(i+1)).toUpperCase();
					check=true; //문자가 시작되었다는 뜻
				}
				else if(s.charAt(i+1) == ' ')
					a = a + " ";
			}
			
			else{ // 문자인 경우
				if(i==0)
					a = a + String.valueOf(s.charAt(i)).toUpperCase();
				
				if(s.charAt(i+1) == ' ') {
					a = a + " ";
					check=false; //다시 첫 문자가 시작될때까지 
				}
				else //다음 글자도 문자인 경우
					a = a + String.valueOf(s.charAt(i+1));
				
				
			}
		}//for
		
	    return a;
	}
```

<br>

#### 후기 (1h)

처음에는 문자열이 공백으로 시작하는 예제를 생각하지 않고 20분만에 풀었다...만..  오류!! <br>그래서 공백으로 시작하는 것까지 체크하려면 

1. 전부 toLowerCase로 만들어놓고
2. i와 i+1을 계속 비교해주는 방식으로
3. i(현재)가 공백이면 i+1이 1)공백인지  2)공백이 아닌지
4. i(현재)가 공백이 아니라면 i+1이 1)공백인지  2)공백이 아닌지
5. 총 4가지 if로 구분해주었고 문자가 시작되어 끝나는 것까지 체크해주는 boolean 변수로 마무리!

<br>

<br>

#### tip

1. 8점이나 받은 문제...! 화우
2. Lowercase 와 UpperCase 사용법도 익혀놓자!

<br>
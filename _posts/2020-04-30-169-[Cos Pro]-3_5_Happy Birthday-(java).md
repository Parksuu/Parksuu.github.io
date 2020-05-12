---
layout: post
title: "[Cos Pro] 3_5_Happy Birthday (java) 문자열"
tags:
  - Algorithum
  - Cos Pro
  - 문자열_String

date: 2020-04-30 16:01:00
comments: true
---



###   3_5_Happy Birthday (Cos Pro> 문자열)

## 풀이

```java
package String;

public class cospro_3_5_happybirthday {

   static public String solution(String phrases, int second) {
        String answer = "";
        String display = "";
        display = "______________" + phrases;
        
        for(int i = 0; i < second; ++i) {
        	System.out.println(display +  " "+Character.toString(display.charAt(0)));
        	
        	//display 맨앞거를 뒤에 붙이고
        	display = display + Character.toString(display.charAt(0));

        	//맨앞을 제거한다
        	display = display.substring(1);
        }
        
        //앞에서부터 14개만
        answer = display.substring(0,14);
        return answer;
    }
	
	public static void main(String[] args) {
		String s = "happy-birthday";
		System.out.println(solution(s, 20));
		
	}
}

```

#### 후기 (--)

뒤에 무엇인가가 생기고 앞에 무엇인가를 떼면 되었던 간단하지만 생각못했던 문제! <br>

1. display의 개수는 14개로 고정되어있고, 뒤에 붙는 문자열도 정해져있다.
2. 그렇다면 display에 문자열을 붙힌 후,
3. 초가 지날 때마다 display(0)을 맨뒤에 붙이고, display(0)번째를 제거해준다
4. 그리고 난 후, 앞에서부터 14개만을 출력한다
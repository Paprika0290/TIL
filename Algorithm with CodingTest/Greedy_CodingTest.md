- 프로그래머스 lessons 42862 __[체육복](https://school.programmers.co.kr/learn/courses/30/lessons/42862)__<br>

```java
public int solution(int n, int[] lost, int[] reserve) {
        // 전체학생수 - 도난학생
        int answer = n - lost.length;

        Arrays.sort(lost);
        Arrays.sort(reserve);

        int count = 0;

        // 여벌학생 = 도난학생인 경우 배열값을 -999로 처리
        for(int i = 0; i < lost.length; i++) {
            for(int j = 0; j < reserve.length; j++) {
                if(lost[i] == reserve[j]) {
                    lost[i] = reserve[j] = -999;
                    answer++;
                    break;
                }
            }
        }

        // (배열 값이 0이 아닐 경우 + ) 도난학생 == 여벌학생 +1 or -1일 경우 answer++
        for(int i = 0; i < lost.length; i++) {
            for(int j = 0; j < reserve.length; j++) {
                if(lost[i] != -999 && reserve[j] != -999) {
                    if(lost[i] == (reserve[j] - 1) || lost[i] == (reserve[j] + 1) ) {
                        lost[i] = reserve[j] = -999;
                        answer++;
                        break;
                    }
                }
            }
        }
        return answer;
    }
```

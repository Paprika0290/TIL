- 프로그래머스 lessons 42576 __[완주하지 못한 선수](https://school.programmers.co.kr/learn/courses/30/lessons/42576)__<br>

```java
public String solution(String[] participant, String[] completion) {
        String answer = "";
        HashMap<String, Integer> map = new HashMap<>();
        
        for(String runner : participant) {
            map.put(runner, map.getOrDefault(runner, 0) + 1);
        }
        
        for(String runner : completion) {
            map.put(runner, map.get(runner) - 1);
        }
        
        for( String runner : participant) {
            if(map.get(runner) != 0) {
                answer = runner;
            }
        }
        return answer;
    } 
```
<br><br>
- 백준 problem 10816 __[숫자 카드 2](https://www.acmicpc.net/problem/10816)__<br>
```java
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int[] havingCards = new int[n];
        for(int i = 0; i < n; i++) {
            havingCards[i] = scanner.nextInt();
        }

        int m = scanner.nextInt();
        int[] compareCards = new int[m];
        for(int i = 0; i < m; i++) {
            compareCards[i] = scanner.nextInt();
        }

        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        for(int card : havingCards) {
            map.put(card, map.getOrDefault(card, 0) + 1);
        }

        StringBuilder answer = new StringBuilder();

        for(int i = 0; i < compareCards.length; i++) {
            if(i < (compareCards.length - 1)) {
                answer.append(map.getOrDefault(compareCards[i], 0));
                answer.append(" ");
            }else {
                answer.append(map.getOrDefault(compareCards[i], 0));
            }
        }

        System.out.println(answer);
    }
```
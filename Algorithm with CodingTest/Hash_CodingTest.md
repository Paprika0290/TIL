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

- 프로그래머스 lessons 1845 __[폰켓몬](https://school.programmers.co.kr/learn/courses/30/lessons/1845)__<br>
```java
public static int solution2(int[] nums) {
        HashSet<Integer> set = new HashSet<>();

        for(int num : nums) {
            set.add(num);
        }

        if(set.size() >= (nums.length/2) ) {
            return nums.length/2;
        }

        return set.size();
    }
```

- 프로그래머스 lessons 42577 __[전화번호 목록](https://school.programmers.co.kr/learn/courses/30/lessons/42577)__ <br>
```java
public static boolean solution(String[] phone_book) {
        HashSet<String> set = new HashSet<>();

        for(String phone: phone_book) {
            set.add(phone);
        }

        for(String phone : phone_book) {
            for(int i = 0; i < phone.length(); i++) {
                if(set.contains(phone.substring(0, i))) {
                    System.out.println(phone);
                    return false;
                }
            }
        }
        return true;
    }
```

- 프로그래머스 lessons 42578 __[의상](https://school.programmers.co.kr/learn/courses/30/lessons/42578)__ <br>
```java
public static int solution(String[][] clothes) {
        int answer = 1;

        HashMap<String, Integer> map = new HashMap<>();

        for(String[] cloth : clothes) {
            map.put(cloth[1], map.getOrDefault(cloth[1], 0) +1 );
        }

        for(String key : map.keySet()) {
            answer *= (map.get(key) + 1);
        }

        return (answer - 1);
    }
```

- 프로그래머스 lessons 42579 __[베스트앨범](https://school.programmers.co.kr/learn/courses/30/lessons/42579)__ <br>
```java
    public int[] solution(String[] genres, int[] plays) {
HashMap<String, Integer> genreSort = new HashMap<>();
        for(int i = 0; i < genres.length; i++) {
            genreSort.put(genres[i], genreSort.getOrDefault(genres[i], 0) + plays[i]);
        }

        List<String> genreList = new ArrayList<>(genreSort.keySet());
        Collections.sort(genreList, (g1, g2) -> (genreSort.get(g2) - genreSort.get(g1)));

        List<Integer> answerList = new ArrayList<>();
        genreList.forEach(li -> {
            HashMap<Integer, Integer> playsMap = new HashMap<>();
            for(int i = 0; i < genres.length; i++) {
                if(li.equals(genres[i])) {
                    playsMap.put(i, plays[i]);
                }
            }

            List<Integer> playsList = new ArrayList<>(playsMap.keySet());
            Collections.sort(playsList, (m1, m2) -> (playsMap.get(m2) - playsMap.get(m1)));

            int count;
            if(playsList.size() > 2) {
                count = 2;
            }else {
                count = playsList.size();
            }

            for(int i = 0; i < count; i++) {
                answerList.add(playsList.get(i));
            }
        });

        int[] answer = new int[answerList.size()];
        for(int i = 0; i < answerList.size(); i++) {
            answer[i] = answerList.get(i);
        }

        return answer;
    }        
```

## 모의고사

```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] answers) {
        int[] supo1 = {1, 2, 3, 4, 5};
        int[] supo2 = {2, 1, 2, 3, 2, 4, 2, 5, 2, 1, 2, 3, 2, 4, 2, 5};
        int[] supo3 = {3, 3, 1, 1, 2, 2, 4, 4, 5, 5};

        int[] scores = new int[3];

        for (int i = 0; i < answers.length; i++) {
            if (answers[i] == supo1[i % supo1.length]) {
                scores[0]++;
            }
            if (answers[i] == supo2[i % supo2.length]) {
                scores[1]++;;
            }
            if (answers[i] == supo3[i % supo3.length]) {
                scores[2]++;
            }
        }

        int maxScore = Math.max(scores[0], Math.max(scores[1], scores[2]));

        int count = (int) Arrays.stream(scores).filter(score -> score == maxScore).count();

        int[] bestSupo = new int[count];
        int index = 0;
        for (int j = 0; j < scores.length; j++) {
            if (scores[j] == maxScore) {
                bestSupo[index++] = j + 1;
            }
        }

        return bestSupo;
    }
}
```

* 각 수포자의 답안 패턴을 배열로 정의한다.
* 주어진 문제의 답안을 순회하면서 각 수포자의 답안과 비교하여 정답일 경우 해당 수포자의 점수를 증가시킨다.
* 각 수포자의 점수 중 최고 점수를 찾는다.
* 최고 점수를 받은 수포자들의 번호를 배열에 저장하여 반환한다.
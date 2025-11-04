### 문제 설명

H-Index는 과학자의 생산성과 영향력을 나타내는 지표입니다. 어느 과학자의 H-Index를 나타내는 값인 h를 구하려고 합니다. 위키백과1에 따르면, H-Index는 다음과 같이 구합니다.

어떤 과학자가 발표한 논문 n편 중, h번 이상 인용된 논문이 h편 이상이고 나머지 논문이 h번 이하 인용되었다면 h의 최댓값이 이 과학자의 H-Index입니다.

어떤 과학자가 발표한 논문의 인용 횟수를 담은 배열 citations가 매개변수로 주어질 때, 이 과학자의 H-Index를 return 하도록 solution 함수를 작성해주세요.

제한사항
과학자가 발표한 논문의 수는 1편 이상 1,000편 이하입니다.
논문별 인용 횟수는 0회 이상 10,000회 이하입니다.

입출력 예
citations return
[3, 0, 6, 1, 5] 3

입출력 예 설명
이 과학자가 발표한 논문의 수는 5편이고, 그중 3편의 논문은 3회 이상 인용되었습니다. 그리고 나머지 2편의 논문은 3회 이하 인용되었기 때문에 이 과학자의 H-Index는 3입니다.

### 문제 풀이

```
def solution(citations):
    # 내림차순 정렬
    citations = sorted(citations, reverse=True)

    # 인용된 횟수 이상의 논문을 cnt로 세지 않고 index를 활용 -> 내림차순이니
    for i, c in enumerate(citations):
        # 최대 h를 구하는 거니 i >= c 이면 반환
        if i >= c:
            # 논문의 인용 횟수를 반환하는 게 아니라 h-index를 구하는 것이니 i 반환
            return i
    # 만약 i >= c가 없었다면 모든 논문의 인용 횟수가 논문 횟수보다 많다는 뜻
    return len(citations)
```

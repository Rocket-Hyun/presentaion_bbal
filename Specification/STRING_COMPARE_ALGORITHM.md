# 음성 텍스트 - 대본 텍스트 비교 알고리즘

## 대본 자료 구조

대본 텍스트들을 1글자 단위로 잘라서 그 글자의 발성여부 (state)를 같이 2중 배열로 저장한다.

```javascript
// Sn -> 대본의 n번째 글자
// statecode -> 0(아직 읽지 않음), 1(읽음), 2(안 읽고 넘어감)
[[S1, state code], [S2, state code], ... , [Sn, state code]]

// 예시) '안녕하세요 박정현입니다' 대본에서 '안녕하세요 정현입'라고 말했을때
[["안",1], ["녕",1], ["하",1], ["세",1], ["요",1], ["박",2], ["정",1], ["현",1], ["입",1], ["니",0], ["다",0]]
```

## 발표 대본 진행 상태 Checker

대본을 읽다가 문장을 통째로 스킵하는 등의 행동을 고려해서 대본에서 진행 상태를 지속적으로 체크하는 배열도 있어야함.

대본의 n글자씩 잘라서 글자와 상태값으로 저장한다.

```javascript

[[S1, state code], [S2, state code], ... [Sn, state code]]
[[S(n+1), state code], [S(n+2), state code], ... [S(2n), state code]]
...

```

최근의 5개 Checker를 다 계속해서 확인하면서 문장을 넘어가더라도 진행상태를 알 수 있게 함.

이미 지나간 Checker는 더 이상 확인하지 않음.

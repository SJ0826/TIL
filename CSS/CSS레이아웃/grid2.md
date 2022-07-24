# 트랙 관련 함수

## repeat()
반복되는 값을 자동으로 처리하는 함수<br><br>

## minmax()
최솟값과 최댓값을 각각 지정할 수 있는 함수<br><br>

## auto-fill  & auto-fit
반응형을 고려해 사용할 수 있는 키워드들(함수x)
* auto-fil: 컨테이너의 여백을 남긴다.
* auto-fit: 컨테이너의 여백을 채워준다.
<br><br>
```
grid-template-columns: repeat(auto-fit, minmax(100px, auto));
/*컨테이너의 여백없이 그리드 아이템의 크기의 최솟값은 100px, 최댓값은 자동으로 만든다.*/
```

![gridtrack](https://user-images.githubusercontent.com/56298540/180641038-bcca95a7-fc15-4b86-bf4b-4698e1aba143.PNG)
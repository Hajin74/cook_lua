#cook.lua

## 변수

* background = {주방, 도마}
* gameUI = {환경설정, 레시피 아이콘, 카운터로 이동하기, 오픈된 레시피북}
* btnUI = {휴지통 버튼, 완성 버튼}
* igUI = {김, 밥, 단무지, 달걀, 햄} // 진열된 재료
* usedigUI = {김, 밥, 단무지, 달걀, 햄} // 사용된 재료
* kimbapUI = {꼬마김밥, 다른김밥1, 다른김밥2...} // 차차 김밥종류 늘려가기
* moneyUI = {돈 표시창}
* flag → finishIg()함수에 사용됨
* money 금액



## 기능(함수)
- 카운터 ↔ 주방 이동: moveCounter()
- 레시피북 열람/닫기 가능: openRecipe(), closeRecipe()
- 각각의 재료를 쓸 때마다 금액 소진 (100원씩 감소): calcIg()
- 완성된 김밥을 클릭하면 
- 완성된 김밥을 팔면 1000원 이익: calcKimbap()
- 김밥을 잘못 만들면(재료 5가지를 모두 쓰지 않고) 완료버튼을 누르면: finishIg()
- 잘못된 김밥(다른김밥1)이 뜸: finishIg() → if flag == 0
- 잘못된 김밥이 뜨면 더 이상 재료를 클릭하지 못함: removeEventListener(putIg)
- 다시 만들기 위해서는 휴지통 버튼을 눌러 김밥을 버려줌: cancleIg()
- putIg(): 진열되어 있는 재료와 사용된 재료는 각자 배열은 다르지만 같은 인덱스를 가지고 있다. 따라서 진열되어 있는 재료를 클릭하면 인덱스를 받아 해당하는 사용된 재료를 보여준다.
즉, 도마 위에 재료를 올려놓는 함수이다.
이 함수를 실행하면 자동으로 calcIg()함수를 실행하여 재료값을 계산한다.
- regame(): putIg()함수를 다시 사용할 수 있게 한다.

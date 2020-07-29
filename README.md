# nomad-css
### 노마드코더 CSS Masterclass 강좌와 함께하는 CSS 뿌시기

---

## Flexbox
- display
  - block : 기본. 오른쪽으로 여백 무한대라서 자리차지.
  - inline : width height 없음. text같은거.
  - inline-block : block 유지하면서 text처럼.
    - 이걸로 px로 margin 주면, 반응형에서 깨진다. 그래서 flexbox가 나옴.
  - flex : 이걸 적용하면 flexbox 사용 가능.

- flexbox 개념
  - display:flex;를 부모에 적용해주면 됨.
  - 붙어있는 부모가 자식을 움직일 수 있다.
  - 반응형 inline-block이라고 생각하면 됨.
  - 두 개의 axis : main axis & cross axis
    - flex-direction: row;가 기본값. 바꾸려면 row 대신 column.
      - row-reverse, column-reverse도 있다.
    - main axis 방향으로 옮길 경우(가로가 기본) justify-content 사용.
      - justify-content: space-around;
      - justify-content: center;
    - cross axis방향으로 옮길 경우(main axis와 반대) align-items 사용.
      - 이게 안 먹는 경우 부모컨테이너 height를 보자. 100vh로 설정해주면 화면 꽉 차므로 알기 쉬울거.
      - align-items : center;
      - align-items : stretch;
      - flex-start(기본값), flex-end도 있음.
  - 부모한테 주는게 원칙이지만.. 자식한테 주는거 딱 두개
    - align-self는 align-item처럼 작동함. 각각의 nth-child로 해서 줄수있겠지.
    - order : 말그대로 order를 바꾼다. 기본값은 0인데 1로주면 order0 다음에 적용됨.
  - 만약 child가 너무 많아서 그 width를 다 못담아낸다면?
    - width를 무시하고 한 줄로 꾸겨넣어짐.
    - 이걸 바꾸려면 flex-wrap:wrap;으로 하면 됨.(nowrap이 기본.)
      - wrap으로 하면 한 줄은 포기해도 width를 유지함.
      - wrap-reverse 또한 존재.
      - 그럼 이걸로 두줄되었을때 각 줄사이의 여백은? align-content로 조절가능.
        - align-content: space-between; 등등 다양한 옵션.
      - nowrap일때는 어떤 박스가 찌그러질지 설정할 수 있음
        - child에 대해 flex-shrink:2로 해주면 다른것보다 두배로 더 찌그러짐. 기본값이 1인거지.
        - 상당히 유용한 property라고 할수있지.
        - 반대로 flex-grow도 있음. 여분의 공간이 있다면 그걸 활용해 늘어나는거지. 기본값은 0.
        - 즉 width를 쓸 필요가 있나..? 이제 없는거다. px는 절대적인데 디스플레이는 크기가 제각각이니까.
      - flex basis는 main axis의 크기다. 기본값은 가로크기다 이말이지.

- flexbox 연습
  - ![](https://github.com/KangJunewoo/nomad-css/blob/master/Flexbox/flexboxfroggy.gif)
  - [여기](http://flexboxfroggy.com/)서 가능
  - 정렬하기
    - justify-conetnt / align-items : space-around, space-between, center, flex-start, flex-end
    - space-around vs space-between?
  - 축바꾸기
    -  flex-direction : row vs column (feat.-reverse)
  - 순서바꾸기
    - order
  - 한줄에서 벗어나기
    - flex-wrap: wrap;
    - flex-flow는 flex-direction + flex-wrap을 동시에 적용한 효과. 가령 column wrap;으로 선언 가능.
    - align-content로 여러 줄 사이 조정 가능. align-items와 같은 속성들이 들어감.

  
## Grid
- 왜 그리드가 필요할까?
  - flexbox에선 뭐랄까 모두 개별적으로 해줘야 한다.
  - 그리드모양을 생각보다 flexbox로 만들기 쉽지 않다.
  - flexbox는 1차원기반 grid는 2차원기반
- 그리드 기본
  - display:grid;로 적용가능.
  - 기본방향은 grid-auto-flow:row; 방향바꾸려면 column으로 고우고우.
  - 역시나 father에서 거의 대부분을 적용해줌.
  - column 당연히 정해줘야겠지.
    - grid-template-columns: 20px 40px 30px 60px 이런식으로 각 칼럼 사이즈를 줄 수 있음
      - 이름을 줄 수 있음. \[first-line\] 100px \[second-line\] 200px 이런식으로.
      - 200px 네번준다고 하면 repeat(4, 200px); 해줘도 ㄱㄴ.
      - px 대신 상대적으로 줄거면 fr 가능. 꽉 채우는 상태에서 해당 비율만큼 채움.
      - repeat 짬뽕 ㄱㄴ (공백으로 구분)
      - auto는 가능한 크게. 역시 짬뽕 ㄱㄴ.
    - column-gap 적용가능.(그냥 gap도 되네)
  - 그담엔 row를 만지고 싶다라고 해보면
    - grid-template-rows : 100px 50px 300px 요런식.
      - repeat 당연히 ㄱㄴ
    - row-gap 또한 적용 ㄱㄴㄱㄴ
    - row에 fr 적용할거면 height 먼저 설정해주자. 50vh 이런식으로.
    - 적용한거보다 더 많이 들어온다면? grid-auto-rows 적용 가능.
      - grid-auto-rows:100px;로 하면 더 많은 content가 들어와도 모두 100px로 처리됨.
- grid template areas
  - 각각의 자식에 grid-area로 이름을 부여하고(따옴표 ㄴㄴ)
  ```
    grid-template-areas:
      "a a a a" (fr이나 이름 지정가능)
      "b b b c" 
      "b b b c" 
      "d d d d"; 
  ```
  - empty space를 남기고 싶다면 a b c d 들어갈 자리에 . 찍자.
  - repeat는 적용되지 않음.
  - 니꼬는 이 방법을 제일 좋아함. 네이밍도 잘 안쓴다고 하더라.
- 쭉쭉 늘리기 (자식 속성)
  - grid-column-start :1;& grid-column-end:4;
    - 1째칸에서 시작해 4째칸에서 끝난다.
    - 줄이면 grid-column: 1 / 4;
    - 처음부터 끝까지 가는 상황이면 1 / -1;
    - 몇칸 차지하는지 나타내고 싶다면 : span 활용
      - 시작점도 같이 적어줘야함.
      - 2 / span 2;면 2번째에서 시작해 2칸 차지한다는 뜻.
  - row도 됨.
  - 각 이름을 갖다쓸 수 있음.
- justify-items와 align-items 사용가능.
  - start / end가 많이 쓰이네. -> 이 경우 width / height가 있어야만 가능.
  - 기본값은 모두 stretch다.
  - place-items: stretch center; 이런 식으로 한방에 두개 적용가능.
  - #2.9 한번 더 보자.
- align-self는 자식한테 적용되는거 익숙하지?
  - justify-self도 그렇게 할 수 있음.
  - 합치면 place-self: start end; 이런 식으로
- keywords
  - minmax(100px, 1fr) : 100px이상 1fr 이하가 됨.
  - auto-fill / auto-fit
    - auto-fill : row에다 빈 column들로 개수를 채우는거
    - auto-fit : row에 그나마 있는 것들로 크기를 채우는거
    - 반응형 디자인의 기본이라고 할 수 있다.
  - min-content / max-content : 태그 안의 컨텐트(텍스트같은거)에 촤라락 맞춰버리기
    - min-content : 여러줄에 최대한 걸치고 박스는 줄어듦
    - max-content : 한줄 쫙 눌이고 박스도 늘어남
    - size에 연연하지 않고 content에 맞춘다는 점이 혁신적.. 이라고 말한다!
  - 약간 이부분 강의 나중에 필요할때 다시 들어보자. 아직 어떻게 응용할지 감이 잘 안온다.


## 기타 몰랐던 것들
```
.box:nth-child(숫자, odd/even 등..){
  ...
}
```
vscode에서 .item*20>{$}로 1~20까지 item 만들 수 있음.
# nomad-css
### 노마드코더 CSS Masterclass 강좌와 함께하는 CSS 뿌시기

---

## Flexbox
- display 속성
  - block : 박스처럼 취급
    - width, height, margin, padding 지정가능.
  - inline : 글자처럼 취급
  - inline-block : 글자처럼 취급되는 block
    - margin을 주면 정렬을 잘 할 수 있겠지만.. 화면크기 바꾸면 깨짐.
  - 그럼 어떻게 반응형도 적용하면서 좌우 or 상하로 예쁘게 배치할까?
    - 답은 display:flex;

- flexbox 개념
  - 두 개의 axis : main axis & cross axis
    - flex-direction
      - row가 기본값.
      - row-reverse, column-reverse도 있다.
    - main axis 방향 : justify-content
      - space-around, space-between, center, ...
    - cross axis방향 : align-items
      - 부모컨테이너 height을 100vh로 설정해주면 쉽게 파악 가능
      - center, stretch, flex-start(기본값), flex-end 등등..
  - 자식한테 주는 속성 딱 두개
    - align-self
    - order
  - 심화
    - 한 줄에 너무 많은 child 해결법 : flex-wrap : wrap;
      - wrap으로 하면 한 줄은 포기해도 width를 유지함.
      - wrap-reverse 또한 존재.
      - 그럼 이걸로 두줄되었을때 각 줄사이의 여백은? align-content로 조절가능.
        - align-content: space-between; 등등 다양한 옵션.
    - nowrap일때는 어떤 박스가 찌그러질지 설정할 수 있음
      - flex-shrink, flex-grow : 기본값은 0. 부족한 / 여분의 공간이 있다면 활용 가능.
      - 즉 width를 이제 굳이 쓸 필요가 없음.

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
- 2차원 작업을 위해선 그리드를 쓰자.
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
- grid 연습
  - ![](https://github.com/KangJunewoo/nomad-css/blob/master/Grid/gridgarden.gif)
  - [여기](http://cssgridgarden.com/)에서 연습 가능
  - 자식태그 : 시작위치 & 끝위치
    - grid-column-start & grid-column-end -> grid-column
    - 칸이 아닌 선을 기준으로 함!
    - 음수 & span & auto
    - row도 가능
    - 싹 다 합치면 grid-area(rs cs re ce 순)
    - order로 그리드 안에서 어떤게 먼저 오게 할지 설정 가능.
  - 부모태그 : 그리드 자체의 설정
    - grid-template-columns & grid-template-rows -> 합치면 grid-template
    - repeat(8, 12.5%); 식으로 설정 ㄱㄴ.
  - 24번 이후 아리까리하다.


## SCSS
- 기본
  - scss 파일명으로 _를 앞에 붙이면(예를들면 _merong.scss) scss 안에서만 쓰겠다는 뜻임. 아래 나오는 문법들 적용시킬때 씀.
  - 변수는 $를 붙이고, 키워드는 @를 붙임.
    - @import '_merong.scss' 해서 background:$bg로 설정하는 것처럼.
    - .box{&:hover{haha}} 이런식으로 this처럼 & 사용 가능.
  - nesting 물론 가능.
- Mixins & Extend
  - 적절히 활용해 함수처럼 사용가능.
- Responsive Mixins : 반응형 디자인을 쉽게 줄 수 있음. 코드 참조.


## 기타 몰랐던 것들
- ```
  .box:nth-child(숫자, odd/even 등..){
    ...
  }
  ```
- vscode에서 .item*20>{$}로 1~20까지 item 만들 수 있음.
- em : 상위요소 기준 em만큼 곱한 크기

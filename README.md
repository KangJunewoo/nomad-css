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

- flexbox
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



## 기타 몰랐던 것들
```
.box:nth-child(3){
  ...
}
```
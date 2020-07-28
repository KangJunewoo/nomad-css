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
  - 항상 붙어있는 부모가 자식을 움직일 수 있다.
  - 반응형 inline-block이라고 생각하면 됨.
  - 두 개의 axis : main axis & cross axis
    - main axis 방향으로 옮길 경우(가로가 기본) justify-content 사용.
      - justify-content: space-around;
      - justify-content: center;
    - cross axis방향으로 옮길 경우(main axis와 반대) align-items 사용.
      - 이게 안 먹는 경우 부모컨테이너 height를 보자. 100vh로 설정해주면 화면 꽉 차므로 알기 쉬울거.
      - align-items : center;
      - align-items : stretch;
      - flex-start(기본값), flex-end도 있음.


## 기타 몰랐던 것들
```
.box:nth-child(3){
  ...
}
```
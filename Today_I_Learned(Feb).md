# 20210201 HTML

## HTML

- block tag
- inline tag

- 주요 태그
  - p
  - a
  - label
  - select
    - option
  - radio
  - hr
  - br
  - div
  - input
  - button

## CSS

- margin-padding
  - margin : border 바깥
  - padding : border 안쪽
  - margin : a b c d 면 a가 top, b가 right c가 bottom, d가 left
  - margin : a b 면 a가 top&bottom / b가 left&right
- box-sizing
  - 기본적으로 모든 요소의 box-sizing은 content-box
  - padding을 제외한 순수 contents 영역만을 box로 지정
  - 다만 우리가 일반적으로 영역을 볼 때는 border까지의 너비를 100px 보는 것을 원함
  - 그 경우 content-box를 border-box로 설정
  - margin 상쇄 : 
    - block일때, top-bottom일 때 나타남
    - margin끼리 겹쳐서 가장 큰 margin으로 상쇄되는 것
- display:
  - block : 부모 너비를 전체를 다 차지함
  - inline : 자식의 (높이 또는) 너비만큼만 너비를 차지함, 
    - width, height 속성 사용 불가
  - inline-block : inline+block
  - none : 화면에 표시하지 않음(공간도 남지 않음)
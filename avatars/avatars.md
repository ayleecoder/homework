# 코드 설명

## HTML

### CSS 리셋

- normalize, reset을 적용한 후 메인 스타일인 avatars.css 적용

### <body>

- 전체 8개의 아바타를 아바타 컨테이너 안에 지정
- 각각의 아바타와 온오프라인 상태 표시를 하나의 박스로 지정

## CSS

### .avatar-container

- flow-root는 부모 요소에 대한 내용이 자식 요소의 float을 감지하고 요소를 감싸는 효과가 있기에 float이 자식 요소를 부모 요소 바깥으로 빠져나가는 현상을 방지하기 위해 지정
- 컨테이너 가운데 정렬 하기 위해 margin에 좌우 auto 지정

### face1, face2 ..

- 이미지 간의 간격이 20px이었으므로 좌우 마진으로 설정하기 위해 10px 지정
- 이미지의 모양을 원형으로 렌더링하기 위해 경계값을 50px로 지정하고 이를 넘어가는 이미지 부분을 보이지 않게 하기 위해
  overflow: hidden 사용

### 아바타 상태 속성

- online, offline 클래스로 각각 지정된 배경색을 통해 아바타의 온오프라인 상태 표시
- float을 사용해 원을 오른쪽부터 float하도록 함
- position: relative를 통해 얼굴 요소 위에 바로 위에 상태 표시를 배치 하며 기존 위치에서 bottom과 left를 통해 상대적으로 상태 표시 위치를 조정

### flex

- 브라우저가 flexbox를 지원하는 경우, 이미 지정한 css 대신 flex를 활용한 방법을 위해 적용하기 @support를 활용
- flex-wrap 을 통해 avatar-container의 자식 요소가 부모요소를 벗어날 시 줄 바꿈하도록 wrap 지정
- justify-content: center를 통해 자식요소가 수평방향으로 가운데 정렬하도록 함

## 어려웠던 부분

- float을 활용하기 위해 어떻게 HTML을 마크업해야할지, avatar-container 안에 어떤 하위요소를 박스로 묶어야할지 어려웠음
- 컨테이너의 마진값을 정확히 설정하지 못함
- 시맨틱 요소 대신 div 요소로 전부 마크업하게 된 점, aria-label 지정하지 못함
- 아바타의 상태속성 on/off를 지금 코드처럼 지정해서 박스로 묶어두는 것이 아닌, 조건에 따라 on, off 가 변경되도록 하는 방법

yhcho0405@kakao.com
피드백은 언제나 감사합니다.
조금이라도 아쉬운 부분이 있다면 편하게 까주셔도 좋습니다.

#2019년 12월 23일 공부용으로 노베이스 개발 시작.
  - 크롬 익스텐션으로 주제 설정.
  - 구글링해가며 구동방식 이해.
  - 개발할 기능 구상.
  - 유튜브 동영상 시청 시, 시청중인 위치를 영상 제목과 함께 북마크해 모아주는 기능 구상.(onetab에서 아이디어 얻음)
  - 현재 시청중인 분, 초를 가져올 방법을 생각해야 함.
  - html body태그에서 모든 단어들을 가져오기 => 띄어쓰기로 스플릿 해서 구분 => 줄바꿈으로 스플릿해서 분, 초 가 담긴 인덱스로 화면에 출력까지 성공.(아마 더 쉽게하는 방법이 있을 것)

  문제점
    1. html로 현재 재생중인 부분을 가져오다 보니 영상 시청 중 아래 타임라인이 사라지면 사라지기 직전의 시간을 가져온다는 점.

  추가 할 기능
    1. 여러개의 북마크를 어떻게 보여줄지.
    2. 북마크된 링크로 넘어가는 방식은 어떻게 할지(링크누르기?, 버튼누르기?)

  아이디어
    1. 유튜브 링크 뒤에 시간을 붙이면 그 시간대로 영상이 재생된다.

#2019년 12월 24일.
  - 유튜브 게시자의 프로필사진을 불러와 보여주는 기능 구상.
  - 추출해야할 jpg파일의 src값 img태그의 class이름까지는 구했는데 자바스크립트에서 이를 받아올 방법을 찾아야 함.
  - jquery를 이용해 보려 했으나 실패.
  - 북마킹 버튼 디자인(오픈소스 활용)

  문제점
    1. 위에서 말했던 대로 jquery를 못 쓰고 js로만 해보려 했으나 안됨.
    2. 아직도 23일 문제점 1을 해결하지 못함.

  추가 할 기능
    1. 북마크된 정보에 프로필사진과 채널 명, 제목 일부를 보여줄 레이아웃 구상.
    2. 크롬 내부저장소에 북마크 된 정보를 저장.

  아이디어
    1. 채널 프로필 사진을 함께 보여주어 정보확인 부분에서의 명확성을 높힘.

#2019년 12월 25일.
  - 새로운 확장프로그램 아이디어 생겨서 병행하느라 별로 못함.

#2019년 12월 26일.
  - 게시자의 프로필 사진을 가져오는 것 보단 썸네일을 가져오는게 가시성이 더 높을 것이라 판단.
  - 썸네일을 html iframe으로 불러오는데 성공.
  - 링크와 합쳐 화면에 띄우는 데 성공.
  - 삭제버튼 추가.

  문제점
    1. 썸네일 위 아래로 검은색 여백이 생간다.
    2. 크기를 강제로 줄이면 아래쪽 썸네일이 잘리기 때문에 해결하지 못한다.

#2019년 12월 27일
  - 전체적인 레이아웃 수정.
  - 제목 가져와서 화면에 표시하기 성공.
  - 제목 string으로 형변환 후 " - YouTube" 삭제.
  - 뒤늦은 오류 발견.(해결)
    + 타이틀을 가져올 때 알람의 수 만큼 제목 앞에 붙어서 출력되는 문제 수정.
    + 현재 시간을 가져올 때 가끔 인덱스 참조 예외가 생기는 문제 수정. (추후 유튜브 UI가 업데이트 되면 다시 발생할 가능성이 있기 때문에 오류코드와 이메일 삽입)

  문제점
    1. 디자인 수정 필요.
    2. 크롬 저장소 활용해야 함.
    3. youtube에서만 작동하도록 예외처리가 안됨.
    4. 버튼이 사라지게 하는 방법 찾기.

  추가할 점
    1. 버튼의 활용 및 레이아웃 구상.

#2019년 12월 28일
  - 유튜브에서만 동작할 수 있도록 예외처리 함.
  - 제목 자르기 부분의 오류 확인 및 수정.(알람에 9+가 떴을 경우 외 여러가지 상황에 유동적으로 반응하게끔)
  - 유튜브 안에는 있지만 동영상을 시청하지 않는 상황에 대한 예외처리 완료.

  문제점
    1. 동영상이 끝났을 때 에러코드 출력함. 예외처리 필요.
    2. 크롬 익스텐션에선 html의 인라인 함수를 보안상의 이유로 막아놈.(인라인 onclick 사용 불가)
    3. 2번의 이유로 js파일 내부에서 버튼 클릭 이벤트를 만들었으나, html 파일의 형식으로 insertBefore메서드를 사용할 방법을 찾아야 함.

  아이디어
    1. 북마크가 쌓이면서 스크롤이 내려간다면 북마크 버튼의 위치를 유동적으로 바꾸는 방법이 있으면 좋겠다.

#2019년 12월 29일
  - insertBefore 메소드를 사용하지 않고 append로 처리해 클릭하면 현재의 창이 스크랩 되도록 함.
  - 크롬 스토리지 기능을 사용해 북마크를 자동으로 저장하고 가져오는 기능 추가.
  - delete all 버튼도 기능 부여.
  - 스토리지 기능 사용하며 코드 구조 수정.
  - 예외처리 때문에 유튜브 밖에서 기록 삭제가 안되는 오류 수정.
  - 썸네일 가져오는 방식을 iframe에서 img로 바꿈.
  - 썸네일 상하 여백 크롭.

  문제점
    1. 익스텐션에서 a태그를 사용할 수 없다.

  추가할 점
    1. 썸네일과 제목 클릭 시 하이퍼링크.
    2. 레이아웃 수정.
    3. 알수 없는 크롬저장소 오류 원인 찾기.

  발견 된 오류
    1. 정상 작동 하나, 가끔 삭제 후 다시 들어가보면 다시 생겨있거나 이전의 기록과 합쳐짐.

#2019년 12월 30일
  - 디자인 레이아웃 수정.
  - 하이퍼링크 기능 활성화.
  - 썸네일 테두리 둥글게 처리.
  - 제목 2줄이상 오버플로우는 hidden처리.
  - 실시간 영상의 경우 인덱스 오류 발생.
  - 인덱스 참조에러가 알림의 유, 무와 관련있다는 사실 파악.
  - 29일 발생한 오류 1번을 해결함.

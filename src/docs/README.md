## 프리코스 미션 1 - 숫자 야구 게임 기능 구현 문서

### 게임 문구 상수 변수 지정

NUMBER = 3
INPUT_NUMBER: '숫자를 입력해주세요 : '
GAME_START: '숫자 야구 게임을 시작합니다.'
GAME_OVER: '3개의 숫자를 모두 맞히셨습니다! 게임 종료'
GAME_RESTART: '게임을 새로 시작하려면 1, 종료하려면 2를 입력하세요.'

- 에러 문구
  ERROR_DUPLE: '[ERROR] 숫자가 중복 되어 프로그램이 종료 됩니다.'
  ERROR_LENGTH: '[ERROR] 3개의 숫자가 아니므로 프로그램이 종료 됩니다.'
  ERROR_RANGE: '[ERROR] 1부터 9까지의 숫자가 아니므로 프로그램이 종료 됩니다.'
  ERROR_GAME_OVER: '[Error] 알맞은 숫자가 아니므로 프로그램이 종료 됩니다.'

---

1. 게임 시작 문구 출력

- 처음 게임 시작시에만 (랜덤 숫자가 들어있는 배열이 비어 있을 경우에만 문구 출력)
- GAME_START 문구 출력

2. 랜덤 숫자 값 생성

- @woowacourse/mission-utils 라이브러리 Random API 사용
- 1부터 9까지의 랜덤 숫자를 생성 후 배열 안에 넣기

3. 숫자 입력 문구 출력 후 사용자 입력 받기

- Console.readLine 사용해서 문구 출력 및 입력 받기
- consturctor - 콜백 받은 함수 바인드 하기
- INPUT_NUMBER 문구 출력

4. 콜백에서 사용자 입력 받은 숫자로 알맞은 메서드로 순서대로 이동

- 처음 입력 받은 값 : string 에서 문자열 하나씩 나누고, Number로 바꾸기
- 숫자 알맞은 값인지 확인 후 에러 발생
  - 숫자 3개인지 확인
  - 숫자 중복 확인
  - 숫자 1부터 9까지 인지 확인
- 스트라이크 개수 확인
- 볼 개수 확인
- 볼, 스트라이크,낫싱 출력
- 3스트라이크 일때, 아닐때 기능
  - 3스트라이크 일때, 게임 재시작 문구 출력 및 입력받고 기능 호출하는 메서드로 이동
  - 3스트라이크가 아닐 때, 숫자 3개 입력 받는 메서드로 이동
- 스트라이크 일때, 게임 재시작 문구 출력 및 입력받고 기능 호출
  - "3개의 숫자를 모두 맞히셨습니다! 게임 종료" 출력
  - MissionUtils.Console.readLine("게임을 새로 시작하려면 1, 종료하려면 2를 입력하세요." ,콜백)
    - consturctor : 콜백 받은 함수 바인드 하기
    - "1" 입력했을 때 : this.play() 다시 처음부터 시작
    - "2" 입력했을 때 : Console.close() 프로그램 종료
    - 1,2 가 아닌 다른 값을 입력 했을때 : throw Error 에러발생 시키기
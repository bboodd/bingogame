Vue.js로 만드는 빙고게임 요구사항 정리

1. 옵저버패턴 적용
게임 진행자 (플레이어 뽑기, 콜, 시작, 종료)
|\
|  \
|    \
|      \
|        \
플레이어    플레이어 
(숫자판 생성, 숫자판 색칠, 빙고시 진행자에게 알림)

abstract Observerable{
    receive()
    register()
    notifyAll()
}

abstract Observer{
    update()
}

2. 예외처리

1.최대 플레이어는 10명
2.최소 플레이어는 2명

3. 기능

1.플레이어추가 버튼 클릭시 빙고판을 가지는 플레이어 하나 추가(v)
2.게임시작 버튼 클릭시 리셋버튼이 생기며 게임시작(x)
3.리셋 버튼 클릭시 리셋(x)
4.1빙고일시 게임 종료(x)   



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

최대 플레이어는 10명


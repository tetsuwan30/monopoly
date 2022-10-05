## ゲーム進行
``` mermaid
graph LR
    startGame((ゲーム<br/>開始))
    startGame --> turn

    subgraph game
        turn[[プレイヤーの<br/>ターン]]
        checkPlayerList[残ったプレイヤーは<br/>1人 ?]
        turn --> checkPlayerList
        checkPlayerList -->|No| chngePlayer[次のプレイヤーに<br/>交代]
        chngePlayer --> turn
    end

    gameEnd((ゲーム<br/>終了))
    checkPlayerList -->|Yes| gameEnd

```
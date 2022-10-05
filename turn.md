### プレイヤーのターン
``` mermaid
graph LR
    turnStart((ターン<br/>開始)) --> checkJail{刑務所 ?}
    subgraph turn
        checkJail -->|No| dice[ダイスを<br/>振る]
        checkJail -->|Yes| checkJailPay{保釈金を<br/>支払う ?}
        checkJailPay -->|Yes| jailPay[保釈金を<br/>支払う]
        checkJailPay -->|No| dice
        jailPay --> dice
        dice --> checkDice3Times{ダイス<br/>3回目 ?}
        checkDice3Times -->|Yes| checkDice3TimesDouble{3回目<br/>ぞろ目 ?}
        checkDice3Times -->|No| move[ダイスの目の数だけ移動]
        checkDice3TimesDouble -->|Yes| goToJail[刑務所へ行く]
        checkDice3TimesDouble -->|No| move
        move --> action[[マスの指示]]
        action --> checkDiceDouble{ぞろ目 ?}
        checkDiceDouble -->|Yes| dice
    end

    turnEnd((ターン<br/>終了))
    goToJail --> turnEnd
    checkDiceDouble -->|No| turnEnd

```
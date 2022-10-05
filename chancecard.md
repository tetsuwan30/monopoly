#### チャンスカード
``` mermaid
graph LR
    startChanceCard((チャンスカードの<br/>開始))
    startChanceCard --> CheckChanceCard{どのカードを<br/>引いた ?}

    subgraph チャンスカード
        CheckChanceCard --> advanceToStCharlesPlace[セントチャールズプレースへ進む]
        CheckChanceCard --> advanceToIllinoisAvenue[イリノイ通りへ進む]
        CheckChanceCard --> advanceToBoardwalk[ボードウォークへ進む]
        CheckChanceCard --> advanceToReadingRailroad[リーディング鉄道へ進む]
        CheckChanceCard --> advanceToNextRailroad[次の鉄道まで進み 通常の2倍のレンタル料を支払う]
        CheckChanceCard --> advanceToNextUtility[次の水道会社か電力会社に進む]
        CheckChanceCard --> goBackThreeSpaces[3マス戻る]
        CheckChanceCard --> advanceToGo[GOのマスへ進む]
        CheckChanceCard --> goToJail[刑務所へ行く]        
        CheckChanceCard --> get150FromBank[銀行より$150受取る]
        CheckChanceCard --> get50FromBank[銀行より$50受取る]
        CheckChanceCard --> pay15ToBank[銀行へ$15支払う]
        CheckChanceCard --> pay50ToPlyaers[各プレーヤーに$50支払う]
        CheckChanceCard --> pay25forHouse100ForHotel[修理費 家1軒あたり$25 ホテル1軒あたり$100を支払う]
        CheckChanceCard --> getOutOfJailFreeCard[刑務所から釈放]
    end

    advanceToStCharlesPlace --> move[指定のマスに移動]
    advanceToIllinoisAvenue --> move[指定のマスに移動]
    advanceToBoardwalk --> move[指定のマスに移動]
    advanceToReadingRailroad --> move[指定のマスに移動]
    advanceToNextRailroad --> move[指定のマスに移動]
    advanceToNextUtility --> move[指定のマスに移動]
    goBackThreeSpaces --> move[指定のマスに移動]
    advanceToGo --> move[指定のマスに移動]
    goToJail --> move[指定のマスに移動]

    move --> checkGoThrough{Goマスを過ぎたか}
    checkGoThrough -->|Yes| pay[支払]

    get150FromBank --> get[収入]
    get50FromBank --> get[収入]
    pay15ToBank --> pay[支払]
    pay50ToPlyaers --> pay[支払]
    pay25forHouse100ForHotel --> pay[支払]

    action[[マスの指示]]
    checkGoThrough -->|No| action
    pay --> action

    endChanceCard((チャンスカードの<br/>終了))
    get --> endChanceCard
    getOutOfJailFreeCard --> endChanceCard
    action --> endChanceCard
```
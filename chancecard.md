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
        CheckChanceCard --> getOutOfJailFreeCard[刑務所から釈放カードを受け取る]
    end

    advanceToStCharlesPlace --> checkGoThrough
    advanceToIllinoisAvenue --> checkGoThrough
    advanceToBoardwalk --> checkGoThrough
    advanceToReadingRailroad --> checkGoThrough
    advanceToNextRailroad --> checkGoThrough
    advanceToNextUtility --> checkGoThrough

    checkGoThrough{Goマスを過ぎたか}
    checkGoThrough -->|Yes| get200FromBank[銀行より$200受取る]
    checkGoThrough -->|No| move

    move[指定のマスに移動]
    advanceToGo --> move
    goToJail --> move
    goBackThreeSpaces --> move
    get200FromBank --> move

    move --> action
    
    get[収入]
    get150FromBank --> get
    get50FromBank --> get

    pay[支払]
    pay15ToBank --> pay
    pay50ToPlyaers --> pay
    pay25forHouse100ForHotel --> pay

    action[[マスの指示]]

    endChanceCard((チャンスカードの<br/>終了))
    get --> endChanceCard
    pay --> endChanceCard
    getOutOfJailFreeCard --> endChanceCard
    action --> endChanceCard
```
### マスのイベント
``` mermaid
graph LR
    startEvent((マスのイベント<br/>開始)) 
    startEvent --> checkSquare{どのマスに<br/>止まったか ?}

    get[収入]
    go --> get

    pay[支払]
    checkPropertySoldOut -->|Yes| pay
    incomeTax --> pay
    luxuryTax --> pay

    subgraph マス
        checkSquare{どのマスに<br/>止まったか ?}
        checkSquare --> jail[刑務所]
        checkSquare --> freeParking[フリーパーキング]
        checkSquare --> incomeTax[所得税] 
        checkSquare --> luxuryTax[物品税] 
        checkSquare --> go[Go]
        checkSquare --> cardCommunityChest[[共同基金]]
        checkSquare --> cardChance[[チャンスカード]]
        checkSquare --> goToJail[刑務所へ行く]
        checkSquare --> property[物件]
    end

    subgraph 物件
        property --> checkPropertySoldOut{既に購入<br/>されているか ?}
        checkPropertySoldOut -->|No| checkBuy{購入するか ?}
        checkBuy-->|Yes| buy[購入]
        checkBuy-->|No| auction[競売]
    end

    endEvent((マスの指示<br/>終了))

    jail --> endEvent
    freeParking --> endEvent
    goToJail --> endEvent
    cardCommunityChest --> endEvent
    cardChance --> endEvent
    buy --> endEvent
    auction --> endEvent
    pay --> endEvent
    get --> endEvent
```
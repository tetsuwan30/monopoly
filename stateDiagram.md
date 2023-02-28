- [共同基金カード](#共同基金カード)
- [救済](#救済)
  





#### 共同基金カード
#### 救済

``` mermaid
graph LR
    payStart((支払<br/>開始))
    payEnd((支払<br/>終了))

    payStart --> checkPlayerBankruptcy{プライヤーは<br/>破産していない ?}
    checkPlayerBankruptcy -->|Yes| checkRelief[他のプレイヤーが<br/>救済する ?]


```
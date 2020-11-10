## 下拉式同意書條款須看完，才可勾選同意，才可下一步
### 解法: 以execute script來做
    {
      "id": "23773b0a-b265-42d8-a909-d2dfb9cc08f7",
      "comment": "",
      "command": "executeScript",
      "target": "document.getElementsByClassName('content')[0].scrollIntoView({ behavior: 'smooth', block: 'end' })",
      "targets": [],
      "value": ""
    }


## store變數
### 解法: 以store來做，value為變數名稱，target是變數值
    {
      "id": "4ee75c79-9884-4268-bca5-c3ecf93288da",
      "comment": "20200421-簡易型歷史No",
      "command": "store",
      "target": "92",
      "targets": [],
      "value": "HistoryNo"
    }


## wait or pause
### 解法有很多，官方最推薦waitForElementVisible，但有時簡單粗暴的pause更能明快解決問題
    {
      "id": "a4bf513b-9f3f-4f67-a58d-d71bebfcfe64",
      "comment": "",
      "command": "waitForElementVisible",
      "target": "xpath=(//a[contains(text(),'閱覽')])[${HistoryNo}]",
      "targets": [],
      "value": "30000"
    },{
      "id": "0e64d127-0300-4a34-956f-29ea72a63a31",
      "comment": "",
      "command": "pause",
      "target": "1000",
      "targets": [],
      "value": ""
    }


## verify
### 解法: verifyText最常用，target設定為該dom物件(的值)，value則手動設定應有的值
    {
      "id": "e7acebd9-326f-4bb7-87aa-78ecd492066b",
      "comment": "",
      "command": "verifyText",
      "target": "css=p.type",
      "targets": [],
      "value": "穩健型"
    }, {
      "id": "a13d8ff8-c6fb-44a1-b8db-2d759e6ab11c",
      "comment": "",
      "command": "verifyText",
      "target": "id=display-insurance",
      "targets": [],
      "value": "富邦人壽新吉祥變額萬能終身壽險（ A 型、 B 型）"
    }, {
      "id": "b3b29c04-95f2-4b25-b017-a0f75623723a",
      "comment": "",
      "command": "verifyText",
      "target": "id=Update",
      "targets": [],
      "value": "${dataDate}"
    }


## 下拉式選單時，Targets盡量選擇 "包含XX文字"
### 相較Xpath或其他selector，這種作法在檢視腳本時較直觀，也可避免不重要的html結構變化影響腳本。
    {
      "id": "f20e1987-5975-40f9-9472-52fce0efc425",
      "comment": "",
      "command": "click",
      "target": "xpath=//li[contains(.,'對金融商品和投資風險有進一步認識，並明白影響價格的因素')]",
      "targets": [
        ["css=.long-answer .option:nth-child(2)", "css:finder"],
        ["xpath=//div[2]/div/div/div[2]/div/div/ul/li[2]", "xpath:position"],
        ["xpath=//li[contains(.,'對金融商品和投資風險有進一步認識，並明白影響價格的因素')]", "xpath:innerText"]
      ],
      "value": ""
    }


## 變數分離
### 可將所有測試時要手動設定的變數析離到另一個Test Suites，以便集中設定
  "suites": [{
    "id": "faf6d461-1a32-4ce4-9cec-6564b044aa4a",
    "name": "Default Suite",
    "persistSession": false,
    "parallel": false,
    "timeout": 300,
    "tests": ["da76ce89-1861-4824-8888-2c2fe72d7dc4"]
  }, {
    "id": "6b919118-8cc1-4f10-8271-d0d0d9f6fece",
    "name": "01_人壽完整型測試",
    "persistSession": false,
    "parallel": false,
    "timeout": 300,
    "tests": ["3966a72a-9fe5-4d3a-9c3c-5049a929013d", "da76ce89-1861-4824-8888-2c2fe72d7dc4"]
  }]


## select window，要先在開視窗的click指令進行window config

## 修改原Test沒有用，重新錄一個Test可以，但指令一模一樣，有時可以試試 (我碰到時忘記做*.side source json比對，若下次有碰到可以比對觀察看看)

## break point: 開發測試腳本時要善用此功能

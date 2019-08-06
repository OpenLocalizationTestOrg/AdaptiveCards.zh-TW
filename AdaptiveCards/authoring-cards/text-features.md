---
title: 文字功能
author: matthidinger
ms.author: mahiding
ms.date: 11/09/2017
ms.topic: article
ms.openlocfilehash: f7ea40b80df4d976c0a8a86b15254018fdf2fac6
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732670"
---
# <a name="text-features"></a>文字功能

`TextBlock`提供一些用來格式化和當地語系化文字的先進功能。

## <a name="markdown"></a>Markdown
為了支援內嵌標記, 調適型卡片支援 Markdown 語法的**子集**。

_支援_

| 文字樣式      | Markdown |
|-----------------|-----|
| **粗體**        | ```**Bold**``` |
| _斜體_        | ```_Italic_``` |
| 專案符號清單     | ```- Item 1\r- Item 2\r- Item 3``` | 
| 編號清單   | ```1. Green\r2. Orange\r3. Blue``` |
| 指向      | ```[Title](url)``` |

_不支援_

* 頁首
* 資料表
* 影像
* 上表中沒有任何專案

### <a name="markdown-example"></a>Markdown 範例

下列承載會轉譯如下的內容:

![markdown 螢幕擷取畫面](media/text-features/markdown.png)

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a>日期/時間格式和當地語系化

有時您不會知道接收卡片的使用者所在的時區, 因此調適型`DATE()`卡片`TIME()`會提供和格式化功能, 以自動將目標裝置上的時間當地語系化。

### <a name="datetime-example"></a>日期/時間範例

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Your package will arrive on {{DATE(2017-02-14T06:00:00Z, SHORT)}} at {{TIME(2017-02-14T06:00:00Z)}}",
            "wrap": true
        }
    ]
}
```

上述卡片將會顯示: 

> **您的套件將會在上午6:00 的星期二抵達2017年2月14日**

### <a name="datetime-function-rules"></a>日期/時間函數規則

有一些規則可適當解讀每個平臺上的日期/時間函數。 如果不符合規則, 則會向使用者顯示原始字串, 而且不會有任何人想要的。

1. 區分**大小寫**(必須全部為大寫)
1. `{{` 、`}}`或括弧之間沒有空格
1. **嚴格的[RFC 3389](https://tools.ietf.org/html/rfc3339)格式**(請參閱下列範例)
1. **必須是**有效的日期和時間

### <a name="valid-formats"></a>有效的格式

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a>日期格式化參數

針對日期, 可以指定選擇性的參數來格式化輸出。


|       格式        |            範例            |
|---------------------|-------------------------------|
| `COMPACT`預設 |          "2/13/2017"          |
|       `SHORT`       |     「2017年2月13日星期一」     |
|       `LONG`        | 「2017年2月13日星期一」 |


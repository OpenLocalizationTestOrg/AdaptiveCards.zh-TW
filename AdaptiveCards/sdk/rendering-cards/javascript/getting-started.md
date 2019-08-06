---
title: JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 55360658d74ca384b0e6090631a7f5db463e968a
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732905"
---
# <a name="getting-started---javascript"></a>開始使用-JavaScript

如我們在[消費者入門](../../../authoring-cards/getting-started.md)頁面中所述, 調適型卡片是 JSON 序列化的卡片物件模型。 這是用來在瀏覽器中產生用戶端 HTML 的 JavaScript SDK。

> [!IMPORTANT]
> **來自 v 0.5 的重大變更**
> 
> 1. 套件已從`microsoft-adaptivecards`重新命名為`adaptivecards`
> 1. 靜態`AdaptiveCards.setHostConfig()`已移至的實例`AdaptiveCard`成員。 例如,`myCard.hostConfig = {}` 
> 1. `HostConfig`已有各種不同的重新命名和移動。 請參閱目前結構的[範例 json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json)主機設定
> 1. 這裡也有一些來自 v 0.5 preview 的架構變更, 如下所[述](https://github.com/Microsoft/AdaptiveCards/pull/633)
> 1. 已移除`renderCard()`靜態函式, 因為它與類別方法是多餘的。 使用`adaptiveCard.render()` , 如下所述。 


## <a name="install"></a>安裝

### <a name="node"></a>節點

[![npm 安裝](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)

```console
npm install adaptivecards --save
```

### <a name="cdn"></a>CDN

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a>使用量

### <a name="import-the-module"></a>匯入模組

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a>後續步驟

請參閱[呈現卡片](render-a-card.md)以進行後續步驟!

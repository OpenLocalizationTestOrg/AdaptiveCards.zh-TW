---
title: 主機設定-JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: a011ffc43c2990cd8eb568b9f1c449cf541f9a70
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732895"
---
# <a name="host-config---javascript"></a>主機設定-JavaScript

```js
// Create an AdaptiveCard instance
var adaptiveCard = new AdaptiveCards.AdaptiveCard();

// Set its hostConfig property unless you want to use the default Host Config
// Host Config defines the style and behavior of a card
adaptiveCard.hostConfig = new AdaptiveCards.HostConfig({
    fontFamily: "Segoe UI, Helvetica Neue, sans-serif"
    // More host config options
});

// Render the card to an HTML element:
var renderedCard = adaptiveCard.render();
```

## <a name="customization"></a>自訂

有三種方式可自訂調適型卡片呈現: 
1. 主機設定
2. CSS 樣式
3. 自訂元素呈現

### <a name="hostconfig"></a>HostConfig 

[主機](../../../rendering-cards/host-config.md)設定是所有轉譯器都瞭解的共用設定物件。 這可讓您定義每個平臺轉譯器會自動解讀的通用樣式 (例如, 字型系列、字型大小、預設間距) 和行為 (例如動作數目上限)。 

目標是每個平臺轉譯器所產生的原生 UI 看起來非常類似于您的最小工作。

```javascript
var renderOptions = {
    ...
    hostConfig: {
        // Define your host config object here
        // See the HostConfig docs for details
    }
};
```
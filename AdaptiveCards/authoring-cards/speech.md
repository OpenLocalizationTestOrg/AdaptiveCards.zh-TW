---
title: 語音和自訂
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 468d090dff0511f40cb7e5eedc4f4a18fa12aa3c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732665"
---
# <a name="speech-and-advanced-customization"></a>語音和自訂
我們居住在透過 Cortana 等服務的語音互動時代。  調適型卡片是從第一天到支援語音的設計, 可實現酷炫的新手滿案例。

此`speak`標籤可將調適型卡片傳遞至視覺顯示不是主要體驗的環境, 例如駕駛時的汽車儀表板。 

## <a name="speak-property"></a>說話屬性
為支援語音, 我們有`speak`一個屬性, 其中包含要向使用者顯示的文字。 文字可以使用語音合成標記語言 ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)) 來標注。 SSML 控制語音的速度、音調和變化。  它甚至可讓您從自己的服務串流音訊或轉譯 TTS 音訊串流, 讓您有絕佳的自訂彈性。

有兩種模式可供主應用程式用來說屬性使用方式:

* **傳遞**時-當卡片交付時, 用戶端可能會選擇讀取卡片的 [說話] 屬性, 以描述整個卡片。
* 依**需求**-為了支援更豐富的協助工具模型, 架構支援每個元素的「說出」標記。 用戶端可能會針對卡片中的每個元素讀取說話屬性。

### <a name="examples"></a>範例

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a>語音內容設計

針對語音設計的內容不同于針對視覺效果顯示而設計的內容。 當您設計卡片時, 您會設計整個視覺體驗, 以樂趣使用者的方式呈現資訊給使用者。 設計語音時, 您應該考慮如何 verbally 以樂趣使用者的方式描述內容。  

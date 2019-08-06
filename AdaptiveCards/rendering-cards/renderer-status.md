---
title: 轉譯器狀態
author: matthidinger
ms.author: mahiding
ms.date: 10/12/2018
ms.topic: article
ms.openlocfilehash: 63426b2250407cc40af8c46975c10f57d1028a40
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733085"
---
# <a name="renderer-status"></a>轉譯器狀態
下表根據公開發行的版本顯示每個轉譯器的目前狀態。

### <a name="parsing"></a>正在剖析

|功能 | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|傳回驗證失敗 | ✅ | ✅ | ✅ | ✅ | ✅ |
|剖析未知的屬性 | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="card-rendering"></a>卡片轉譯

|功能 | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|檢查支援的版本 | ✅ | ✅ | ✅ | ✅ | ✅  |
|轉譯完整架構 | ✅ | ✅ | ✅ | ✅ | ✅ |
|呈現動作列 | ✅ | ✅ | ✅ | ✅ | ✅ |
|忽略未知的元素 | ✅ | ✅ | ✅ | ✅ | ✅ |
|主機設定支援 | ✅ | ✅ | ✅ | ✅ | ✅ |
|原生平臺樣式 | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="element-rendering"></a>元素呈現

|功能 | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|間距和分隔符號 | ✅ | ✅ | ✅ | ✅ | ✅ |
|[TextBlock 日期/時間格式](../authoring-cards/text-features.md#datetime-formatting-and-localization) | ✅ | ✅ | ✅ | ✅ | ✅ |
|[TextBlock Markdown 支援](../authoring-cards/text-features.md#markdown) | ✅* | ✅ | ✅ | ✅ | ✅ |
|完整輸入支援 | ✅ | ✅ | ✅ | ✅ | ✅ |

\*HTML 轉譯器不包含內建的 Markdown 支援, 可將程式庫大小降至最低, 並讓取用應用程式使用其慣用的 Markdown 處理器。 不過, 如果載入, HTML 轉譯器會自動使用 Markdown。

### <a name="extensibility"></a>擴充性

|功能 | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|覆寫元素轉譯器 | ✅ | ✅ | ✅ | ✅ | ✅ |
|加入新的元素轉譯器 | ✅ | ✅ | ✅ | ✅ | ✅ |
|移除元素轉譯器 | ✅ | ✅ | ✅ | ✅ | ✅ |
|[覆寫/新增/移除動作轉譯器](https://github.com/Microsoft/AdaptiveCards/issues/1671) | ✅ | ✅ | ❌ | ✅ | ✅ |

### <a name="actions"></a>動作

| 功能 | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
| 動作。 OpenUrl 支援人員 | ✅ | ✅ | ✅ | ✅ | ✅  |
| 動作。 ShowCard 支援人員  | ✅ | ✅ | ✅ | ✅ | ✅ |
| 動作。提交支援  | ✅ | ✅ | ✅ | ✅ | ✅  |
| selectAction 支援 | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="events"></a>事件

|       功能        | HTML | .NET | UWP | iOS | Android | 
|----------------------------|------|------|-----|-----|---------|
| 元素可見度已變更 |  ✅   |  ❌   |  ❌  |  ❌  | ❌ |


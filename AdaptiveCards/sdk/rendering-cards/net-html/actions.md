---
title: 動作-.NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: f577c0bab73e2bd1f75bb22dd7a41a7dbfd63307
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732850"
---
# <a name="actions---net-html"></a>動作-.NET HTML

最上層的卡片`actions`將會轉譯為 HTML `<button>`。 由於這是伺服器端程式庫, 因此您可以在按下按鈕時, 將用戶端事件處理常式連線。 HTML `<button>`中的每個都有屬性, 可讓您用來連接適當的行為。

有些元素具有`selectAction`屬性 (容器、資料行、影像), 使其可叫用。 如果元素具有`selectAction`轉譯器`ac-selectable`, 則會加入的 CSS 類別以及下列屬性。

動作類型 | CSS 類別 | 其他屬性
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | `data-ac-url`(來自卡片的屬性)`url`
`Action.Submit` | `ac-action-submit` | `data-ac-data`(來自卡片的屬性)`data`
`Action.ShowCard` | `ac-action-showCard` | `data-ac-showcardid``id` (`<div>`包含內部卡片的)
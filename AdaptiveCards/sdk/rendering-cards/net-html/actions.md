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
# <a name="actions---net-html"></a><span data-ttu-id="827bc-102">動作-.NET HTML</span><span class="sxs-lookup"><span data-stu-id="827bc-102">Actions - .NET HTML</span></span>

<span data-ttu-id="827bc-103">最上層的卡片`actions`將會轉譯為 HTML `<button>`。</span><span class="sxs-lookup"><span data-stu-id="827bc-103">Top-level card `actions` will render as an HTML `<button>`.</span></span> <span data-ttu-id="827bc-104">由於這是伺服器端程式庫, 因此您可以在按下按鈕時, 將用戶端事件處理常式連線。</span><span class="sxs-lookup"><span data-stu-id="827bc-104">Since this is a server-side library it's up to you to wire up client-side event handlers when buttons are pressed.</span></span> <span data-ttu-id="827bc-105">HTML `<button>`中的每個都有屬性, 可讓您用來連接適當的行為。</span><span class="sxs-lookup"><span data-stu-id="827bc-105">Each `<button>` in the HTML will have attributes that you can use to wire up the proper behavior.</span></span>

<span data-ttu-id="827bc-106">有些元素具有`selectAction`屬性 (容器、資料行、影像), 使其可叫用。</span><span class="sxs-lookup"><span data-stu-id="827bc-106">Some elements have a `selectAction` property (Container, Columns, Image) which makes them invokable.</span></span> <span data-ttu-id="827bc-107">如果元素具有`selectAction`轉譯器`ac-selectable`, 則會加入的 CSS 類別以及下列屬性。</span><span class="sxs-lookup"><span data-stu-id="827bc-107">If an element has a `selectAction` the renderer will add a CSS class of `ac-selectable`, along with the below attributes.</span></span>

<span data-ttu-id="827bc-108">動作類型</span><span class="sxs-lookup"><span data-stu-id="827bc-108">Action Type</span></span> | <span data-ttu-id="827bc-109">CSS 類別</span><span class="sxs-lookup"><span data-stu-id="827bc-109">CSS class</span></span> | <span data-ttu-id="827bc-110">其他屬性</span><span class="sxs-lookup"><span data-stu-id="827bc-110">Additional attributes</span></span>
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | <span data-ttu-id="827bc-111">`data-ac-url`(來自卡片的屬性)`url`</span><span class="sxs-lookup"><span data-stu-id="827bc-111">`data-ac-url` (the `url` property from the card)</span></span>
`Action.Submit` | `ac-action-submit` | <span data-ttu-id="827bc-112">`data-ac-data`(來自卡片的屬性)`data`</span><span class="sxs-lookup"><span data-stu-id="827bc-112">`data-ac-data` (the `data` property from the card)</span></span>
`Action.ShowCard` | `ac-action-showCard` | <span data-ttu-id="827bc-113">`data-ac-showcardid``id` (`<div>`包含內部卡片的)</span><span class="sxs-lookup"><span data-stu-id="827bc-113">`data-ac-showcardid` (the `id` of the `<div>` containing the inner card)</span></span>
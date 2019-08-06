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
# <a name="getting-started---javascript"></a><span data-ttu-id="2dfa3-102">開始使用-JavaScript</span><span class="sxs-lookup"><span data-stu-id="2dfa3-102">Getting started - JavaScript</span></span>

<span data-ttu-id="2dfa3-103">如我們在[消費者入門](../../../authoring-cards/getting-started.md)頁面中所述, 調適型卡片是 JSON 序列化的卡片物件模型。</span><span class="sxs-lookup"><span data-stu-id="2dfa3-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="2dfa3-104">這是用來在瀏覽器中產生用戶端 HTML 的 JavaScript SDK。</span><span class="sxs-lookup"><span data-stu-id="2dfa3-104">This is a JavaScript SDK for generating client-side HTML in the browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2dfa3-105">**來自 v 0.5 的重大變更**</span><span class="sxs-lookup"><span data-stu-id="2dfa3-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="2dfa3-106">套件已從`microsoft-adaptivecards`重新命名為`adaptivecards`</span><span class="sxs-lookup"><span data-stu-id="2dfa3-106">Package renamed from `microsoft-adaptivecards` to `adaptivecards`</span></span>
> 1. <span data-ttu-id="2dfa3-107">靜態`AdaptiveCards.setHostConfig()`已移至的實例`AdaptiveCard`成員。</span><span class="sxs-lookup"><span data-stu-id="2dfa3-107">The static `AdaptiveCards.setHostConfig()` has been moved to an instance member of `AdaptiveCard`.</span></span> <span data-ttu-id="2dfa3-108">例如,`myCard.hostConfig = {}`</span><span class="sxs-lookup"><span data-stu-id="2dfa3-108">E.g., `myCard.hostConfig = {}`</span></span> 
> 1. <span data-ttu-id="2dfa3-109">`HostConfig`已有各種不同的重新命名和移動。</span><span class="sxs-lookup"><span data-stu-id="2dfa3-109">`HostConfig` has gone though various renames and moves.</span></span> <span data-ttu-id="2dfa3-110">請參閱目前結構的[範例 json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json)主機設定</span><span class="sxs-lookup"><span data-stu-id="2dfa3-110">See the [sample.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) Host Config for current structure</span></span>
> 1. <span data-ttu-id="2dfa3-111">這裡也有一些來自 v 0.5 preview 的架構變更, 如下所[述](https://github.com/Microsoft/AdaptiveCards/pull/633)</span><span class="sxs-lookup"><span data-stu-id="2dfa3-111">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>
> 1. <span data-ttu-id="2dfa3-112">已移除`renderCard()`靜態函式, 因為它與類別方法是多餘的。</span><span class="sxs-lookup"><span data-stu-id="2dfa3-112">The static `renderCard()` function was removed as it was redundant with the class methods.</span></span> <span data-ttu-id="2dfa3-113">使用`adaptiveCard.render()` , 如下所述。</span><span class="sxs-lookup"><span data-stu-id="2dfa3-113">Use `adaptiveCard.render()` as described below.</span></span> 


## <a name="install"></a><span data-ttu-id="2dfa3-114">安裝</span><span class="sxs-lookup"><span data-stu-id="2dfa3-114">Install</span></span>

### <a name="node"></a><span data-ttu-id="2dfa3-115">節點</span><span class="sxs-lookup"><span data-stu-id="2dfa3-115">Node</span></span>

<span data-ttu-id="2dfa3-116">[![npm 安裝](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span><span class="sxs-lookup"><span data-stu-id="2dfa3-116">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span></span>

```console
npm install adaptivecards --save
```

### <a name="cdn"></a><span data-ttu-id="2dfa3-117">CDN</span><span class="sxs-lookup"><span data-stu-id="2dfa3-117">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a><span data-ttu-id="2dfa3-118">使用量</span><span class="sxs-lookup"><span data-stu-id="2dfa3-118">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="2dfa3-119">匯入模組</span><span class="sxs-lookup"><span data-stu-id="2dfa3-119">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a><span data-ttu-id="2dfa3-120">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2dfa3-120">Next steps</span></span>

<span data-ttu-id="2dfa3-121">請參閱[呈現卡片](render-a-card.md)以進行後續步驟!</span><span class="sxs-lookup"><span data-stu-id="2dfa3-121">See [Render a card](render-a-card.md) for the next steps!</span></span>

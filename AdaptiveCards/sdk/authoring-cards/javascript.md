---
title: 調適型卡片的 JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 07/26/2019
ms.topic: article
ms.openlocfilehash: 4ddff841ec073c60a8aa6184f309e94052cb002d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732550"
---
# <a name="javascript-sdk-for-creating-cards"></a><span data-ttu-id="8c27e-102">建立卡片的 JavaScript SDK</span><span class="sxs-lookup"><span data-stu-id="8c27e-102">JavaScript SDK for creating cards</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c27e-103">序列化 JSON 的程式庫仍在開發中, 而您的 milage 可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="8c27e-103">The library for serializing JSON is still in development and your milage may vary.</span></span>

<span data-ttu-id="8c27e-104">如我們在[消費者入門](../../authoring-cards/getting-started.md)中所述, 調適型卡片只是卡片物件模型的序列化 JSON 物件。</span><span class="sxs-lookup"><span data-stu-id="8c27e-104">As we described in the [Getting Started](../../authoring-cards/getting-started.md), an Adaptive Card is nothing more than a serialized JSON object of a card object model.</span></span>  <span data-ttu-id="8c27e-105">為了讓操作物件模型變得更容易, 我們定義了一些程式庫, 定義了可輕鬆序列化/還原序列化 json 的強型別類別階層。</span><span class="sxs-lookup"><span data-stu-id="8c27e-105">To make it easy to manipulate the object model we have defined some libraries which define a strongly typed class hierarchy that is easy to serialize/deserialize json.</span></span>

<span data-ttu-id="8c27e-106">您可以使用任何您想要建立調適型卡片 json 的工具。</span><span class="sxs-lookup"><span data-stu-id="8c27e-106">You can use any tooling that you want to create the adaptive card json.</span></span>

<span data-ttu-id="8c27e-107">`adaptivecards` Npm 套件會定義可在 javascript 中使用調適型卡片的程式庫</span><span class="sxs-lookup"><span data-stu-id="8c27e-107">The `adaptivecards` npm package defines a library for working with adaptive cards in javascript</span></span>

## <a name="to-install"></a><span data-ttu-id="8c27e-108">安裝</span><span class="sxs-lookup"><span data-stu-id="8c27e-108">To install</span></span>
```console
npm install adaptivecards
```

## <a name="example"></a><span data-ttu-id="8c27e-109">範例</span><span class="sxs-lookup"><span data-stu-id="8c27e-109">Example</span></span>

<span data-ttu-id="8c27e-110">下列 API 顯示如何使用物件模型來建立調適型卡片, 並將其序列化為 JSON。</span><span class="sxs-lookup"><span data-stu-id="8c27e-110">The following API shows how to construct an Adaptive Card using the object model and serialize it to JSON.</span></span>

```typescript
let card = new Adaptive.AdaptiveCard();
card.version = new Adaptive.Version(1, 0);

let textBlock = new Adaptive.TextBlock();
textBlock.text = "Hello World";

card.addItem(textBlock);

let json = card.toJSON();
```

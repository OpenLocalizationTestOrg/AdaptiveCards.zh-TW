---
title: 呈現卡片-UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: d7e101bbabfccf162797a3a8e154028f29bdc84b
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732545"
---
# <a name="render-a-card---uwp"></a><span data-ttu-id="f4d4e-102">呈現卡片-UWP</span><span class="sxs-lookup"><span data-stu-id="f4d4e-102">Render a card - UWP</span></span>

<span data-ttu-id="f4d4e-103">以下說明如何使用 UWP SDK 來呈現卡片。</span><span class="sxs-lookup"><span data-stu-id="f4d4e-103">Here's how to render a card using the UWP SDK.</span></span>

## <a name="create-an-instance-of-your-renderer"></a><span data-ttu-id="f4d4e-104">建立轉譯器的實例</span><span class="sxs-lookup"><span data-stu-id="f4d4e-104">Create an instance of your renderer</span></span>

<span data-ttu-id="f4d4e-105">建立轉譯器程式庫的實例。</span><span class="sxs-lookup"><span data-stu-id="f4d4e-105">Create an instance of the renderer library.</span></span> 

```csharp
using AdaptiveCards.Rendering.Uwp;
// ...

var renderer = new AdaptiveCardRenderer();
```

## <a name="create-a-card-from-a-json-string"></a><span data-ttu-id="f4d4e-106">從 JSON 字串建立卡片</span><span class="sxs-lookup"><span data-stu-id="f4d4e-106">Create a card from a JSON string</span></span>

```csharp
var card = AdaptiveCard.FromJsonString(jsonString);
```

## <a name="create-a-card-from-a-json-object"></a><span data-ttu-id="f4d4e-107">從 JSON 物件建立卡片</span><span class="sxs-lookup"><span data-stu-id="f4d4e-107">Create a card from a JSON object</span></span>

```csharp
var card = AdaptiveCard.FromJson(jsonObject);
```

## <a name="render-a-card"></a><span data-ttu-id="f4d4e-108">呈現卡片</span><span class="sxs-lookup"><span data-stu-id="f4d4e-108">Render a card</span></span>

<span data-ttu-id="f4d4e-109">從來源取得卡片並加以呈現。</span><span class="sxs-lookup"><span data-stu-id="f4d4e-109">Acquire a card from a source and render it.</span></span>

```csharp
RenderedAdaptiveCard renderedAdaptiveCard =  renderer.RenderAdaptiveCard(card);

// Check if the render was successful
if (renderedAdaptiveCard.FrameworkElement != null)
{
    // Get the framework element
    var uiCard = renderedAdaptiveCard.FrameworkElement;

    // Add it to your UI
    myGrid.Children.Add(uiCard);
}
```

## <a name="example"></a><span data-ttu-id="f4d4e-110">範例</span><span class="sxs-lookup"><span data-stu-id="f4d4e-110">Example</span></span>

<span data-ttu-id="f4d4e-111">以下是來自 UWP 轉譯器的範例。</span><span class="sxs-lookup"><span data-stu-id="f4d4e-111">Here is an example from the UWP renderer.</span></span>

```csharp
var renderer = new AdaptiveCardRenderer();
var card = AdaptiveCard.FromJsonString(jsonString);
var renderedAdaptiveCard = renderer.RenderAdaptiveCard(card.AdaptiveCard);
if (renderedAdaptiveCard.FrameworkElement != null)
{
    myGrid.Children.Add(renderedAdaptiveCard.FrameworkElement);
}
...
```
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
# <a name="render-a-card---uwp"></a>呈現卡片-UWP

以下說明如何使用 UWP SDK 來呈現卡片。

## <a name="create-an-instance-of-your-renderer"></a>建立轉譯器的實例

建立轉譯器程式庫的實例。 

```csharp
using AdaptiveCards.Rendering.Uwp;
// ...

var renderer = new AdaptiveCardRenderer();
```

## <a name="create-a-card-from-a-json-string"></a>從 JSON 字串建立卡片

```csharp
var card = AdaptiveCard.FromJsonString(jsonString);
```

## <a name="create-a-card-from-a-json-object"></a>從 JSON 物件建立卡片

```csharp
var card = AdaptiveCard.FromJson(jsonObject);
```

## <a name="render-a-card"></a>呈現卡片

從來源取得卡片並加以呈現。

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

## <a name="example"></a>範例

以下是來自 UWP 轉譯器的範例。

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
---
title: 呈現卡片-.NET WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 1445754d968ee531dc1e2b1816df1189c286d479
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732715"
---
# <a name="render-a-card---net-wpf"></a>呈現卡片-.NET WPF

以下說明如何使用 .NET WPF SDK 呈現卡片。

> [!NOTE]
> **`Media`使用 HTTPS Url 將無法在 WPF 中使用**
> 
> 由於[WPF MediaElement 控制項中的錯誤](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception), 我們無法轉譯透過 HTTPS 提供的媒體。 在解決此問題之前, 您`Media`應該在元素中使用 HTTP url。  

## <a name="instantiate-a-renderer"></a>具現化轉譯器

建立轉譯器程式庫的實例。 

```csharp
using AdaptiveCards;
using AdaptiveCards.Rendering;
using AdaptiveCards.Rendering.Wpf;
// ...

// Create a card renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// If using the Xceed package, enable the enhanced input
renderer.UseXceedElementRenderers();

// For fun, check the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion;
```

## <a name="render-a-card-to-xaml"></a>將卡片轉譯為 XAML

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard("1.0")
{
    Body = { new AdaptiveTextBlock() { Text = "Hello World" } }
};

try
{
    // Render the card
    RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

    // Get the FrameworkElement
    // Add this to your app's UI somewhere
    FrameworkElement fe = renderedCard.FrameworkElement;

    // (Optional) Check for any renderer warnings
    // This includes things like an unknown element type found in the card
    // Or the card exceeded the maximum number of supported actions, etc
    IList<AdaptiveWarning> warnings = renderedCard.Warnings;
}
catch(AdaptiveException ex)
{
    // Failed rendering
}
```


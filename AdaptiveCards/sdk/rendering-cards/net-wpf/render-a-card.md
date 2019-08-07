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
# <a name="render-a-card---net-wpf"></a><span data-ttu-id="5ff01-102">呈現卡片-.NET WPF</span><span class="sxs-lookup"><span data-stu-id="5ff01-102">Render a card - .NET WPF</span></span>

<span data-ttu-id="5ff01-103">以下說明如何使用 .NET WPF SDK 呈現卡片。</span><span class="sxs-lookup"><span data-stu-id="5ff01-103">Here's how to render a card using the .NET WPF SDK.</span></span>

> [!NOTE]
> <span data-ttu-id="5ff01-104">**`Media`使用 HTTPS Url 將無法在 WPF 中使用**</span><span class="sxs-lookup"><span data-stu-id="5ff01-104">**`Media` with HTTPS URLs will not work in WPF**</span></span>
> 
> <span data-ttu-id="5ff01-105">由於[WPF MediaElement 控制項中的錯誤](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception), 我們無法轉譯透過 HTTPS 提供的媒體。</span><span class="sxs-lookup"><span data-stu-id="5ff01-105">Due to a [bug in the WPF MediaElement control](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) we aren't able to render media that is served via HTTPS.</span></span> <span data-ttu-id="5ff01-106">在解決此問題之前, 您`Media`應該在元素中使用 HTTP url。</span><span class="sxs-lookup"><span data-stu-id="5ff01-106">You should use HTTP URLs in the `Media` element until this is addressed.</span></span>  

## <a name="instantiate-a-renderer"></a><span data-ttu-id="5ff01-107">具現化轉譯器</span><span class="sxs-lookup"><span data-stu-id="5ff01-107">Instantiate a renderer</span></span>

<span data-ttu-id="5ff01-108">建立轉譯器程式庫的實例。</span><span class="sxs-lookup"><span data-stu-id="5ff01-108">Create an instance of the renderer library.</span></span> 

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

## <a name="render-a-card-to-xaml"></a><span data-ttu-id="5ff01-109">將卡片轉譯為 XAML</span><span class="sxs-lookup"><span data-stu-id="5ff01-109">Render a card to XAML</span></span>

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


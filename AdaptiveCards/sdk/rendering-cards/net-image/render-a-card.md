---
title: 呈現卡片-.NET 影像轉譯 SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: d46bd3cba22ffa416edd249f8836db17bc97386f
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732740"
---
# <a name="render-a-card---net-image"></a><span data-ttu-id="f2f4e-102">呈現卡片-.NET 影像</span><span class="sxs-lookup"><span data-stu-id="f2f4e-102">Render a card - .NET Image</span></span>

<span data-ttu-id="f2f4e-103">以下說明如何使用 .NET 映射 SDK 來轉譯卡片。</span><span class="sxs-lookup"><span data-stu-id="f2f4e-103">Here's how to render a card using the .NET Image SDK.</span></span>

```csharp
try
{
    // A URL that returns an Adaptive Card JSON payload
    var cardUrl = "http://adaptivecards.io/payloads/ActivityUpdate.json";

    // Timeout after 30 seconds
    var cts = new CancellationTokenSource(TimeSpan.FromSeconds(30));

    // Get the JSON from the card URL
    var client = new HttpClient();
    var response = await client.GetAsync(cardUrl, cts.Token);
    var json = await response.Content.ReadAsStringAsync();

    // Parse the Adaptive Card JSON
    AdaptiveCardParseResult parseResult = AdaptiveCard.FromJson(json);
    AdaptiveCard card = parseResult.Card;

    // Create a host config with no interactivity 
    // (buttons in images would be deceiving)
    AdaptiveHostConfig hostConfig = new AdaptiveHostConfig()
    {
        SupportsInteractivity = false
    };

    // Create a renderer
    AdaptiveCardRenderer renderer = new AdaptiveCardRenderer(hostConfig);

    // Set any XAML resource Dictionary if you have one
    //renderer.ResourcesPath = <path-to-your-resourcedictionary.xaml>;

    // Render the card to png
    // Set createStaThread to true if running from a server
    RenderedAdaptiveCardImage renderedCard =
        await renderer.RenderCardToImageAsync(card, createStaThread: true, cancellationToken: cts.Token);
}
catch (OperationCanceledException)
{
    // Timed out
}
catch (Exception ex)
{
    // Log failure
}
```
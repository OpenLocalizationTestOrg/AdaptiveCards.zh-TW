---
title: 調適型卡片的 .NET SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
ms.openlocfilehash: 009ac262b40152d120ca626ce0dadc6983bc187c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733035"
---
# <a name="net-sdk-for-authoring-cards"></a><span data-ttu-id="f2132-102">適用于撰寫卡片的 .NET SDK</span><span class="sxs-lookup"><span data-stu-id="f2132-102">.NET SDK for Authoring Cards</span></span>

<span data-ttu-id="f2132-103">如我們在[消費者入門](../../authoring-cards/getting-started.md)頁面中所述, 調適型卡片是 JSON 物件模型。</span><span class="sxs-lookup"><span data-stu-id="f2132-103">As we described in the [Getting Started](../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON object model.</span></span> <span data-ttu-id="f2132-104">.NET 程式庫可讓您更輕鬆地使用該 JSON。</span><span class="sxs-lookup"><span data-stu-id="f2132-104">The .NET library makes working with that JSON much easier.</span></span>


## <a name="nuget-install"></a><span data-ttu-id="f2132-105">NuGet 安裝</span><span class="sxs-lookup"><span data-stu-id="f2132-105">NuGet Install</span></span>
<span data-ttu-id="f2132-106">`AdaptiveCards` NuGet 套件提供在 .net 中使用調適型卡片的類型</span><span class="sxs-lookup"><span data-stu-id="f2132-106">The `AdaptiveCards` NuGet package provides types for working with adaptive cards in .NET</span></span>

<span data-ttu-id="f2132-107">[![Nuget 安裝](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span><span class="sxs-lookup"><span data-stu-id="f2132-107">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span></span>

```console
Install-Package AdaptiveCards
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a><span data-ttu-id="f2132-108">範例：建立 AdaptiveCard 並序列化為 JSON</span><span class="sxs-lookup"><span data-stu-id="f2132-108">Example: Create an AdaptiveCard and serialize to JSON</span></span>

<span data-ttu-id="f2132-109">這個範例示範如何使用標準C#物件建立調適型卡片, 然後將它序列化為 JSON 以透過網路傳輸。</span><span class="sxs-lookup"><span data-stu-id="f2132-109">This example demonstrates how to build an Adaptive Card using standard C# objects and then serialize it to JSON for transport over the wire.</span></span>

```csharp
using AdaptiveCards;
// ...

AdaptiveCard card = new AdaptiveCard();

card.Body.Add(new AdaptiveTextBlock() 
{
    Text = "Hello",
    Size = AdaptiveTextSize.ExtraLarge
});

card.Body.Add(new AdaptiveImage() 
{
    Url = new Uri("http://adaptivecards.io/content/cats/1.png")
});

// serialize the card to JSON
string json = card.ToJson();
```

## <a name="example-parse-an-adaptivecard-from-json"></a><span data-ttu-id="f2132-110">範例：從 JSON 剖析 AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="f2132-110">Example: Parse an AdaptiveCard from JSON</span></span>

<span data-ttu-id="f2132-111">這個範例示範如何將 JSON 承載剖析成調適型卡片。</span><span class="sxs-lookup"><span data-stu-id="f2132-111">This example demonstrates how to parse a JSON payload into an Adaptive Card.</span></span> <span data-ttu-id="f2132-112">這可讓您使用轉譯器[sdk](../../rendering-cards/getting-started.md), 輕鬆操作物件模型, 或甚至在您的應用程式中呈現調適型卡片。</span><span class="sxs-lookup"><span data-stu-id="f2132-112">This makes it easy to manipulate the object model or even render Adaptive Cards inside your app by using our [renderer SDKs](../../rendering-cards/getting-started.md).</span></span>

```csharp
try
{
    // Get a JSON-serialized payload
    // Your app will probably get cards from somewhere else :)
    var client = new HttpClient();
    var response = await client.GetAsync("http://adaptivecards.io/payloads/ActivityUpdate.json");
    var json = await response.Content.ReadAsStringAsync();

    // Parse the JSON 
    AdaptiveCardParseResult result = AdaptiveCard.FromJson(json);

    // Get card from result
    AdaptiveCard card = result.Card;

    // Optional: check for any parse warnings
    // This includes things like unknown element "type"
    // or unknown properties on element
    IList<AdaptiveWarning> warnings = result.Warnings;
}
catch(AdaptiveSerializationException ex)
{
    // Failed to deserialize card 
    // This occurs from malformed JSON
    // or schema violations like required properties missing 
}
```

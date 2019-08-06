---
title: .NET WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 999f8ac3cd6a18fbbfc8b8bbdcf47465d8bb314f
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732730"
---
# <a name="getting-started---net-wpf"></a><span data-ttu-id="dc6f5-102">快速入門-.NET WPF</span><span class="sxs-lookup"><span data-stu-id="dc6f5-102">Getting started - .NET WPF</span></span>

<span data-ttu-id="dc6f5-103">如我們在[消費者入門](../../../authoring-cards/getting-started.md)頁面中所述, 調適型卡片是 JSON 序列化的卡片物件模型。</span><span class="sxs-lookup"><span data-stu-id="dc6f5-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="dc6f5-104">此程式庫可讓您輕鬆地將該 JSON 轉譯成 WPF UI, 以便在您的應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="dc6f5-104">This library makes it easy to render that JSON into WPF UI that you can use within your app.</span></span>

## <a name="nuget-install"></a><span data-ttu-id="dc6f5-105">NuGet 安裝</span><span class="sxs-lookup"><span data-stu-id="dc6f5-105">NuGet install</span></span>

<span data-ttu-id="dc6f5-106">[![Nuget 安裝](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span><span class="sxs-lookup"><span data-stu-id="dc6f5-106">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a><span data-ttu-id="dc6f5-107">Xceed 增強型輸入套件</span><span class="sxs-lookup"><span data-stu-id="dc6f5-107">Xceed enhanced input package</span></span>

<span data-ttu-id="dc6f5-108">這個選擇性的封裝可加強調適型卡片輸入控制項, 但 WPF 提供的功能已超出預設。</span><span class="sxs-lookup"><span data-stu-id="dc6f5-108">This optional package enhances the Adaptive Card Input controls beyond what WPF provides out of the box.</span></span> <span data-ttu-id="dc6f5-109">依存于`Extended.Wpf.Toolkit`</span><span class="sxs-lookup"><span data-stu-id="dc6f5-109">It has a dependency on `Extended.Wpf.Toolkit`</span></span>

<span data-ttu-id="dc6f5-110">[![Nuget 安裝](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span><span class="sxs-lookup"><span data-stu-id="dc6f5-110">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="dc6f5-111">WPF 視覺化檢視範例</span><span class="sxs-lookup"><span data-stu-id="dc6f5-111">WPF Visualizer Sample</span></span>

![視覺化檢視螢幕擷取畫面](../../../resources/media/tools/wpfvisualizer.png)

<span data-ttu-id="dc6f5-113">[Wpf 視覺化檢視範例](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer)可讓您使用 wpf 將卡片視覺化。</span><span class="sxs-lookup"><span data-stu-id="dc6f5-113">The [WPF Visualizer sample](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF.</span></span>  <span data-ttu-id="dc6f5-114">內`Host Config`建編輯器來編輯和查看主機設定。</span><span class="sxs-lookup"><span data-stu-id="dc6f5-114">A `Host Config` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="dc6f5-115">將這些設定儲存為 JSON, 以在應用程式中轉譯時使用它們。</span><span class="sxs-lookup"><span data-stu-id="dc6f5-115">Save these settings as a JSON to use them in rendering in your application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dc6f5-116">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dc6f5-116">Next steps</span></span>

<span data-ttu-id="dc6f5-117">請參閱[呈現卡片](render-a-card.md)以進行後續步驟!</span><span class="sxs-lookup"><span data-stu-id="dc6f5-117">See [Render a card](render-a-card.md) for the next steps!</span></span>

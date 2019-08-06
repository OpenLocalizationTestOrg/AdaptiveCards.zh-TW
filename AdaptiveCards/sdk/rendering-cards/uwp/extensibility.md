---
title: 擴充性-UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: ffe22e1e9b8632cbceedb4bfc26b285b4a9b0075
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732705"
---
# <a name="extensibility---uwp"></a><span data-ttu-id="e626b-102">擴充性-UWP</span><span class="sxs-lookup"><span data-stu-id="e626b-102">Extensibility - UWP</span></span>

## <a name="changing-per-element-rendering"></a><span data-ttu-id="e626b-103">變更每個元素轉譯</span><span class="sxs-lookup"><span data-stu-id="e626b-103">Changing per element rendering</span></span>

<span data-ttu-id="e626b-104">執行轉譯器類別並在轉譯器中加以設定</span><span class="sxs-lookup"><span data-stu-id="e626b-104">Implement a renderer class and set it in the renderer</span></span>

```csharp
// My custom renderer is going to replace how textblocks should render!
public class MyCustomRenderer : IAdaptiveElementRenderer
{
    public UIElement Render(IAdaptiveCardElement element, AdaptiveRenderContext context)
    {
        var adaptiveTextBlock = element as AdaptiveTextBlock;
        TextBlock textblock = new TextBlock()
        {
            Text = adaptiveTextBlock.Text + "I want every single textblock to append this text, and it should be aligned to the right!",
            HorizontalAlignment = HorizontalAlignment.Right
        };

        return textblock;
    }
}

renderer.ElementRenderers.Set("TextBlock", new MyCustomRenderer());
```
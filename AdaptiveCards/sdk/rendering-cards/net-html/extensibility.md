---
title: 擴充性-.NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: d1df38608abde9ad26c78bbc5f66eb3bbb3d1971
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732825"
---
# <a name="extensibility---net-html"></a><span data-ttu-id="a99e0-102">擴充性-.NET HTML</span><span class="sxs-lookup"><span data-stu-id="a99e0-102">Extensibility - .NET HTML</span></span>

## <a name="custom-element-rendering"></a><span data-ttu-id="a99e0-103">自訂元素呈現</span><span class="sxs-lookup"><span data-stu-id="a99e0-103">Custom Element Rendering</span></span>

<span data-ttu-id="a99e0-104">如需轉譯器的完全控制, 您可以`ElementRenderers`使用屬性來**新增**、**移除**或覆**寫**預設轉譯器。</span><span class="sxs-lookup"><span data-stu-id="a99e0-104">For full control of the renderer you can use the `ElementRenderers` property to **add**, **remove**, or **override** default renderers.</span></span>

<span data-ttu-id="a99e0-105">下列範例顯示如何定義自訂`"type": "Rating"`專案並加以呈現。</span><span class="sxs-lookup"><span data-stu-id="a99e0-105">The following example shows how you could define a custom `"type": "Rating"` element and render it.</span></span>

```csharp
// Register the new type with the JSON parser
AdaptiveTypedElementConverter.RegisterTypedElement<MyCustomRating>();

// Add the new type to the element renderer registry
renderer.ElementRenderers.Set<MyCustomRating>(MyCustomRating.Render);

// Define a custom Rating element type
public class MyCustomRating : AdaptiveElement
{
    public override string Type => "Rating";

    public double Rating { get; set; }

    public AdaptiveTextSize Size { get; set; }

    public AdaptiveTextColor Color { get; set; }

    public static FrameworkElement Render(MyCustomRating rating, AdaptiveRenderContext context)
    {
        var textBlock = new AdaptiveTextBlock
        {
            Size = rating.Size,
            Color = rating.Color
        };
        for (int i = 0; i < rating.Rating; i++)
        {
            textBlock.Text += "\u2605";
        }
        textBlock.Text += $" ({rating.Rating})";
        return context.Render(textBlock);
    }
}
```

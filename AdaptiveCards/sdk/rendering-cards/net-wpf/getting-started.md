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
# <a name="getting-started---net-wpf"></a>快速入門-.NET WPF

如我們在[消費者入門](../../../authoring-cards/getting-started.md)頁面中所述, 調適型卡片是 JSON 序列化的卡片物件模型。 此程式庫可讓您輕鬆地將該 JSON 轉譯成 WPF UI, 以便在您的應用程式中使用。

## <a name="nuget-install"></a>NuGet 安裝

[![Nuget 安裝](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a>Xceed 增強型輸入套件

這個選擇性的封裝可加強調適型卡片輸入控制項, 但 WPF 提供的功能已超出預設。 依存于`Extended.Wpf.Toolkit`

[![Nuget 安裝](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a>WPF 視覺化檢視範例

![視覺化檢視螢幕擷取畫面](../../../resources/media/tools/wpfvisualizer.png)

[Wpf 視覺化檢視範例](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer)可讓您使用 wpf 將卡片視覺化。  內`Host Config`建編輯器來編輯和查看主機設定。 將這些設定儲存為 JSON, 以在應用程式中轉譯時使用它們。

## <a name="next-steps"></a>後續步驟

請參閱[呈現卡片](render-a-card.md)以進行後續步驟!

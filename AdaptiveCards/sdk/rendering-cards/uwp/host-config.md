---
title: 主機設定-UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 6f14830a643b064c6169cf3143bbc7cd4ce45937
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732485"
---
# <a name="host-config---uwp"></a><span data-ttu-id="3a152-102">主機設定-UWP</span><span class="sxs-lookup"><span data-stu-id="3a152-102">Host config - UWP</span></span>

<span data-ttu-id="3a152-103">若要自訂轉譯器, 請提供 HostConfig 物件的實例。</span><span class="sxs-lookup"><span data-stu-id="3a152-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="3a152-104">(如需完整描述, 請參閱[主機設定架構](../../../rendering-cards/host-config.md))。</span><span class="sxs-lookup"><span data-stu-id="3a152-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

> <span data-ttu-id="3a152-105">HostConfig 物件將會以預設值具現化, 因此您可以只設定您想要變更的屬性。</span><span class="sxs-lookup"><span data-stu-id="3a152-105">The HostConfig object will be instantiated with defaults, so you can set just the properties you want to change.</span></span>

<span data-ttu-id="3a152-106">範例：</span><span class="sxs-lookup"><span data-stu-id="3a152-106">Example:</span></span>

```csharp
var hostConfig = new AdaptiveHostConfig() 
{
    FontSizes = {
        Small = 15,
        Normal = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};
renderer.HostConfig = hostConfig;
```

> <span data-ttu-id="3a152-107">或者, 您也可以從 JSON 字串載入 HostConfig。</span><span class="sxs-lookup"><span data-stu-id="3a152-107">Alternatively, you can load the HostConfig from a JSON string.</span></span>

<span data-ttu-id="3a152-108">範例：</span><span class="sxs-lookup"><span data-stu-id="3a152-108">Example:</span></span>

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

<span data-ttu-id="3a152-109">當您將它傳遞給 UWPRenderer 時, 您會將預設 HostConfig 設定為用於轉譯的每張卡片。</span><span class="sxs-lookup"><span data-stu-id="3a152-109">When you pass it in to the UWPRenderer you are setting the default HostConfig to use for every card you render.</span></span>
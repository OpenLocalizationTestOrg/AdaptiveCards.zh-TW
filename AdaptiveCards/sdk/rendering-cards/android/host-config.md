---
title: 主機設定-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 2828a379d8fda151b1cfca51e5898135186333ae
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733010"
---
# <a name="host-config---android"></a><span data-ttu-id="59ec8-102">主機設定-Android</span><span class="sxs-lookup"><span data-stu-id="59ec8-102">Host config - Android</span></span>

<span data-ttu-id="59ec8-103">若要自訂轉譯器, 請提供 HostConfig 物件的實例。</span><span class="sxs-lookup"><span data-stu-id="59ec8-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="59ec8-104">(如需完整描述, 請參閱[主機設定架構](../../../rendering-cards/host-config.md))。</span><span class="sxs-lookup"><span data-stu-id="59ec8-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

<span data-ttu-id="59ec8-105">若要從字串建立 HostConfig 物件, 請使用 DeserializeFromString 方法</span><span class="sxs-lookup"><span data-stu-id="59ec8-105">To Create a HostConfig object from a string, use the DeserializeFromString method</span></span>

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```
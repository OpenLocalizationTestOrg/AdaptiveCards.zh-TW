---
title: 主機設定-iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34d28ef0f0cd7200965fb6967bb2f252f6a47456
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732930"
---
# <a name="host-config---ios"></a><span data-ttu-id="06880-102">主機設定-iOS</span><span class="sxs-lookup"><span data-stu-id="06880-102">Host config - iOS</span></span>

<span data-ttu-id="06880-103">主機可以透過可由 JSON 字串產生的 HostConfig 來設定</span><span class="sxs-lookup"><span data-stu-id="06880-103">Host can be configured through HostConfig which can be generated by JSON string</span></span>

```objective-c
ACOParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
```

<span data-ttu-id="06880-104">預設 HostConfig 可以具現化</span><span class="sxs-lookup"><span data-stu-id="06880-104">Default HostConfig can be instantiated</span></span>

```objective-c
ACOHostConfig *defaultConfig = [[ACHostConfig alloc] init];
```

## <a name="render-a-card-using-host-config"></a><span data-ttu-id="06880-105">使用主機配置來轉譯卡片</span><span class="sxs-lookup"><span data-stu-id="06880-105">Render a card using host config</span></span>

<span data-ttu-id="06880-106">Rederer 會使用調適型卡片和主機設定。HostConfig 可以是 nil, 如果是 nil, 則會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="06880-106">Rederer takes adaptive card and host config. HostConfig can be nil, and if nil, default value will be used.</span></span>

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:hostconfigParseResult.config
                   widthConstraint:300.0];
```
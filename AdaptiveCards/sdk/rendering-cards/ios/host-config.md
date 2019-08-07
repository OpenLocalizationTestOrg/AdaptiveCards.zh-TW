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
# <a name="host-config---ios"></a>主機設定-iOS

主機可以透過可由 JSON 字串產生的 HostConfig 來設定

```objective-c
ACOParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
```

預設 HostConfig 可以具現化

```objective-c
ACOHostConfig *defaultConfig = [[ACHostConfig alloc] init];
```

## <a name="render-a-card-using-host-config"></a>使用主機配置來轉譯卡片

Rederer 會使用調適型卡片和主機設定。HostConfig 可以是 nil, 如果是 nil, 則會使用預設值。

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:hostconfigParseResult.config
                   widthConstraint:300.0];
```
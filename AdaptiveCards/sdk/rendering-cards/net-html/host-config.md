---
title: 主機設定-.NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: a51b64f5f9783a187d7c3eb56c563a1d4497d3e2
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732820"
---
# <a name="host-config---net-html"></a>主機設定-.NET HTML

[主機](../../../rendering-cards/host-config.md)設定是所有轉譯器都瞭解的共用設定物件。 這可讓您定義每個平臺轉譯器會自動解讀的通用樣式 (例如, 字型系列、字型大小、預設間距) 和行為 (例如動作數目上限)。 

目標是每個平臺轉譯器所產生的原生 UI 看起來非常類似于您的最小工作。

```csharp
// Construct programmatically
renderer.HostConfig = new AdaptiveHostConfig() 
{
    FontFamily = "Comic Sans",
    FontSizes = {
        Small = 15,
        Default = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};

// Or parse from JSON
renderer.HostConfig  = AdaptiveHostConfig.FromJson(@"{
    ""fontFamily"": ""Comic Sans"",
    ""fontSizes"": {
        ""small"": 25,
        ""default"": 26,
        ""medium"": 27,
        ""large"": 28,
        ""extraLarge"": 29
    }
}");
```
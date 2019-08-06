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
# <a name="host-config---android"></a>主機設定-Android

若要自訂轉譯器, 請提供 HostConfig 物件的實例。 (如需完整描述, 請參閱[主機設定架構](../../../rendering-cards/host-config.md))。

若要從字串建立 HostConfig 物件, 請使用 DeserializeFromString 方法

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```
---
title: 原生樣式-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: c3190fbb31480f92c774d233476436ee2cfc52b3
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733020"
---
# <a name="native-styling---android"></a>原生樣式-Android

Android 轉譯器不支援原生樣式, 而 v1.0 引進了設定某些屬性樣式的支援:

## <a name="action-sentiment"></a>動作情感

動作情感包含在 v1.0 中, 而且不支援與其他版本一樣多的樣式, 可以藉由執行有效的樣式, 並將下列程式程式碼加入至, 來為具有*破壞性*或*正面*情感的動作加上樣式專案的樣式 .xml

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a>內嵌動作

具有內嵌動作的文字輸入, 可以為所轉譯的動作設定樣式。 這可將動作的樣式設定為按鈕 (adaptiveInlineAction), 或做為影像 (adaptiveInlineActionImage)

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> 所有專案名稱都必須如這裡所示加以保留, 因為轉譯器會尋找這些確切名稱

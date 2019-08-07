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
# <a name="native-styling---android"></a><span data-ttu-id="783ea-102">原生樣式-Android</span><span class="sxs-lookup"><span data-stu-id="783ea-102">Native styling - Android</span></span>

<span data-ttu-id="783ea-103">Android 轉譯器不支援原生樣式, 而 v1.0 引進了設定某些屬性樣式的支援:</span><span class="sxs-lookup"><span data-stu-id="783ea-103">Native styling is not supported on the android renderer, v1.2 introduces the support for styling some properties:</span></span>

## <a name="action-sentiment"></a><span data-ttu-id="783ea-104">動作情感</span><span class="sxs-lookup"><span data-stu-id="783ea-104">Action Sentiment</span></span>

<span data-ttu-id="783ea-105">動作情感包含在 v1.0 中, 而且不支援與其他版本一樣多的樣式, 可以藉由執行有效的樣式, 並將下列程式程式碼加入至, 來為具有*破壞性*或*正面*情感的動作加上樣式專案的樣式 .xml</span><span class="sxs-lookup"><span data-stu-id="783ea-105">Action sentiment is included in **v1.2** and while not supporting as many styles as other versions, actions with *destructive* or *positive* sentiment can be styled by implementing a valid style and adding the following line into the styles.xml for your project</span></span>

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a><span data-ttu-id="783ea-106">內嵌動作</span><span class="sxs-lookup"><span data-stu-id="783ea-106">Inline Action</span></span>

<span data-ttu-id="783ea-107">具有內嵌動作的文字輸入, 可以為所轉譯的動作設定樣式。</span><span class="sxs-lookup"><span data-stu-id="783ea-107">Text inputs with an inline action allows styling for the action being rendered.</span></span> <span data-ttu-id="783ea-108">這可將動作的樣式設定為按鈕 (adaptiveInlineAction), 或做為影像 (adaptiveInlineActionImage)</span><span class="sxs-lookup"><span data-stu-id="783ea-108">This allows styling the action as a button (adaptiveInlineAction) or as an image (adaptiveInlineActionImage)</span></span>

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> <span data-ttu-id="783ea-109">所有專案名稱都必須如這裡所示加以保留, 因為轉譯器會尋找這些確切名稱</span><span class="sxs-lookup"><span data-stu-id="783ea-109">All item names must be kept as shown here as the renderer looks for those exact names</span></span>

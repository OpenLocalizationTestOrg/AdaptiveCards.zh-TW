---
title: 呈現卡片-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 5ced7a2217ef6ef475aa344d92ad2f5e567266f8
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733000"
---
# <a name="render-a-card---android"></a><span data-ttu-id="ebeb2-102">呈現卡片-Android</span><span class="sxs-lookup"><span data-stu-id="ebeb2-102">Render a card - Android</span></span>

<span data-ttu-id="ebeb2-103">以下說明如何使用 Android SDK 來轉譯卡片。</span><span class="sxs-lookup"><span data-stu-id="ebeb2-103">Here's how to render a card using the Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="ebeb2-104">從 JSON 文字建立調適型卡片物件實例</span><span class="sxs-lookup"><span data-stu-id="ebeb2-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> <span data-ttu-id="ebeb2-105">**1.2 版的重大變更**</span><span class="sxs-lookup"><span data-stu-id="ebeb2-105">**Breaking changes for v1.2**</span></span>
> 

1. <span data-ttu-id="ebeb2-106">ElementParserRegistration 參數已變更為 ParseCoNtext, 其中包括 ElementParserRegistration 和 ActionParserRegistration 物件</span><span class="sxs-lookup"><span data-stu-id="ebeb2-106">ElementParserRegistration parameter changed to ParseContext which includes an ElementParserRegistration and an ActionParserRegistration object</span></span>

```java
ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="ebeb2-107">或</span><span class="sxs-lookup"><span data-stu-id="ebeb2-107">or</span></span>

```java
ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

## <a name="render-a-card"></a><span data-ttu-id="ebeb2-108">呈現卡片</span><span class="sxs-lookup"><span data-stu-id="ebeb2-108">Render a card</span></span>

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.getView();
```

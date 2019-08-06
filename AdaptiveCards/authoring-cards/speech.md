---
title: 語音和自訂
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 468d090dff0511f40cb7e5eedc4f4a18fa12aa3c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732665"
---
# <a name="speech-and-advanced-customization"></a><span data-ttu-id="dd5d3-102">語音和自訂</span><span class="sxs-lookup"><span data-stu-id="dd5d3-102">Speech and advanced customization</span></span>
<span data-ttu-id="dd5d3-103">我們居住在透過 Cortana 等服務的語音互動時代。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-103">We live in an era of speech interaction via services like Cortana.</span></span>  <span data-ttu-id="dd5d3-104">調適型卡片是從第一天到支援語音的設計, 可實現酷炫的新手滿案例。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-104">Adaptive cards are designed from day one to support speech, enabling cool new hands-full scenarios.</span></span>

<span data-ttu-id="dd5d3-105">此`speak`標籤可將調適型卡片傳遞至視覺顯示不是主要體驗的環境, 例如駕駛時的汽車儀表板。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-105">The `speak` tag enables the adaptive card to be delivered to an environment where a visual display is not primary experience, such as to a car dashboard while driving.</span></span> 

## <a name="speak-property"></a><span data-ttu-id="dd5d3-106">說話屬性</span><span class="sxs-lookup"><span data-stu-id="dd5d3-106">Speak property</span></span>
<span data-ttu-id="dd5d3-107">為支援語音, 我們有`speak`一個屬性, 其中包含要向使用者顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-107">To support speech we have a `speak` property which contains text to say to the user.</span></span> <span data-ttu-id="dd5d3-108">文字可以使用語音合成標記語言 ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)) 來標注。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-108">The text can be annotated using speech synthesis markup language ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)).</span></span> <span data-ttu-id="dd5d3-109">SSML 控制語音的速度、音調和變化。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-109">SSML controls the speed, tone, and inflection of the speech.</span></span>  <span data-ttu-id="dd5d3-110">它甚至可讓您從自己的服務串流音訊或轉譯 TTS 音訊串流, 讓您有絕佳的自訂彈性。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-110">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of flexibility for customization.</span></span>

<span data-ttu-id="dd5d3-111">有兩種模式可供主應用程式用來說屬性使用方式:</span><span class="sxs-lookup"><span data-stu-id="dd5d3-111">There are two patterns for speak property usage by a host application:</span></span>

* <span data-ttu-id="dd5d3-112">**傳遞**時-當卡片交付時, 用戶端可能會選擇讀取卡片的 [說話] 屬性, 以描述整個卡片。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-112">**On delivery** - When a card is delivered, the client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="dd5d3-113">依**需求**-為了支援更豐富的協助工具模型, 架構支援每個元素的「說出」標記。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-113">**On demand** - In order to support a richer accessibility model, the schema supports a speak tag for each element.</span></span> <span data-ttu-id="dd5d3-114">用戶端可能會針對卡片中的每個元素讀取說話屬性。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-114">The client may read a Speak property  for each element in the card.</span></span>

### <a name="examples"></a><span data-ttu-id="dd5d3-115">範例</span><span class="sxs-lookup"><span data-stu-id="dd5d3-115">Examples</span></span>

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a><span data-ttu-id="dd5d3-116">語音內容設計</span><span class="sxs-lookup"><span data-stu-id="dd5d3-116">Speech content design</span></span>

<span data-ttu-id="dd5d3-117">針對語音設計的內容不同于針對視覺效果顯示而設計的內容。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-117">Content designed for speech is different from content designed for visual display.</span></span> <span data-ttu-id="dd5d3-118">當您設計卡片時, 您會設計整個視覺體驗, 以樂趣使用者的方式呈現資訊給使用者。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-118">When you design a card, you are designing an entire visual experience to present information to a user in a way that delights them.</span></span> <span data-ttu-id="dd5d3-119">設計語音時, 您應該考慮如何 verbally 以樂趣使用者的方式描述內容。</span><span class="sxs-lookup"><span data-stu-id="dd5d3-119">When designing for speech, you should think about how to verbally describe the content in a way that delights the user.</span></span>  

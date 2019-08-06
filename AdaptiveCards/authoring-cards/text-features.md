---
title: 文字功能
author: matthidinger
ms.author: mahiding
ms.date: 11/09/2017
ms.topic: article
ms.openlocfilehash: f7ea40b80df4d976c0a8a86b15254018fdf2fac6
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732670"
---
# <a name="text-features"></a><span data-ttu-id="74051-102">文字功能</span><span class="sxs-lookup"><span data-stu-id="74051-102">Text features</span></span>

<span data-ttu-id="74051-103">`TextBlock`提供一些用來格式化和當地語系化文字的先進功能。</span><span class="sxs-lookup"><span data-stu-id="74051-103">`TextBlock` offers some advanced features for formatting and localizing the text.</span></span>

## <a name="markdown"></a><span data-ttu-id="74051-104">Markdown</span><span class="sxs-lookup"><span data-stu-id="74051-104">Markdown</span></span>
<span data-ttu-id="74051-105">為了支援內嵌標記, 調適型卡片支援 Markdown 語法的**子集**。</span><span class="sxs-lookup"><span data-stu-id="74051-105">To support inline markup, Adaptive Cards support a **subset** of Markdown syntax.</span></span>

<span data-ttu-id="74051-106">_支援_</span><span class="sxs-lookup"><span data-stu-id="74051-106">_Supported_</span></span>

| <span data-ttu-id="74051-107">文字樣式</span><span class="sxs-lookup"><span data-stu-id="74051-107">Text Style</span></span>      | <span data-ttu-id="74051-108">Markdown</span><span class="sxs-lookup"><span data-stu-id="74051-108">Markdown</span></span> |
|-----------------|-----|
| <span data-ttu-id="74051-109">**粗體**</span><span class="sxs-lookup"><span data-stu-id="74051-109">**Bold**</span></span>        | ```**Bold**``` |
| <span data-ttu-id="74051-110">_斜體_</span><span class="sxs-lookup"><span data-stu-id="74051-110">_Italic_</span></span>        | ```_Italic_``` |
| <span data-ttu-id="74051-111">專案符號清單</span><span class="sxs-lookup"><span data-stu-id="74051-111">Bullet list</span></span>     | ```- Item 1\r- Item 2\r- Item 3``` | 
| <span data-ttu-id="74051-112">編號清單</span><span class="sxs-lookup"><span data-stu-id="74051-112">Numbered list</span></span>   | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="74051-113">指向</span><span class="sxs-lookup"><span data-stu-id="74051-113">Hyperlinks</span></span>      | ```[Title](url)``` |

<span data-ttu-id="74051-114">_不支援_</span><span class="sxs-lookup"><span data-stu-id="74051-114">_Not supported_</span></span>

* <span data-ttu-id="74051-115">頁首</span><span class="sxs-lookup"><span data-stu-id="74051-115">Headers</span></span>
* <span data-ttu-id="74051-116">資料表</span><span class="sxs-lookup"><span data-stu-id="74051-116">Tables</span></span>
* <span data-ttu-id="74051-117">影像</span><span class="sxs-lookup"><span data-stu-id="74051-117">Images</span></span>
* <span data-ttu-id="74051-118">上表中沒有任何專案</span><span class="sxs-lookup"><span data-stu-id="74051-118">Anything not in the table above</span></span>

### <a name="markdown-example"></a><span data-ttu-id="74051-119">Markdown 範例</span><span class="sxs-lookup"><span data-stu-id="74051-119">Markdown Example</span></span>

<span data-ttu-id="74051-120">下列承載會轉譯如下的內容:</span><span class="sxs-lookup"><span data-stu-id="74051-120">The below payload would render something like this:</span></span>

![markdown 螢幕擷取畫面](media/text-features/markdown.png)

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a><span data-ttu-id="74051-122">日期/時間格式和當地語系化</span><span class="sxs-lookup"><span data-stu-id="74051-122">Date/Time formatting and localization</span></span>

<span data-ttu-id="74051-123">有時您不會知道接收卡片的使用者所在的時區, 因此調適型`DATE()`卡片`TIME()`會提供和格式化功能, 以自動將目標裝置上的時間當地語系化。</span><span class="sxs-lookup"><span data-stu-id="74051-123">Sometimes you won't know the timezone of the user receiving the card, so Adaptive Cards offers `DATE()` and `TIME()` formatting functions to automatically localize the time on the target device.</span></span>

### <a name="datetime-example"></a><span data-ttu-id="74051-124">日期/時間範例</span><span class="sxs-lookup"><span data-stu-id="74051-124">Date/Time Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Your package will arrive on {{DATE(2017-02-14T06:00:00Z, SHORT)}} at {{TIME(2017-02-14T06:00:00Z)}}",
            "wrap": true
        }
    ]
}
```

<span data-ttu-id="74051-125">上述卡片將會顯示:</span><span class="sxs-lookup"><span data-stu-id="74051-125">The above card will display:</span></span> 

> <span data-ttu-id="74051-126">**您的套件將會在上午6:00 的星期二抵達2017年2月14日**</span><span class="sxs-lookup"><span data-stu-id="74051-126">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM**</span></span>

### <a name="datetime-function-rules"></a><span data-ttu-id="74051-127">日期/時間函數規則</span><span class="sxs-lookup"><span data-stu-id="74051-127">Date/Time function rules</span></span>

<span data-ttu-id="74051-128">有一些規則可適當解讀每個平臺上的日期/時間函數。</span><span class="sxs-lookup"><span data-stu-id="74051-128">There are some rules to properly interpret the the date/time functions on every platform.</span></span> <span data-ttu-id="74051-129">如果不符合規則, 則會向使用者顯示原始字串, 而且不會有任何人想要的。</span><span class="sxs-lookup"><span data-stu-id="74051-129">If the rules aren't met then the raw string will be displayed to the user, and no one wants that.</span></span>

1. <span data-ttu-id="74051-130">區分**大小寫**(必須全部為大寫)</span><span class="sxs-lookup"><span data-stu-id="74051-130">**CASE SENSITIVE** (must be all caps)</span></span>
1. <span data-ttu-id="74051-131">`{{` 、`}}`或括弧之間沒有空格</span><span class="sxs-lookup"><span data-stu-id="74051-131">**NO SPACES** between the `{{`, `}}`, or parentheses</span></span>
1. <span data-ttu-id="74051-132">**嚴格的[RFC 3389](https://tools.ietf.org/html/rfc3339)格式**(請參閱下列範例)</span><span class="sxs-lookup"><span data-stu-id="74051-132">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) FORMATTING** (See examples below)</span></span>
1. <span data-ttu-id="74051-133">**必須是**有效的日期和時間</span><span class="sxs-lookup"><span data-stu-id="74051-133">**MUST BE** a valid date and time</span></span>

### <a name="valid-formats"></a><span data-ttu-id="74051-134">有效的格式</span><span class="sxs-lookup"><span data-stu-id="74051-134">Valid formats</span></span>

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a><span data-ttu-id="74051-135">日期格式化參數</span><span class="sxs-lookup"><span data-stu-id="74051-135">Date formatting param</span></span>

<span data-ttu-id="74051-136">針對日期, 可以指定選擇性的參數來格式化輸出。</span><span class="sxs-lookup"><span data-stu-id="74051-136">For dates, an optional param may be specified to format the output.</span></span>


|       <span data-ttu-id="74051-137">格式</span><span class="sxs-lookup"><span data-stu-id="74051-137">Format</span></span>        |            <span data-ttu-id="74051-138">範例</span><span class="sxs-lookup"><span data-stu-id="74051-138">Example</span></span>            |
|---------------------|-------------------------------|
| <span data-ttu-id="74051-139">`COMPACT`預設</span><span class="sxs-lookup"><span data-stu-id="74051-139">`COMPACT` (Default)</span></span> |          <span data-ttu-id="74051-140">"2/13/2017"</span><span class="sxs-lookup"><span data-stu-id="74051-140">"2/13/2017"</span></span>          |
|       `SHORT`       |     <span data-ttu-id="74051-141">「2017年2月13日星期一」</span><span class="sxs-lookup"><span data-stu-id="74051-141">"Mon, Feb 13th, 2017"</span></span>     |
|       `LONG`        | <span data-ttu-id="74051-142">「2017年2月13日星期一」</span><span class="sxs-lookup"><span data-stu-id="74051-142">"Monday, February 13th, 2017"</span></span> |


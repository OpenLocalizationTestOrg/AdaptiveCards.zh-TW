---
title: 適用于 Bot 開發人員的調適型卡片
author: matthidinger
ms.author: mahiding
ms.date: 05/30/2018
ms.topic: article
ms.openlocfilehash: a50f2e6f145ae2c4571d6b20b61b9ad182ca7ba5
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733165"
---
# <a name="adaptive-cards-for-bot-developers"></a><span data-ttu-id="19a4a-102">適用于 Bot 開發人員的調適型卡片</span><span class="sxs-lookup"><span data-stu-id="19a4a-102">Adaptive Cards for Bot Developers</span></span>

<span data-ttu-id="19a4a-103">調適型卡片非常適合 Bot。</span><span class="sxs-lookup"><span data-stu-id="19a4a-103">Adaptive Cards are a great fit for Bots.</span></span> <span data-ttu-id="19a4a-104">它們可讓您撰寫一次卡片, 並讓它在多個應用程式 (例如 Microsoft 小組、您自己的網站等等) 中轉譯精美。</span><span class="sxs-lookup"><span data-stu-id="19a4a-104">They let you author a card once and have it render beautifully inside multiple apps, like  Microsoft Teams, your own website, and more.</span></span>

> [!NOTE]
> <span data-ttu-id="19a4a-105">目前的預覽中不支援 Skype。</span><span class="sxs-lookup"><span data-stu-id="19a4a-105">Skype is not supported in the current preview.</span></span> <span data-ttu-id="19a4a-106">請參閱[合作夥伴狀態](../resources/partners.md)頁面以取得最新消息。</span><span class="sxs-lookup"><span data-stu-id="19a4a-106">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>

## <a name="try-it-out"></a><span data-ttu-id="19a4a-107">立即試用</span><span class="sxs-lookup"><span data-stu-id="19a4a-107">Try it out</span></span>

<span data-ttu-id="19a4a-108">按一下下列連結, 並[與我們的潛水 Bot 交談](http://contososcubademo.azurewebsites.net/)。</span><span class="sxs-lookup"><span data-stu-id="19a4a-108">Click the following link and [talk to our Scuba Bot](http://contososcubademo.azurewebsites.net/).</span></span> <span data-ttu-id="19a4a-109">比方`I'm looking for scuba`說, 它可協助您預訂夢想的潛水旅程。</span><span class="sxs-lookup"><span data-stu-id="19a4a-109">Say `I'm looking for scuba` and it'll help you book the scuba trip of your dreams.</span></span>  

<span data-ttu-id="19a4a-110">所有 bot 的回應都是透過調適型卡片來建立。</span><span class="sxs-lookup"><span data-stu-id="19a4a-110">All of the bot's responses are created with Adaptive Cards.</span></span>

<span data-ttu-id="19a4a-111">[![潛水聊天螢幕擷取畫面](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span><span class="sxs-lookup"><span data-stu-id="19a4a-111">[![Scuba chat screenshot](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span></span>

<span data-ttu-id="19a4a-112">**取得程式碼**: 您可以[在 GitHub 上找到完整](https://github.com/matthidinger/ContosoScubaBot
)的 Contoso 潛水 Bot 原始碼。</span><span class="sxs-lookup"><span data-stu-id="19a4a-112">**Get the code**: the full [Contoso Scuba Bot source code](https://github.com/matthidinger/ContosoScubaBot
) can be found on GitHub.</span></span>


## <a name="bot-framework-integration"></a><span data-ttu-id="19a4a-113">Bot Framework 整合</span><span class="sxs-lookup"><span data-stu-id="19a4a-113">Bot Framework Integration</span></span>

<span data-ttu-id="19a4a-114">使用[Bot Framework](https://dev.botframework.com/)時, 您可以撰寫單一 Bot, 以便在多個「頻道」 (例如 Skype、Microsoft 小組、Facebook Messenger 等) 之間與使用者進行交談。</span><span class="sxs-lookup"><span data-stu-id="19a4a-114">With the [Bot Framework](https://dev.botframework.com/) you can write a single bot that is able to chat with users across multiple "channels", like Skype, Microsoft Teams, Facebook Messenger, etc.</span></span>

## <a name="walkthrough"></a><span data-ttu-id="19a4a-115">逐步解說</span><span class="sxs-lookup"><span data-stu-id="19a4a-115">Walkthrough</span></span>

<span data-ttu-id="19a4a-116">將調適型卡片新增至您的 bot 非常簡單。</span><span class="sxs-lookup"><span data-stu-id="19a4a-116">It's pretty straight forward to add an Adaptive Card to your bot.</span></span>

### <a name="step-0-start-with-a-basic-message"></a><span data-ttu-id="19a4a-117">步驟 0：開始使用基本訊息</span><span class="sxs-lookup"><span data-stu-id="19a4a-117">Step 0: Start with a basic message</span></span>

<span data-ttu-id="19a4a-118">以下是標準的 Bot Framework `message`裝載, 可以傳遞至任何通道並向使用者顯示文字。</span><span class="sxs-lookup"><span data-stu-id="19a4a-118">Here's a standard Bot Framework `message` payload that can be delivered to any channel and display text to the user.</span></span>

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a><span data-ttu-id="19a4a-119">步驟 1：新增調適型卡片`attachment`</span><span class="sxs-lookup"><span data-stu-id="19a4a-119">Step 1: Add an Adaptive Card `attachment`</span></span>

<span data-ttu-id="19a4a-120">若要新增只包含文字的一些豐富內容, Bot Framework 具有的`attachments`概念。</span><span class="sxs-lookup"><span data-stu-id="19a4a-120">To add some richness beyond just text, the Bot Framework has a concept of `attachments`.</span></span> 

<span data-ttu-id="19a4a-121">讓我們附加可顯示自訂文字的調適型卡片。</span><span class="sxs-lookup"><span data-stu-id="19a4a-121">Let's attach an Adaptive Card that displays custom text.</span></span>

![基本調適型卡片](media/bots/hello-adaptivecards.png)

```json
{
  "type": "message",
  "text": "Plain text is ok, but sometimes I long for more...",
  "attachments": [
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "TextBlock",
            "text": "Hello World!",
            "size": "large"
          },
          {
            "type": "TextBlock",
            "text": "*Sincerely yours,*"
          },
          {
            "type": "TextBlock",
            "text": "Adaptive Cards",
            "separation": "none"
          }
        ],
        "actions": [
          {
            "type": "Action.OpenUrl",
            "url": "http://adaptivecards.io",
            "title": "Learn More"
          }
        ]
      }
    }
  ]
}
```

### <a name="step-2-build-even-richer-cards"></a><span data-ttu-id="19a4a-123">步驟 2：建立更豐富的卡片</span><span class="sxs-lookup"><span data-stu-id="19a4a-123">Step 2: Build even richer cards</span></span> 

<span data-ttu-id="19a4a-124">調適型卡片所提供的不僅僅是可自訂的文字。</span><span class="sxs-lookup"><span data-stu-id="19a4a-124">Adaptive Cards offer much more than just customizable text.</span></span> 

<span data-ttu-id="19a4a-125">您可以：</span><span class="sxs-lookup"><span data-stu-id="19a4a-125">You can:</span></span> 

* <span data-ttu-id="19a4a-126">新增`Images`至您的卡片</span><span class="sxs-lookup"><span data-stu-id="19a4a-126">Add `Images` to your card</span></span>
* <span data-ttu-id="19a4a-127">使用和組織您`Containers`的內容`Columns`</span><span class="sxs-lookup"><span data-stu-id="19a4a-127">Organize your content with `Containers` and `Columns`</span></span>
* <span data-ttu-id="19a4a-128">新增多個類型的`Actions`</span><span class="sxs-lookup"><span data-stu-id="19a4a-128">Add multiple types of `Actions`</span></span>
* <span data-ttu-id="19a4a-129">從`Input`您的使用者收集</span><span class="sxs-lookup"><span data-stu-id="19a4a-129">Collect `Input` from your users</span></span>
* <span data-ttu-id="19a4a-130">有一個卡片`show another card`</span><span class="sxs-lookup"><span data-stu-id="19a4a-130">Have one card `show another card`</span></span>
* <span data-ttu-id="19a4a-131">[查看完整的架構瀏覽器](http://adaptivecards.io/explorer/)!</span><span class="sxs-lookup"><span data-stu-id="19a4a-131">[Check out the full schema explorer](http://adaptivecards.io/explorer/)!</span></span> 

## <a name="platform-sdks"></a><span data-ttu-id="19a4a-132">平臺 Sdk</span><span class="sxs-lookup"><span data-stu-id="19a4a-132">Platform SDKs</span></span>

<span data-ttu-id="19a4a-133">如果您的 bot 是使用 .NET 或 NodeJS 開發的, 我們的程式庫可讓您更輕鬆地建立調適型卡片。</span><span class="sxs-lookup"><span data-stu-id="19a4a-133">If your bot is developed using .NET or NodeJS we have libraries to make building Adaptive Cards even easier.</span></span>

<span data-ttu-id="19a4a-134">平台</span><span class="sxs-lookup"><span data-stu-id="19a4a-134">Platform</span></span>|<span data-ttu-id="19a4a-135">安裝</span><span class="sxs-lookup"><span data-stu-id="19a4a-135">Install</span></span>|<span data-ttu-id="19a4a-136">進一步了解</span><span class="sxs-lookup"><span data-stu-id="19a4a-136">Learn more</span></span>
--------|-------|----------
<span data-ttu-id="19a4a-137">.NET</span><span class="sxs-lookup"><span data-stu-id="19a4a-137">.NET</span></span> | `Install-Package AdaptiveCards -IncludePrerelease` | [<span data-ttu-id="19a4a-138">Bot Framework .NET 檔</span><span class="sxs-lookup"><span data-stu-id="19a4a-138">Bot Framework .NET Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
<span data-ttu-id="19a4a-139">NodeJS</span><span class="sxs-lookup"><span data-stu-id="19a4a-139">NodeJS</span></span> | `npm install adaptivecards` | [<span data-ttu-id="19a4a-140">Bot Framework NodeJS 檔</span><span class="sxs-lookup"><span data-stu-id="19a4a-140">Bot Framework NodeJS Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a><span data-ttu-id="19a4a-141">頻道狀態</span><span class="sxs-lookup"><span data-stu-id="19a4a-141">Channel status</span></span>

<span data-ttu-id="19a4a-142">Bot Framework 可讓您將 bot 發佈至多個通道。</span><span class="sxs-lookup"><span data-stu-id="19a4a-142">The Bot Framework lets you publish your bot to multiple channels.</span></span> <span data-ttu-id="19a4a-143">我們正使用各種通道來提供調適型卡片的完整支援。</span><span class="sxs-lookup"><span data-stu-id="19a4a-143">We're working with various channels to provide full support for Adaptive Cards.</span></span> <span data-ttu-id="19a4a-144">請參閱[合作夥伴狀態](../resources/partners.md)頁面以取得最新消息。</span><span class="sxs-lookup"><span data-stu-id="19a4a-144">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>


## <a name="dive-in"></a><span data-ttu-id="19a4a-145">深入瞭解!</span><span class="sxs-lookup"><span data-stu-id="19a4a-145">Dive in!</span></span>

<span data-ttu-id="19a4a-146">我們已在本教學課程中特別說明此介面, 因此請參閱下列連結, 以探索調適型卡片可增強 bot 的更多方式。</span><span class="sxs-lookup"><span data-stu-id="19a4a-146">We've just scratched the surface in this tutorial, so please take a look at the links below to explore more ways that Adaptive Cards can enhance your bot.</span></span>

* <span data-ttu-id="19a4a-147">[流覽範例卡片](http://adaptivecards.io/samples/)以取得靈感</span><span class="sxs-lookup"><span data-stu-id="19a4a-147">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="19a4a-148">使用 [[架構瀏覽器](http://adaptivecards.io/explorer)] 學習可用的元素</span><span class="sxs-lookup"><span data-stu-id="19a4a-148">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="19a4a-149">使用[互動式視覺化檢視](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)建立卡片</span><span class="sxs-lookup"><span data-stu-id="19a4a-149">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="19a4a-150">隨時[掌握](http://adaptivecards.io/connect)您的意見反應</span><span class="sxs-lookup"><span data-stu-id="19a4a-150">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>

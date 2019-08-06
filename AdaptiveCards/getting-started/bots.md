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
# <a name="adaptive-cards-for-bot-developers"></a>適用于 Bot 開發人員的調適型卡片

調適型卡片非常適合 Bot。 它們可讓您撰寫一次卡片, 並讓它在多個應用程式 (例如 Microsoft 小組、您自己的網站等等) 中轉譯精美。

> [!NOTE]
> 目前的預覽中不支援 Skype。 請參閱[合作夥伴狀態](../resources/partners.md)頁面以取得最新消息。

## <a name="try-it-out"></a>立即試用

按一下下列連結, 並[與我們的潛水 Bot 交談](http://contososcubademo.azurewebsites.net/)。 比方`I'm looking for scuba`說, 它可協助您預訂夢想的潛水旅程。  

所有 bot 的回應都是透過調適型卡片來建立。

[![潛水聊天螢幕擷取畫面](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)

**取得程式碼**: 您可以[在 GitHub 上找到完整](https://github.com/matthidinger/ContosoScubaBot
)的 Contoso 潛水 Bot 原始碼。


## <a name="bot-framework-integration"></a>Bot Framework 整合

使用[Bot Framework](https://dev.botframework.com/)時, 您可以撰寫單一 Bot, 以便在多個「頻道」 (例如 Skype、Microsoft 小組、Facebook Messenger 等) 之間與使用者進行交談。

## <a name="walkthrough"></a>逐步解說

將調適型卡片新增至您的 bot 非常簡單。

### <a name="step-0-start-with-a-basic-message"></a>步驟 0：開始使用基本訊息

以下是標準的 Bot Framework `message`裝載, 可以傳遞至任何通道並向使用者顯示文字。

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a>步驟 1：新增調適型卡片`attachment`

若要新增只包含文字的一些豐富內容, Bot Framework 具有的`attachments`概念。 

讓我們附加可顯示自訂文字的調適型卡片。

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

### <a name="step-2-build-even-richer-cards"></a>步驟 2：建立更豐富的卡片 

調適型卡片所提供的不僅僅是可自訂的文字。 

您可以： 

* 新增`Images`至您的卡片
* 使用和組織您`Containers`的內容`Columns`
* 新增多個類型的`Actions`
* 從`Input`您的使用者收集
* 有一個卡片`show another card`
* [查看完整的架構瀏覽器](http://adaptivecards.io/explorer/)! 

## <a name="platform-sdks"></a>平臺 Sdk

如果您的 bot 是使用 .NET 或 NodeJS 開發的, 我們的程式庫可讓您更輕鬆地建立調適型卡片。

平台|安裝|進一步了解
--------|-------|----------
.NET | `Install-Package AdaptiveCards -IncludePrerelease` | [Bot Framework .NET 檔](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
NodeJS | `npm install adaptivecards` | [Bot Framework NodeJS 檔](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a>頻道狀態

Bot Framework 可讓您將 bot 發佈至多個通道。 我們正使用各種通道來提供調適型卡片的完整支援。 請參閱[合作夥伴狀態](../resources/partners.md)頁面以取得最新消息。


## <a name="dive-in"></a>深入瞭解!

我們已在本教學課程中特別說明此介面, 因此請參閱下列連結, 以探索調適型卡片可增強 bot 的更多方式。

* [流覽範例卡片](http://adaptivecards.io/samples/)以取得靈感
* 使用 [[架構瀏覽器](http://adaptivecards.io/explorer)] 學習可用的元素
* 使用[互動式視覺化檢視](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)建立卡片
* 隨時[掌握](http://adaptivecards.io/connect)您的意見反應

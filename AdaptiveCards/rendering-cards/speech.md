---
title: 處理語音
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: ea46a1c2c14a4cd2aded9672d7493561bbebbd16
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732615"
---
# <a name="handling-speech"></a><span data-ttu-id="93ec2-102">處理語音</span><span class="sxs-lookup"><span data-stu-id="93ec2-102">Handling speech</span></span>

<span data-ttu-id="93ec2-103">支援語音調適型卡片具有`speak`屬性, 其中包含有關如何大聲讀出卡片給使用者的資訊。</span><span class="sxs-lookup"><span data-stu-id="93ec2-103">To support speech adaptive Cards has the `speak` property which contains information on how a card should be read aloud to a user.</span></span>

<span data-ttu-id="93ec2-104">聲控標籤可以使用[SSML 標記](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx)來標注。</span><span class="sxs-lookup"><span data-stu-id="93ec2-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="93ec2-105">SSML 讓您能夠控制語音的速度、音調、變化。</span><span class="sxs-lookup"><span data-stu-id="93ec2-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="93ec2-106">它甚至可讓您從自己的服務串流音訊或轉譯 TTS 音訊串流, 讓您有很多的自訂。</span><span class="sxs-lookup"><span data-stu-id="93ec2-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="93ec2-107">有兩種模式可供主應用程式用來說屬性使用方式:</span><span class="sxs-lookup"><span data-stu-id="93ec2-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="93ec2-108">**傳遞**時-當卡片傳遞時, 用戶端可能會選擇讀取卡片的 [說話] 屬性, 以描述整個卡片。</span><span class="sxs-lookup"><span data-stu-id="93ec2-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="93ec2-109">依**需求**-為了支援更豐富的協助工具模型, 架構支援每個元素的「朗讀」標記。</span><span class="sxs-lookup"><span data-stu-id="93ec2-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="93ec2-110">這可讓用戶端將每個元素讀取至具有協助工具需求的收件者。</span><span class="sxs-lookup"><span data-stu-id="93ec2-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>


---
title: 動作
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34283b52f0c4902c71ea33634676832c7dfec5c9
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733105"
---
# <a name="actions"></a><span data-ttu-id="77d36-102">動作</span><span class="sxs-lookup"><span data-stu-id="77d36-102">Actions</span></span>

<span data-ttu-id="77d36-103">根據預設, 動作將會轉譯為卡片上的按鈕, 但會由您的應用程式決定, 使其行為如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="77d36-103">By default, the actions will render as buttons on the card, but it's up to your app to make them behave as you expect.</span></span> <span data-ttu-id="77d36-104">每個 SDK 都有相當於`OnAction`您必須處理的事件。</span><span class="sxs-lookup"><span data-stu-id="77d36-104">Each SDK has the equivalent of an `OnAction` event that you must handle.</span></span>

* <span data-ttu-id="77d36-105">**OpenUrl** -開啟指定`url`的。</span><span class="sxs-lookup"><span data-stu-id="77d36-105">**Action.OpenUrl** - open the specified `url`.</span></span>  
* <span data-ttu-id="77d36-106">**動作。提交**-接受提交的結果, 並將其傳送至來源。</span><span class="sxs-lookup"><span data-stu-id="77d36-106">**Action.Submit** - take the result of the submit and send it to the source.</span></span> <span data-ttu-id="77d36-107">您要如何將它傳送到卡片的來源, 完全由您決定。</span><span class="sxs-lookup"><span data-stu-id="77d36-107">How you send it to the source of the card is entirely up to you.</span></span>
* <span data-ttu-id="77d36-108">**ShowCard** -叫用對話方塊, 並將子卡片轉譯成該對話方塊。</span><span class="sxs-lookup"><span data-stu-id="77d36-108">**Action.ShowCard** - invokes a dialog and renders the sub-card into that dialog.</span></span> <span data-ttu-id="77d36-109">請注意, 如果`ShowCardActionMode`設定為`popup`, 您只需要處理此情況。</span><span class="sxs-lookup"><span data-stu-id="77d36-109">Note that you only need to handle this if `ShowCardActionMode` is set to `popup`.</span></span>
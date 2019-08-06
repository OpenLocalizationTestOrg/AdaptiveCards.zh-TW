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
# <a name="actions"></a>動作

根據預設, 動作將會轉譯為卡片上的按鈕, 但會由您的應用程式決定, 使其行為如預期般運作。 每個 SDK 都有相當於`OnAction`您必須處理的事件。

* **OpenUrl** -開啟指定`url`的。  
* **動作。提交**-接受提交的結果, 並將其傳送至來源。 您要如何將它傳送到卡片的來源, 完全由您決定。
* **ShowCard** -叫用對話方塊, 並將子卡片轉譯成該對話方塊。 請注意, 如果`ShowCardActionMode`設定為`popup`, 您只需要處理此情況。
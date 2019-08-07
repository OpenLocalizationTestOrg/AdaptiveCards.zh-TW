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
# <a name="handling-speech"></a>處理語音

支援語音調適型卡片具有`speak`屬性, 其中包含有關如何大聲讀出卡片給使用者的資訊。

聲控標籤可以使用[SSML 標記](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx)來標注。 SSML 讓您能夠控制語音的速度、音調、變化。  它甚至可讓您從自己的服務串流音訊或轉譯 TTS 音訊串流, 讓您有很多的自訂。

有兩種模式可供主應用程式用來說屬性使用方式:
* **傳遞**時-當卡片傳遞時, 用戶端可能會選擇讀取卡片的 [說話] 屬性, 以描述整個卡片。
* 依**需求**-為了支援更豐富的協助工具模型, 架構支援每個元素的「朗讀」標記。  
這可讓用戶端將每個元素讀取至具有協助工具需求的收件者。


---
title: Adaptive Cards Roadmap
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: b11edbedca83bb26d2990d029a220165f68bc1ca
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733090"
---
# <a name="future-work"></a>未來工作

雖然我們已建立絕佳的進度來定義調適型卡片, 但仍有許多工作需要執行。 我們希望透過活躍的開發人員社區 (例如 botness), 以及像是時差和 Kik 等絕佳合作夥伴, 我們可以建立一個絕佳的跨平臺卡生態系統。

## <a name="roadmap"></a>藍圖

您可以在這裡看到我們[目前的 (非最終) 藍圖](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog)。 請注意, 此處的任何專案都有可能變更, 而且不保證出貨。

## <a name="future-ideas"></a>未來的想法

以下是我們所擁有的一些未來想法, 這只是在集體討論階段。 如果您對上述任何一項感興趣, 請在批註中讓我們知道。

### <a name="great-looking-cards-from-data"></a>資料的絕佳卡片

我們知道許多卡片作者在其卡片後方已經有妥善定義的資料。 我們的計畫是探索範本化模型, 它會根據資料和妥善定義且可自訂範本的儲存機制, 來產生 (伺服器端或用戶端) 的卡片。

### <a name="make-cards-responsive"></a>使卡片回應

卡片版面配置應該會回應可用空間。 調適型卡片可調整成不同的裝置、ux 樣式和 ui 架構, 但它們尚未處於回應模式。 您必須在專案上定義其他屬性, 讓卡片產生者能夠將必要的提示提供給轉譯程式庫, 讓他們能夠以智慧方式變更配置, 以維持卡片的目的。

### <a name="responsive-exploration"></a>回應式探索

* 新增**重要性**屬性, 以標注內容的重要性。 較不重要的內容可以放入以符合可用空間
* 加入**條件約束**和**原則**屬性, 描述當條件約束無法符合時如何回應。 
  * 隱藏內容或將內容折迭成較小的大小。
  * 新增臨界值, 當超過此閾值時`columnSet` , 就會變更資料行的浮動切換。

### <a name="new-element-types"></a>新的元素類型

* 繪? -將地圖內嵌至具有互動性或回到點陣圖的卡片
* *您想要或需要哪些元素*？

### <a name="new-rendering-libraries"></a>新的轉譯程式庫

* 反應?
* Xamarin?
* *您想要的架構為何？*

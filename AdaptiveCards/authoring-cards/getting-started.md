---
title: 快速入門
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: c9a0ad07ba5fefbcdc35239591c02fe0720b5b66
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732650"
---
# <a name="getting-started"></a>快速入門 

調適型卡片是 JSON 序列化的卡片物件模型。

## <a name="adaptive-card-structure"></a>調適型卡片結構

卡片的基本結構如下所示:

* `AdaptiveCard`-根物件會描述 AdaptiveCard 本身, 包括其專案的構成專案、其動作、應如何說出它的方式, 以及呈現它所需的架構版本。
* `body`-卡片的主體是由稱為`elements`的建立區塊所組成。 元素可以用幾乎無限的安排來撰寫, 以建立許多類型的卡片。 
* `actions`-許多卡片都有一組使用者可以採取的動作。 此屬性描述通常會在底部的「動作列」中轉譯的動作。

### <a name="example-card"></a>範例卡片

這個範例卡片包含一行文字, 後面接著影像。

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png"
        }
    ]
}
```

## <a name="type-property"></a>`Type` 屬性

每個元素都`type`有一個屬性, 可識別它的物件種類。 查看上述卡片, 您可以看到我們有兩個元素: `TextBlock` `Image`和。

所有調適型卡片元素會**垂直堆疊**, 並**展開至其父系的寬度**( `display: block`以 HTML 表示)。 不過, 您可以使用`ColumnSet`來建立容器的並存資料行。

## <a name="adaptive-elements"></a>調適型元素

最基本的元素如下:

* **TextBlock** -新增包含屬性的文字區塊, 以控制文字的外觀
* **影像**-新增包含屬性的影像, 以控制影像的外觀

## <a name="container-elements"></a>容器元素

卡片也可以有可排列子專案集合的容器。

* **容器**-定義元素的集合
* **ColumnSet/column** -定義資料行的集合, 每個資料行都是一個容器
* **FactSet** -事實容器
* **ImageSet** -映射容器, 讓 UI 可以針對影像集合顯示適當的相片圖庫體驗。

## <a name="input-elements"></a>輸入元素

輸入元素可讓您要求原生 UI 來建立簡單的表單:

* **輸入。文字**-從使用者取得文字內容
* **輸入。日期**-從使用者取得日期
* **輸入。時間**-從使用者取得時間
* **輸入。數位**-從使用者取得數位
* **輸入. ChoiceSet** -提供使用者一組選擇, 並加以挑選
* **輸入。切換**-提供使用者在兩個專案之間的單一選擇, 並讓他們挑選

## <a name="actions"></a>動作

動作會將按鈕新增至卡片。 這些可以執行各種動作, 例如開啟 URL 或提交某些資料。

* **OpenUrl** -按鈕會開啟外部 URL 進行流覽
* **ShowCard** -要求向使用者顯示的子卡。
* **動作。提交**-要求將所有輸入專案收集到物件中, 然後透過主應用程式所定義的某些方法傳送給您。

> **範例動作。提交**:透過 Skype, 動作。提交會將 Bot Framework bot 活動傳回 bot, 並具有**Value**屬性, 其中包含具有所有輸入資料的物件。

## <a name="learn-more"></a>進一步了解

* [流覽範例卡片](http://adaptivecards.io/samples/)以取得靈感
* 使用 [[架構瀏覽器](http://adaptivecards.io/explorer)] 流覽可用的元素
* 使用[互動式視覺化檢視](http://adaptivecards.io/visualizer/)建立卡片
* 隨時[掌握](http://adaptivecards.io/connect)您的意見反應

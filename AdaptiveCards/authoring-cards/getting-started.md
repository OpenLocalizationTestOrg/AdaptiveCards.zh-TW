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
# <a name="getting-started"></a><span data-ttu-id="4fd47-102">快速入門</span><span class="sxs-lookup"><span data-stu-id="4fd47-102">Getting Started</span></span> 

<span data-ttu-id="4fd47-103">調適型卡片是 JSON 序列化的卡片物件模型。</span><span class="sxs-lookup"><span data-stu-id="4fd47-103">An Adaptive Card is a JSON-serialized card object model.</span></span>

## <a name="adaptive-card-structure"></a><span data-ttu-id="4fd47-104">調適型卡片結構</span><span class="sxs-lookup"><span data-stu-id="4fd47-104">Adaptive Card structure</span></span>

<span data-ttu-id="4fd47-105">卡片的基本結構如下所示:</span><span class="sxs-lookup"><span data-stu-id="4fd47-105">The basic structure of a card is as follows:</span></span>

* <span data-ttu-id="4fd47-106">`AdaptiveCard`-根物件會描述 AdaptiveCard 本身, 包括其專案的構成專案、其動作、應如何說出它的方式, 以及呈現它所需的架構版本。</span><span class="sxs-lookup"><span data-stu-id="4fd47-106">`AdaptiveCard` - The root object describes the AdaptiveCard itself, including its element makeup, its actions, how it should be spoken, and the schema version required to render it.</span></span>
* <span data-ttu-id="4fd47-107">`body`-卡片的主體是由稱為`elements`的建立區塊所組成。</span><span class="sxs-lookup"><span data-stu-id="4fd47-107">`body` - The body of the card is made up of building-blocks known as `elements`.</span></span> <span data-ttu-id="4fd47-108">元素可以用幾乎無限的安排來撰寫, 以建立許多類型的卡片。</span><span class="sxs-lookup"><span data-stu-id="4fd47-108">Elements can be composed in nearly infinite arrangements to create many types of cards.</span></span> 
* <span data-ttu-id="4fd47-109">`actions`-許多卡片都有一組使用者可以採取的動作。</span><span class="sxs-lookup"><span data-stu-id="4fd47-109">`actions` - Many cards have a set of actions a user may take on it.</span></span> <span data-ttu-id="4fd47-110">此屬性描述通常會在底部的「動作列」中轉譯的動作。</span><span class="sxs-lookup"><span data-stu-id="4fd47-110">This property describes those actions which typically get rendered in an "action bar" at the bottom.</span></span>

### <a name="example-card"></a><span data-ttu-id="4fd47-111">範例卡片</span><span class="sxs-lookup"><span data-stu-id="4fd47-111">Example Card</span></span>

<span data-ttu-id="4fd47-112">這個範例卡片包含一行文字, 後面接著影像。</span><span class="sxs-lookup"><span data-stu-id="4fd47-112">This sample card which includes a single line of text followed by an image.</span></span>

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

## <a name="type-property"></a><span data-ttu-id="4fd47-113">`Type` 屬性</span><span class="sxs-lookup"><span data-stu-id="4fd47-113">`Type` property</span></span>

<span data-ttu-id="4fd47-114">每個元素都`type`有一個屬性, 可識別它的物件種類。</span><span class="sxs-lookup"><span data-stu-id="4fd47-114">Every element has a `type` property which identifies what kind of object it is.</span></span> <span data-ttu-id="4fd47-115">查看上述卡片, 您可以看到我們有兩個元素: `TextBlock` `Image`和。</span><span class="sxs-lookup"><span data-stu-id="4fd47-115">Looking at the above card, you can see we have two elements, a `TextBlock` and an `Image`.</span></span>

<span data-ttu-id="4fd47-116">所有調適型卡片元素會**垂直堆疊**, 並**展開至其父系的寬度**( `display: block`以 HTML 表示)。</span><span class="sxs-lookup"><span data-stu-id="4fd47-116">All Adaptive Card elements **stack vertically** and **expand to the width of their parent** (think `display: block` in HTML).</span></span> <span data-ttu-id="4fd47-117">不過, 您可以使用`ColumnSet`來建立容器的並存資料行。</span><span class="sxs-lookup"><span data-stu-id="4fd47-117">However, you can use a `ColumnSet` to create side-by-side columns of containers.</span></span>

## <a name="adaptive-elements"></a><span data-ttu-id="4fd47-118">調適型元素</span><span class="sxs-lookup"><span data-stu-id="4fd47-118">Adaptive Elements</span></span>

<span data-ttu-id="4fd47-119">最基本的元素如下:</span><span class="sxs-lookup"><span data-stu-id="4fd47-119">The most fundamental elements are:</span></span>

* <span data-ttu-id="4fd47-120">**TextBlock** -新增包含屬性的文字區塊, 以控制文字的外觀</span><span class="sxs-lookup"><span data-stu-id="4fd47-120">**TextBlock** - adds a block of text with properties to control what the text looks like</span></span>
* <span data-ttu-id="4fd47-121">**影像**-新增包含屬性的影像, 以控制影像的外觀</span><span class="sxs-lookup"><span data-stu-id="4fd47-121">**Image** - adds an image with properties to control what the image looks like</span></span>

## <a name="container-elements"></a><span data-ttu-id="4fd47-122">容器元素</span><span class="sxs-lookup"><span data-stu-id="4fd47-122">Container elements</span></span>

<span data-ttu-id="4fd47-123">卡片也可以有可排列子專案集合的容器。</span><span class="sxs-lookup"><span data-stu-id="4fd47-123">Cards can also have containers, which arrange a collection of child elements.</span></span>

* <span data-ttu-id="4fd47-124">**容器**-定義元素的集合</span><span class="sxs-lookup"><span data-stu-id="4fd47-124">**Container** - Defines a a collection of elements</span></span>
* <span data-ttu-id="4fd47-125">**ColumnSet/column** -定義資料行的集合, 每個資料行都是一個容器</span><span class="sxs-lookup"><span data-stu-id="4fd47-125">**ColumnSet/Column** - Defines a collection of columns, each column is a container</span></span>
* <span data-ttu-id="4fd47-126">**FactSet** -事實容器</span><span class="sxs-lookup"><span data-stu-id="4fd47-126">**FactSet** - Container of Facts</span></span>
* <span data-ttu-id="4fd47-127">**ImageSet** -映射容器, 讓 UI 可以針對影像集合顯示適當的相片圖庫體驗。</span><span class="sxs-lookup"><span data-stu-id="4fd47-127">**ImageSet** - Container of Images so that UI can show appropriate photo gallery experience for a collection of images.</span></span>

## <a name="input-elements"></a><span data-ttu-id="4fd47-128">輸入元素</span><span class="sxs-lookup"><span data-stu-id="4fd47-128">Input elements</span></span>

<span data-ttu-id="4fd47-129">輸入元素可讓您要求原生 UI 來建立簡單的表單:</span><span class="sxs-lookup"><span data-stu-id="4fd47-129">Input elements allow you to ask for native UI to build simple forms:</span></span>

* <span data-ttu-id="4fd47-130">**輸入。文字**-從使用者取得文字內容</span><span class="sxs-lookup"><span data-stu-id="4fd47-130">**Input.Text** - get text content from the user</span></span>
* <span data-ttu-id="4fd47-131">**輸入。日期**-從使用者取得日期</span><span class="sxs-lookup"><span data-stu-id="4fd47-131">**Input.Date** - get a Date from the user</span></span>
* <span data-ttu-id="4fd47-132">**輸入。時間**-從使用者取得時間</span><span class="sxs-lookup"><span data-stu-id="4fd47-132">**Input.Time** - get a Time from the user</span></span>
* <span data-ttu-id="4fd47-133">**輸入。數位**-從使用者取得數位</span><span class="sxs-lookup"><span data-stu-id="4fd47-133">**Input.Number** - get a Number from the user</span></span>
* <span data-ttu-id="4fd47-134">**輸入. ChoiceSet** -提供使用者一組選擇, 並加以挑選</span><span class="sxs-lookup"><span data-stu-id="4fd47-134">**Input.ChoiceSet** - Give the user a set of choices and have them pick</span></span>
* <span data-ttu-id="4fd47-135">**輸入。切換**-提供使用者在兩個專案之間的單一選擇, 並讓他們挑選</span><span class="sxs-lookup"><span data-stu-id="4fd47-135">**Input.Toggle** - Give the user a single choice between two items and have them pick</span></span>

## <a name="actions"></a><span data-ttu-id="4fd47-136">動作</span><span class="sxs-lookup"><span data-stu-id="4fd47-136">Actions</span></span>

<span data-ttu-id="4fd47-137">動作會將按鈕新增至卡片。</span><span class="sxs-lookup"><span data-stu-id="4fd47-137">Actions add buttons to the card.</span></span> <span data-ttu-id="4fd47-138">這些可以執行各種動作, 例如開啟 URL 或提交某些資料。</span><span class="sxs-lookup"><span data-stu-id="4fd47-138">These can perform a variety of actions, like opening a URL or submitting some data.</span></span>

* <span data-ttu-id="4fd47-139">**OpenUrl** -按鈕會開啟外部 URL 進行流覽</span><span class="sxs-lookup"><span data-stu-id="4fd47-139">**Action.OpenUrl** - the button opens an external URL for viewing</span></span>
* <span data-ttu-id="4fd47-140">**ShowCard** -要求向使用者顯示的子卡。</span><span class="sxs-lookup"><span data-stu-id="4fd47-140">**Action.ShowCard** - Requests a sub-card to be shown to the user.</span></span>
* <span data-ttu-id="4fd47-141">**動作。提交**-要求將所有輸入專案收集到物件中, 然後透過主應用程式所定義的某些方法傳送給您。</span><span class="sxs-lookup"><span data-stu-id="4fd47-141">**Action.Submit** - Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

> <span data-ttu-id="4fd47-142">**範例動作。提交**:透過 Skype, 動作。提交會將 Bot Framework bot 活動傳回 bot, 並具有**Value**屬性, 其中包含具有所有輸入資料的物件。</span><span class="sxs-lookup"><span data-stu-id="4fd47-142">**Example Action.Submit**: With Skype, an Action.Submit will send a Bot Framework bot activity back to the bot with the **Value** property containing an object with all of the input data on it.</span></span>

## <a name="learn-more"></a><span data-ttu-id="4fd47-143">進一步了解</span><span class="sxs-lookup"><span data-stu-id="4fd47-143">Learn More</span></span>

* <span data-ttu-id="4fd47-144">[流覽範例卡片](http://adaptivecards.io/samples/)以取得靈感</span><span class="sxs-lookup"><span data-stu-id="4fd47-144">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="4fd47-145">使用 [[架構瀏覽器](http://adaptivecards.io/explorer)] 流覽可用的元素</span><span class="sxs-lookup"><span data-stu-id="4fd47-145">Use the [Schema Explorer](http://adaptivecards.io/explorer) to browse the available elements</span></span>
* <span data-ttu-id="4fd47-146">使用[互動式視覺化檢視](http://adaptivecards.io/visualizer/)建立卡片</span><span class="sxs-lookup"><span data-stu-id="4fd47-146">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/)</span></span>
* <span data-ttu-id="4fd47-147">隨時[掌握](http://adaptivecards.io/connect)您的意見反應</span><span class="sxs-lookup"><span data-stu-id="4fd47-147">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>

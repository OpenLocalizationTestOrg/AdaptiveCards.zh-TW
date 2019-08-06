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
# <a name="future-work"></a><span data-ttu-id="ceb9f-102">未來工作</span><span class="sxs-lookup"><span data-stu-id="ceb9f-102">Future work</span></span>

<span data-ttu-id="ceb9f-103">雖然我們已建立絕佳的進度來定義調適型卡片, 但仍有許多工作需要執行。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-103">While we have made excellent progress defining adaptive cards, there is still lots of work to do.</span></span> <span data-ttu-id="ceb9f-104">我們希望透過活躍的開發人員社區 (例如 botness), 以及像是時差和 Kik 等絕佳合作夥伴, 我們可以建立一個絕佳的跨平臺卡生態系統。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-104">Our hope is that through active developer communities like botness, and great partners like Slack and Kik, we can create a great ecosystem of cross-platform cards.</span></span>

## <a name="roadmap"></a><span data-ttu-id="ceb9f-105">藍圖</span><span class="sxs-lookup"><span data-stu-id="ceb9f-105">Roadmap</span></span>

<span data-ttu-id="ceb9f-106">您可以在這裡看到我們[目前的 (非最終) 藍圖](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog)。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-106">You can see our [current (non-final) roadmap here](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span></span> <span data-ttu-id="ceb9f-107">請注意, 此處的任何專案都有可能變更, 而且不保證出貨。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-107">Note that anything on here is subject to change, and is not a guarantee of shipping.</span></span>

## <a name="future-ideas"></a><span data-ttu-id="ceb9f-108">未來的想法</span><span class="sxs-lookup"><span data-stu-id="ceb9f-108">Future ideas</span></span>

<span data-ttu-id="ceb9f-109">以下是我們所擁有的一些未來想法, 這只是在集體討論階段。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-109">The following are some future ideas we have, which are simply in the brainstorm stage.</span></span> <span data-ttu-id="ceb9f-110">如果您對上述任何一項感興趣, 請在批註中讓我們知道。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-110">If you're interested in any of these, let us know in a comment.</span></span>

### <a name="great-looking-cards-from-data"></a><span data-ttu-id="ceb9f-111">資料的絕佳卡片</span><span class="sxs-lookup"><span data-stu-id="ceb9f-111">Great looking Cards from Data</span></span>

<span data-ttu-id="ceb9f-112">我們知道許多卡片作者在其卡片後方已經有妥善定義的資料。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-112">We know many card authors already have well-defined data behind their cards.</span></span> <span data-ttu-id="ceb9f-113">我們的計畫是探索範本化模型, 它會根據資料和妥善定義且可自訂範本的儲存機制, 來產生 (伺服器端或用戶端) 的卡片。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-113">Our plan is to explore a templating model that would allow cards to be generated (server side or client side) based on the data and a repository of well-defined and customizable templates.</span></span>

### <a name="make-cards-responsive"></a><span data-ttu-id="ceb9f-114">使卡片回應</span><span class="sxs-lookup"><span data-stu-id="ceb9f-114">Make cards responsive</span></span>

<span data-ttu-id="ceb9f-115">卡片版面配置應該會回應可用空間。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-115">Card layouts should be reactive to available space.</span></span> <span data-ttu-id="ceb9f-116">調適型卡片可調整成不同的裝置、ux 樣式和 ui 架構, 但它們尚未處於回應模式。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-116">Adaptive cards are adaptable to different devices, ux styles and and ui frameworks, but they are not reactive yet.</span></span> <span data-ttu-id="ceb9f-117">您必須在專案上定義其他屬性, 讓卡片產生者能夠將必要的提示提供給轉譯程式庫, 讓他們能夠以智慧方式變更配置, 以維持卡片的目的。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-117">Additional properties must be defined on elements which allow card producers to provide the necessary hints to the rendering libraries so that they can intelligently change the layout in a way which maintains the intent of the card.</span></span>

### <a name="responsive-exploration"></a><span data-ttu-id="ceb9f-118">回應式探索</span><span class="sxs-lookup"><span data-stu-id="ceb9f-118">Responsive exploration</span></span>

* <span data-ttu-id="ceb9f-119">新增**重要性**屬性, 以標注內容的重要性。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-119">Add an **importance** property which annotates importance of content.</span></span> <span data-ttu-id="ceb9f-120">較不重要的內容可以放入以符合可用空間</span><span class="sxs-lookup"><span data-stu-id="ceb9f-120">Less important content can be dropped to fit available space</span></span>
* <span data-ttu-id="ceb9f-121">加入**條件約束**和**原則**屬性, 描述當條件約束無法符合時如何回應。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-121">Add **constraints** and **policy** properties describing how to react when constraints can't be met.</span></span> 
  * <span data-ttu-id="ceb9f-122">隱藏內容或將內容折迭成較小的大小。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-122">Hide content or collapse content to smaller size.</span></span>
  * <span data-ttu-id="ceb9f-123">新增臨界值, 當超過此閾值時`columnSet` , 就會變更資料行的浮動切換。</span><span class="sxs-lookup"><span data-stu-id="ceb9f-123">Add a threshold that, when exceeded, changes `columnSet` to carousel of columns.</span></span>

### <a name="new-element-types"></a><span data-ttu-id="ceb9f-124">新的元素類型</span><span class="sxs-lookup"><span data-stu-id="ceb9f-124">New element types</span></span>

* <span data-ttu-id="ceb9f-125">繪?</span><span class="sxs-lookup"><span data-stu-id="ceb9f-125">Maps?</span></span> <span data-ttu-id="ceb9f-126">-將地圖內嵌至具有互動性或回到點陣圖的卡片</span><span class="sxs-lookup"><span data-stu-id="ceb9f-126">- embed a map into a card with interactivity or fallback to bitmap</span></span>
* <span data-ttu-id="ceb9f-127">*您想要或需要哪些元素*？</span><span class="sxs-lookup"><span data-stu-id="ceb9f-127">*What elements do you want or need*?</span></span>

### <a name="new-rendering-libraries"></a><span data-ttu-id="ceb9f-128">新的轉譯程式庫</span><span class="sxs-lookup"><span data-stu-id="ceb9f-128">New rendering libraries</span></span>

* <span data-ttu-id="ceb9f-129">反應?</span><span class="sxs-lookup"><span data-stu-id="ceb9f-129">React?</span></span>
* <span data-ttu-id="ceb9f-130">Xamarin?</span><span class="sxs-lookup"><span data-stu-id="ceb9f-130">Xamarin?</span></span>
* <span data-ttu-id="ceb9f-131">*您想要的架構為何？*</span><span class="sxs-lookup"><span data-stu-id="ceb9f-131">*What frameworks do you want?*</span></span>

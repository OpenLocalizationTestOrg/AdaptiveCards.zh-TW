---
title: 調適型卡片總覽
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: d62bae9259a45dd828028e4f866d18fc75924b0c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733110"
---
# <a name="adaptive-cards-overview"></a><span data-ttu-id="df9f1-102">調適型卡片總覽</span><span class="sxs-lookup"><span data-stu-id="df9f1-102">Adaptive Cards Overview</span></span> 

<span data-ttu-id="df9f1-103">調適型卡片是一種開放式卡片交換格式, 可讓開發人員以通用且一致的方式交換 UI 內容。</span><span class="sxs-lookup"><span data-stu-id="df9f1-103">Adaptive Cards are an open card exchange format enabling developers to exchange UI content in a common and consistent way.</span></span>

<video controls width="100%" poster="./content/videoposter.png">
    <source src="https://adaptivecardsblob.blob.core.windows.net/assets/AdaptiveCardsOverviewVideo.mp4" type="video/mp4">
</video>

## <a name="how-they-work"></a><span data-ttu-id="df9f1-104">其工作方式</span><span class="sxs-lookup"><span data-stu-id="df9f1-104">How they work</span></span>

<span data-ttu-id="df9f1-105">[**卡片作者**](authoring-cards/getting-started.md)將其內容描述為簡單的 JSON 物件。</span><span class="sxs-lookup"><span data-stu-id="df9f1-105">[**Card Authors**](authoring-cards/getting-started.md) describe their content as a simple JSON object.</span></span> <span data-ttu-id="df9f1-106">接著, 該內容可以在[**主應用程式**](rendering-cards/getting-started.md)內以原生方式轉譯, 並自動適應主機的外觀與風格。</span><span class="sxs-lookup"><span data-stu-id="df9f1-106">That content can then be rendered natively inside a [**Host Application**](rendering-cards/getting-started.md), automatically adapting to the look and feel of the Host.</span></span>

<span data-ttu-id="df9f1-107">例如, Contoso Bot 可以透過 Bot Framework 撰寫調適型卡片, 而在傳送至 Skype 時, 它看起來就像是 Skype 卡。</span><span class="sxs-lookup"><span data-stu-id="df9f1-107">For example, Contoso Bot can author an Adaptive Card through the Bot Framework, and when delivered to Skype, it will look and feel like a Skype card.</span></span> <span data-ttu-id="df9f1-108">將相同的承載傳送給 Microsoft 小組時, 它看起來像是 Microsoft 團隊。</span><span class="sxs-lookup"><span data-stu-id="df9f1-108">When that same payload is sent to Microsoft Teams, it will look and feel like Microsoft Teams.</span></span> <span data-ttu-id="df9f1-109">當有更多主機應用程式開始支援調適型卡片時, 相同的承載會自動在這些應用程式中出現, 但仍然可以完全在應用程式中運作。</span><span class="sxs-lookup"><span data-stu-id="df9f1-109">As more host apps start to support Adaptive Cards, that same payload will automatically light up inside these applications, yet still feel entirely native to the app.</span></span>

<span data-ttu-id="df9f1-110">使用者贏了, 因為大家都很熟悉。</span><span class="sxs-lookup"><span data-stu-id="df9f1-110">Users win because everything feels familiar.</span></span> <span data-ttu-id="df9f1-111">主機應用程式勝出, 因為它們控制了使用者經驗。</span><span class="sxs-lookup"><span data-stu-id="df9f1-111">Host apps win because they control the user experience.</span></span> <span data-ttu-id="df9f1-112">而且卡片作者獲勝, 因為他們的內容會變得更廣泛, 而不需要任何額外的工作。</span><span class="sxs-lookup"><span data-stu-id="df9f1-112">And Card Authors win because their content gets broader reach without any additional work.</span></span>

## <a name="goals"></a><span data-ttu-id="df9f1-113">目標</span><span class="sxs-lookup"><span data-stu-id="df9f1-113">Goals</span></span> 

<span data-ttu-id="df9f1-114">調適型卡片的目標如下:</span><span class="sxs-lookup"><span data-stu-id="df9f1-114">The goals for Adaptive Cards are:</span></span>

* <span data-ttu-id="df9f1-115">**可移植**-適用于任何應用程式、裝置和 UI 架構</span><span class="sxs-lookup"><span data-stu-id="df9f1-115">**Portable** - To any app, device, and UI framework</span></span>
* <span data-ttu-id="df9f1-116">**開放**程式庫和架構是開放原始碼且共用</span><span class="sxs-lookup"><span data-stu-id="df9f1-116">**Open** - Libraries and schema are open source and shared</span></span>
* <span data-ttu-id="df9f1-117">**低成本**-容易定義、容易使用</span><span class="sxs-lookup"><span data-stu-id="df9f1-117">**Low cost** - Easy to define, easy to consume</span></span>
* <span data-ttu-id="df9f1-118">**表達**性-以開發人員想要產生之內容的長結尾為目標</span><span class="sxs-lookup"><span data-stu-id="df9f1-118">**Expressive** - Targeted at the long tail of content that developers want to produce</span></span>
* <span data-ttu-id="df9f1-119">**純粹宣告**-不需要或不允許程式碼</span><span class="sxs-lookup"><span data-stu-id="df9f1-119">**Purely declarative** - No code is needed or allowed</span></span>
* <span data-ttu-id="df9f1-120">**自動樣式**-裝載應用程式 UX 和品牌指導方針</span><span class="sxs-lookup"><span data-stu-id="df9f1-120">**Automatically styled** - To the Host application UX and brand guidelines</span></span>

## <a name="for-card-authors"></a><span data-ttu-id="df9f1-121">針對卡片作者</span><span class="sxs-lookup"><span data-stu-id="df9f1-121">For Card Authors</span></span>
<span data-ttu-id="df9f1-122">調適型卡片適用于卡片作者:</span><span class="sxs-lookup"><span data-stu-id="df9f1-122">Adaptive Cards are great for card authors:</span></span>

* <span data-ttu-id="df9f1-123">**一個架構**-您可以取得單一格式, 將建立卡片的成本降到最低, 並將可使用的位置數目最大化。</span><span class="sxs-lookup"><span data-stu-id="df9f1-123">**One schema** - You get a single format, minimizing the cost of creating a card and maximizing the number of places it can be used.</span></span>
* <span data-ttu-id="df9f1-124">**更豐富的運算式**-您的內容可能會比您想要的更緊密地對齊, 因為您有更豐富的調色板可供繪製。</span><span class="sxs-lookup"><span data-stu-id="df9f1-124">**Richer expression** - Your content can more closely align with want you want to say because you have a richer palette to paint with.</span></span>
* <span data-ttu-id="df9f1-125">**涵蓋範圍廣泛**-您的內容會在一組更廣泛的應用程式上工作, 而不需要學習新的架構。</span><span class="sxs-lookup"><span data-stu-id="df9f1-125">**Broad reach** - Your content will work across a broader set of applications without you having to learn new schemas.</span></span>
* <span data-ttu-id="df9f1-126">**輸入控制項**-您的卡片可以包含輸入控制項, 用來從正在查看卡片的使用者收集資訊。</span><span class="sxs-lookup"><span data-stu-id="df9f1-126">**Input controls** - Your card can include input controls for gathering information from the user that is viewing the card.</span></span>
* <span data-ttu-id="df9f1-127">**更好的工具**-開放式卡片生態系統表示每個人都能分享更好的工具。</span><span class="sxs-lookup"><span data-stu-id="df9f1-127">**Better tooling** - An open card ecosystem means better tooling that is shared by everyone.</span></span>

## <a name="for-experience-owners"></a><span data-ttu-id="df9f1-128">針對經驗擁有者</span><span class="sxs-lookup"><span data-stu-id="df9f1-128">For Experience Owners</span></span>
<span data-ttu-id="df9f1-129">如果您是想要利用協力廠商內容生態系統的應用程式開發人員, 您會喜歡調適型卡片, 因為:</span><span class="sxs-lookup"><span data-stu-id="df9f1-129">If you are an app developer who wants to tap into an ecosystem of third-party content you will love Adaptive Cards because:</span></span>

* <span data-ttu-id="df9f1-130">**一致的使用者體驗**-確保您的使用者擁有一致的體驗, 因為您擁有的是轉譯的卡片樣式。</span><span class="sxs-lookup"><span data-stu-id="df9f1-130">**Consistent user experience** - You guarantee a consistent experience for your users, because you own the style of the rendered card.</span></span>
* <span data-ttu-id="df9f1-131">**原**生效-您可以取得原生效能, 因為它會直接以您的 UI 架構為目標。</span><span class="sxs-lookup"><span data-stu-id="df9f1-131">**Native performance** - You get native performance as it targets your UI framework directly.</span></span>
* <span data-ttu-id="df9f1-132">**安全**-內容會在安全的承載中傳遞, 因此您不需要開啟 UI 架構來進行原始標記和腳本編寫。</span><span class="sxs-lookup"><span data-stu-id="df9f1-132">**Safe** - Content is delivered in safe payloads so you don't have to open up your UI framework to raw markup and scripting.</span></span>
* <span data-ttu-id="df9f1-133">**輕鬆實行**-您可以從機架程式庫輕鬆地在您支援的任何平臺上進行整合</span><span class="sxs-lookup"><span data-stu-id="df9f1-133">**Easy to implement** - You get off the shelf libraries to easily integrate on any platform you support</span></span> 
* <span data-ttu-id="df9f1-134">**免費檔**-您可以節省時間, 因為您不需要製作專屬的架構並加以記載。</span><span class="sxs-lookup"><span data-stu-id="df9f1-134">**Free documentation** - You save time because you don't have to invent, implement, and document a proprietary schema.</span></span>
* <span data-ttu-id="df9f1-135">**共用的工具**-您可以節省時間, 因為您不需要建立自訂工具。</span><span class="sxs-lookup"><span data-stu-id="df9f1-135">**Shared tooling** - You save time because you don't have to create custom tooling.</span></span>

## <a name="core-design-principles"></a><span data-ttu-id="df9f1-136">核心設計原則</span><span class="sxs-lookup"><span data-stu-id="df9f1-136">Core Design Principles</span></span> 

<span data-ttu-id="df9f1-137">調適型卡片是由一組[指導原則](resources/principles.md)所驅動, 這些準則有助於保持設計的進度。</span><span class="sxs-lookup"><span data-stu-id="df9f1-137">Adaptive Cards are driven by a set of [guiding principles](resources/principles.md) that have been useful for keeping the design on track.</span></span> 

### <a name="semantic-instead-of-pixel-perfect"></a><span data-ttu-id="df9f1-138">語義, 而不是圖元完美</span><span class="sxs-lookup"><span data-stu-id="df9f1-138">Semantic instead of pixel-perfect</span></span>
<span data-ttu-id="df9f1-139">我們盡可能 striven 語義值和概念, 而不是純圖元完美的版面配置。</span><span class="sxs-lookup"><span data-stu-id="df9f1-139">We have striven as much as possible for semantic values and concepts as opposed to pure pixel-perfect layout.</span></span> <span data-ttu-id="df9f1-140">語義運算式的範例會以色彩、大小和元素 (如 FactSet 和 ImageSet) 顯示。</span><span class="sxs-lookup"><span data-stu-id="df9f1-140">Examples of semantic expression show up in colors, sizes, and in elements like FactSet and ImageSet.</span></span> <span data-ttu-id="df9f1-141">這些全都讓主應用程式能夠對實際的外觀與風格做出更佳的決策。</span><span class="sxs-lookup"><span data-stu-id="df9f1-141">These all allow the host application to make better decisions about the actual look and feel.</span></span>

### <a name="card-authors-own-the-content-host-app-owns-the-look-and-feel"></a><span data-ttu-id="df9f1-142">卡片作者擁有內容, 主應用程式擁有外觀與風格</span><span class="sxs-lookup"><span data-stu-id="df9f1-142">Card Authors own the content, Host App owns the look and feel</span></span>
<span data-ttu-id="df9f1-143">卡片作者擁有他們想要說的內容, 但顯示它的應用程式擁有其應用程式內容中卡片的外觀與風格。</span><span class="sxs-lookup"><span data-stu-id="df9f1-143">The card authors own what they want to say, but the application displaying it owns the look and feel of the card in the context of their application.</span></span>

### <a name="keep-it-simple-but-expressive"></a><span data-ttu-id="df9f1-144">保持簡單, 但表達</span><span class="sxs-lookup"><span data-stu-id="df9f1-144">Keep it simple, but expressive</span></span>
<span data-ttu-id="df9f1-145">我們想要調適型卡片是可表達和一般用途, 但我們不想要建立 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="df9f1-145">We want Adaptive Cards to be expressive and general purpose, but we don't want to build a UI framework.</span></span>  <span data-ttu-id="df9f1-146">其目標是要建立一個「合理」的中繼層, 這種方式的 Markdown 對檔而言就已經足夠表達。</span><span class="sxs-lookup"><span data-stu-id="df9f1-146">The goal is to create an intermediate layer which is "expressive enough" in the same way Markdown is expressive enough for documents.</span></span>

<span data-ttu-id="df9f1-147">藉由將重點放在簡化和表達, Markdown 建立了一個簡單且一致的檔內容描述。</span><span class="sxs-lookup"><span data-stu-id="df9f1-147">By focusing on keeping it simple and expressive, Markdown created an easy and consistent description of document content.</span></span>  <span data-ttu-id="df9f1-148">同樣地, 我們相信調適型卡片可以建立一個簡單易懂的方法來描述卡片內容。</span><span class="sxs-lookup"><span data-stu-id="df9f1-148">In the same way, we believe that Adaptive Cards can create a simple, expressive means of describing card content.</span></span>

### <a name="when-in-doubt-keep-it-out"></a><span data-ttu-id="df9f1-149">不確定時, 請將它保留</span><span class="sxs-lookup"><span data-stu-id="df9f1-149">When in doubt, keep it out</span></span>
<span data-ttu-id="df9f1-150">稍後新增的作業會更容易, 並出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="df9f1-150">It is easier to add later then it is to live with a mistake.</span></span> <span data-ttu-id="df9f1-151">如果我們發現自己的地爭論是否應該加入東西, 我們選擇將它排除。使用我們不需要支援的舊版來新增屬性, 一律會更容易。</span><span class="sxs-lookup"><span data-stu-id="df9f1-151">If we found ourselves debating whether we should add something or not, we opted to leave it out.  It is always easier to add a property than to live with a legacy we wish we didn't have to support.</span></span>


## <a name="build-2018-session"></a><span data-ttu-id="df9f1-152">組建2018會話</span><span class="sxs-lookup"><span data-stu-id="df9f1-152">Build 2018 Session</span></span>

<span data-ttu-id="df9f1-153">下列組建2018的會話展示了 Bot、Cortana、Outlook 和 Windows 中的調適型卡片。</span><span class="sxs-lookup"><span data-stu-id="df9f1-153">The following session at Build 2018 showcases Adaptive Cards in Bots, Cortana, Outlook, and Windows.</span></span> 

<iframe src="https://medius.studios.ms/Embed/Video/BRK2401?SFYT=true" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

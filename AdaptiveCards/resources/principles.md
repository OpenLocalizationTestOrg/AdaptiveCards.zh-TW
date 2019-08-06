---
title: 動機和原則
author: matthidinger
ms.author: mahiding
ms.date: 5/14/2018
ms.topic: article
ms.openlocfilehash: 243ad63fc585c5afc3fa396b86ff6261e8a7ee93
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732560"
---
# <a name="motivations-and-principles"></a><span data-ttu-id="95821-102">動機和原則</span><span class="sxs-lookup"><span data-stu-id="95821-102">Motivations and Principles</span></span>

<span data-ttu-id="95821-103">以下是 govering 調適型卡片格式演進的動機和原則。</span><span class="sxs-lookup"><span data-stu-id="95821-103">Below are the motivations and principles govering the evolution of the Adaptive Card format.</span></span>

## <a name="motivations-behind-the-format"></a><span data-ttu-id="95821-104">格式背後的動機</span><span class="sxs-lookup"><span data-stu-id="95821-104">Motivations behind the format</span></span>

<span data-ttu-id="95821-105">在2016年初, Microsoft 的幾個小組 (包括 Outlook、Windows 和 Bot Framework) 都是要實現的, 它們都想要有非常相似的東西 (「卡片」), 而且每一個都是獨立設計自己的解決方案:</span><span class="sxs-lookup"><span data-stu-id="95821-105">In early 2016, several teams at Microsoft (including Outlook, Windows and the Bot Framework) came to the realization that they all wanted something extremely similar ("cards") and that each of them were designing their own solutions independently:</span></span>

- <span data-ttu-id="95821-106">Windows 有自己的動態磚和通知格式</span><span class="sxs-lookup"><span data-stu-id="95821-106">Windows had its own Live Tiles and Notifications format</span></span>
-  <span data-ttu-id="95821-107">Bot framework 使用一組預先定義的卡片範本, 開發人員可以在傳送 Bot 訊息時從中選擇</span><span class="sxs-lookup"><span data-stu-id="95821-107">The Bot framework was using a set of predefined card templates developers could choose from when sending Bot messages</span></span>
- <span data-ttu-id="95821-108">Outlook 針對其可採取動作的訊息功能使用自己的 MessageCard 格式</span><span class="sxs-lookup"><span data-stu-id="95821-108">Outlook was using its own MessageCard format for its Actionable Messages feature</span></span>

<span data-ttu-id="95821-109">同時, 其他平臺 (例如線條、FaceBook Messenger、時差和更多) 會定義自己專屬的「卡片」格式。</span><span class="sxs-lookup"><span data-stu-id="95821-109">At the same time, other platforms such as LINE, FaceBook Messenger, Slack and more were defining their own, proprietary "card" format.</span></span> <span data-ttu-id="95821-110">因此, 有些 Microsoft 員工會收集並開始工作, 以定義單一的開放式卡片格式和一組 Sdk, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="95821-110">So a few Microsoft employees gathered up and started an effort to define a single, open card format and a set of SDKs that:</span></span>

- <span data-ttu-id="95821-111">有助於在主機之間交換卡片</span><span class="sxs-lookup"><span data-stu-id="95821-111">Would facilitate the interchange of cards between hosts</span></span>
- <span data-ttu-id="95821-112">允許每部主機控制卡片的樣式, 以確保視覺效果一致性</span><span class="sxs-lookup"><span data-stu-id="95821-112">Would allow each host to keep control over the styling of cards to ensure visual consistency</span></span>
- <span data-ttu-id="95821-113">可讓主應用程式輕鬆地透過立即可用的 Sdk, 以最少的工作顯示卡片</span><span class="sxs-lookup"><span data-stu-id="95821-113">Would make it easy for a host application to display cards with minimum effort via ready-to-use SDKs</span></span>
- <span data-ttu-id="95821-114">此外, 這也會為協力廠商提供價值, 而且最終會被業界普遍採用</span><span class="sxs-lookup"><span data-stu-id="95821-114">And that would also provide value to third parties and eventually get adopted widely by the industry</span></span>

## <a name="principles-governing-adaptive-cards"></a><span data-ttu-id="95821-115">管理調適型卡片的原則</span><span class="sxs-lookup"><span data-stu-id="95821-115">Principles governing Adaptive Cards</span></span>

1.  <span data-ttu-id="95821-116">**調適型卡片是_簡單_且_宣告_式的卡片格式**</span><span class="sxs-lookup"><span data-stu-id="95821-116">**Adaptive Card is a _simple_ and _declarative_ card format**</span></span>

    1.  <span data-ttu-id="95821-117">這不是為了 HTML 或 XAML 取代/替代</span><span class="sxs-lookup"><span data-stu-id="95821-117">It is not meant as an HTML or XAML replacement/alternative</span></span>
    2.  <span data-ttu-id="95821-118">調適型卡片沒有「程式**代碼後**置」</span><span class="sxs-lookup"><span data-stu-id="95821-118">There is **no "code behind"** with Adaptive Cards</span></span>
        1. <span data-ttu-id="95821-119">卡片作者無法使用其裝載來內嵌自訂/任意程式碼, 因此調適型卡片主機永遠不需要執行協力廠商程式碼</span><span class="sxs-lookup"><span data-stu-id="95821-119">Card authors cannot embed custom/arbitrary code with their payloads, and as a result an Adaptive Card host never needs to run third party code</span></span>
        2. <span data-ttu-id="95821-120">動性和互動性僅透過宣告式標記來達成</span><span class="sxs-lookup"><span data-stu-id="95821-120">Dynamism and interactivity are achieved solely via declarative markup</span></span>
    3.  <span data-ttu-id="95821-121">這可確保為新的平臺建立調適型卡片 SDK 所需的努力仍然合理</span><span class="sxs-lookup"><span data-stu-id="95821-121">This ensures that the effort necessary to build an Adaptive Card SDK for a new platform remains reasonable</span></span>

2.  <span data-ttu-id="95821-122">**調適型卡片格式不能強制使用任何特定的基礎技術**</span><span class="sxs-lookup"><span data-stu-id="95821-122">**The Adaptive Card format can't impose the use of any particular underlying technology**</span></span>

    1.  <span data-ttu-id="95821-123">調適型卡片格式不依賴 JavaScript、 C#、Python 或任何其他語言</span><span class="sxs-lookup"><span data-stu-id="95821-123">The Adaptive Card format does not rely on JavaScript, C#, Python or any other language</span></span>
    2.  <span data-ttu-id="95821-124">同樣地, 它也不依賴 HTML 或 XAML 或任何其他圖形/UI 架構</span><span class="sxs-lookup"><span data-stu-id="95821-124">Similarly it doesn't rely on HTML or XAML or any other graphic/UI framework</span></span>
    3.  <span data-ttu-id="95821-125">如此一來, 只要轉譯器存在, 調適型卡片就可以在任何平臺上以原生方式呈現</span><span class="sxs-lookup"><span data-stu-id="95821-125">This way, Adaptive Cards can be rendered natively on any platform for as long as a renderer exists</span></span>

3.  <span data-ttu-id="95821-126">**調適型卡片格式是_共用屬性_**</span><span class="sxs-lookup"><span data-stu-id="95821-126">**The Adaptive Card format is a _shared property_**</span></span>

    1.  <span data-ttu-id="95821-127">連同其 Sdk, 其格式是開放原始碼, 且其演進團體已驅動</span><span class="sxs-lookup"><span data-stu-id="95821-127">Along with its SDKs, the format is to be open source and its evolution community driven</span></span>
    2.  <span data-ttu-id="95821-128">因此, 此格式不是任何一個小組所擁有或驅動的</span><span class="sxs-lookup"><span data-stu-id="95821-128">The format is therefore not owned nor driven by any one team</span></span>

4.  <span data-ttu-id="95821-129">**調適型卡片格式不是設計為「僅供 Microsoft 使用」**</span><span class="sxs-lookup"><span data-stu-id="95821-129">**The Adaptive Card format is not designed "just for Microsoft's use"**</span></span>

    1.  <span data-ttu-id="95821-130">相反地, 它是為了符合各種應用程式和使用案例的需求而設計的</span><span class="sxs-lookup"><span data-stu-id="95821-130">Instead it is designed to suit the needs of a wide variety of applications and use cases</span></span>

5.  <span data-ttu-id="95821-131">**調適型_卡片工作群組負責_控制格式的演進**</span><span class="sxs-lookup"><span data-stu-id="95821-131">**The _Adaptive Card Working Group_ governs the evolution of the format**</span></span>

    1.  <span data-ttu-id="95821-132">此工作群組是由一組 Microsoft 員工所組成, 它們全都牽涉到該格式的成功</span><span class="sxs-lookup"><span data-stu-id="95821-132">This working group is comprised of a set of Microsoft employees that are all deeply involved in the success of the format</span></span>
    2.  <span data-ttu-id="95821-133">工作群組會執行每週的會議 (目前在星期一), 在這段期間會檢查功能提案、解決開放問題並進行分級, 以及追蹤 vNext 工作專案的整體進度</span><span class="sxs-lookup"><span data-stu-id="95821-133">The Working Group conducts weekly meetings (currently on Monday) during which feature proposals are reviewed, open issues are discussed and triaged and overall progress on vNext work items is tracked</span></span>
    3.  <span data-ttu-id="95821-134">工作群組會使用來自大型小組的意見反應 (包括內部 Microsoft 團隊) 來決定如何演變格式</span><span class="sxs-lookup"><span data-stu-id="95821-134">The Working Group uses feedback from the community at large, including internal Microsoft teams, to decide how the format evolves</span></span>
        1. <span data-ttu-id="95821-135">任何人都可以透過在 GitHub 中開啟問題來參與工作群組 (請參閱下文)</span><span class="sxs-lookup"><span data-stu-id="95821-135">Anyone can participate in the working group through opening issues in GitHub (see below)</span></span>
        2. <span data-ttu-id="95821-136">以「調適型卡片」架構 (做為主機或卡片作者) 的實際使用方式的問題/功能要求, 對未來格式的影響最大。</span><span class="sxs-lookup"><span data-stu-id="95821-136">Issues/feature requests rooted in actual usage of the Adaptive Cards framework (either as a host or as a card author) have the most impact on the future of the format</span></span>
    4.  <span data-ttu-id="95821-137">若要由工作群組核准, 建議的新功能:</span><span class="sxs-lookup"><span data-stu-id="95821-137">To be approved by the Working Group, proposed new features:</span></span>
        1. <span data-ttu-id="95821-138">必須以實際使用案例來對齊</span><span class="sxs-lookup"><span data-stu-id="95821-138">Must be justified by real life use cases</span></span>
        2. <span data-ttu-id="95821-139">必須具有功能規格</span><span class="sxs-lookup"><span data-stu-id="95821-139">Must have a functional specification</span></span>
    5.  <span data-ttu-id="95821-140">已核准的新功能會新增至待處理專案, 並考慮 vNext</span><span class="sxs-lookup"><span data-stu-id="95821-140">Approved new feature are added to the backlog and considered for vNext</span></span>
        1. <span data-ttu-id="95821-141">用來設定新功能優先順序的準則包括功能所啟用的各種案例、複雜度/維護性等</span><span class="sxs-lookup"><span data-stu-id="95821-141">The criteria used to prioritize new features include the breadth of scenarios the feature enables, its complexity/maintainability and more</span></span>
        2. <span data-ttu-id="95821-142">當您不確定時, 請繼續進行!</span><span class="sxs-lookup"><span data-stu-id="95821-142">When in doubt, keep it out!</span></span> <span data-ttu-id="95821-143">引進一個設計良好的功能, 比起永遠不小心的情況更容易。</span><span class="sxs-lookup"><span data-stu-id="95821-143">It's a lot easier to introduce a well designed feature later than to live with a mistake forever.</span></span>
    6.  <span data-ttu-id="95821-144">所有的新功能都會在所有支援的 Sdk 中執行</span><span class="sxs-lookup"><span data-stu-id="95821-144">All new features are implemented in all supported SDKs</span></span>
    7.  <span data-ttu-id="95821-145">所有的新功能都已記載, 並與 [範例] 資料夾中發行的測試卡片相關聯</span><span class="sxs-lookup"><span data-stu-id="95821-145">All new features are documented and associated with a test card published in the samples folder</span></span>
    8.  <span data-ttu-id="95821-146">新版本的格式和 Sdk 會經歷搶鮮版 (Beta) 階段</span><span class="sxs-lookup"><span data-stu-id="95821-146">New versions of the format and SDKs go through a beta phase</span></span>
    9.  <span data-ttu-id="95821-147">調適型卡片架構和 SDK 版本的發行排程是由品質而非日期所驅動</span><span class="sxs-lookup"><span data-stu-id="95821-147">The release schedule for Adaptive Card schema and SDK versions is driven by quality, not date</span></span>

6.  <span data-ttu-id="95821-148">**互通性**</span><span class="sxs-lookup"><span data-stu-id="95821-148">**Interoperability**</span></span>
    1.  <span data-ttu-id="95821-149">根據記載的格式 (例如, 未使用任何主機專屬的延伸模組) 所撰寫的卡片, 會在任何調適型卡片支援的主機中正確呈現</span><span class="sxs-lookup"><span data-stu-id="95821-149">Cards authored in accordance with the documented format (e.g. not using any host-specific extensions) will render properly in any Adaptive Card-capable host</span></span>
    2.  <span data-ttu-id="95821-150">此原則唯一的例外是:</span><span class="sxs-lookup"><span data-stu-id="95821-150">The only exceptions to this principles are:</span></span>
        1.  <span data-ttu-id="95821-151">某些主機可能不允許互動, 因此不會呈現輸入或動作</span><span class="sxs-lookup"><span data-stu-id="95821-151">Some hosts might not allow interactivity, and will therefore not render inputs nor actions</span></span>
        2.  <span data-ttu-id="95821-152">執行動作。提交動作是由主機決定, 而且並非所有主機都必須正確處理所有動作。請提交裝載。</span><span class="sxs-lookup"><span data-stu-id="95821-152">Execution of Action.Submit actions is at the discretion of the host, and not all hosts will necessarily properly handle all Action.Submit payloads.</span></span> <span data-ttu-id="95821-153">此外, 某些主機可能不支援動作。全部提交</span><span class="sxs-lookup"><span data-stu-id="95821-153">Furthermore, some hosts might not support Action.Submit at all</span></span>

7.  <span data-ttu-id="95821-154">**格式必須是可擴充的**</span><span class="sxs-lookup"><span data-stu-id="95821-154">**The format needs to be extensible**</span></span>

    1.  <span data-ttu-id="95821-155">主機應該要能夠自由加入自訂專案或自訂動作的支援, 但其格式不能超過</span><span class="sxs-lookup"><span data-stu-id="95821-155">Hosts should have the freedom of adding support for custom elements or custom actions that go beyond what the format is capable of</span></span>
    2.  <span data-ttu-id="95821-156">這對動作特別重要, 因為各種主機不一定支援相同的一組動作</span><span class="sxs-lookup"><span data-stu-id="95821-156">This is particularly important for actions, as various hosts don't necessarily support the same set of actions</span></span>
    3.  <span data-ttu-id="95821-157">這些新增專案是主機的判斷</span><span class="sxs-lookup"><span data-stu-id="95821-157">These additions are at the discretion of the host</span></span>
        1. <span data-ttu-id="95821-158">它們並不是調適型卡片規格的實際補充</span><span class="sxs-lookup"><span data-stu-id="95821-158">They are not a *de facto* addition to the Adaptive Card specification</span></span>
        2. <span data-ttu-id="95821-159">因此, 它們會使用與主流調適型卡片格式不相容的承載</span><span class="sxs-lookup"><span data-stu-id="95821-159">As such, they make a payload that uses them incompatible with the mainstream Adaptive Card format</span></span>
        3. <span data-ttu-id="95821-160">不過, 它們可以呈現給工作群組, 並提議為未來版本格式的新功能, 如 point #5 中所述。</span><span class="sxs-lookup"><span data-stu-id="95821-160">They can however be presented to the Working Group and proposed as new features for a future version of the format, as described in point #5</span></span>

8.  <span data-ttu-id="95821-161">**卡片作者擁有內容, 主應用程式擁有外觀與風格**</span><span class="sxs-lookup"><span data-stu-id="95821-161">**Card authors own the content, host apps own the look and feel**</span></span>

    1.  <span data-ttu-id="95821-162">主機應用程式會強加其樣式, 讓卡片外觀與風格類似于應用程式體驗的原生延伸模組</span><span class="sxs-lookup"><span data-stu-id="95821-162">Host apps impose their styling so cards look and feel like they are native extensions of the app's experience</span></span>
    2.  <span data-ttu-id="95821-163">卡片作者仍然可以指定樣式, 但只能透過色彩、大小等的語義運算式。</span><span class="sxs-lookup"><span data-stu-id="95821-163">Card authors can still specify styling, but only via semantic expressions of colors, sizes, etc.</span></span>

9.  <span data-ttu-id="95821-164">**Sdk 將提供給最熱門的開發人員平臺**</span><span class="sxs-lookup"><span data-stu-id="95821-164">**SDKs will be provided for the most popular developer platforms**</span></span>

    1.  <span data-ttu-id="95821-165">Sdk 可讓您輕鬆地在任何主機中呈現調適型卡片承載</span><span class="sxs-lookup"><span data-stu-id="95821-165">SDKs make it easy to render Adaptive Card payloads in any host</span></span>
    2.  <span data-ttu-id="95821-166">這可確保進入的屏障與協力廠商開發人員和 Microsoft 團隊一樣低</span><span class="sxs-lookup"><span data-stu-id="95821-166">This ensures the barrier to entry is as low as can be both for third party developers and Microsoft teams</span></span>

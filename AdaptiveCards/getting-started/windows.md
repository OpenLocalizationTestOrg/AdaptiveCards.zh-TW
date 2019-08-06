---
title: 適用于 Windows 開發人員的調適型卡片
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: c9ea788cfbc8e365cdece1cd8f42c3718b7bc3e7
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733115"
---
# <a name="adaptive-cards-for-windows-developers"></a><span data-ttu-id="8da10-102">適用于 Windows 開發人員的調適型卡片</span><span class="sxs-lookup"><span data-stu-id="8da10-102">Adaptive Cards for Windows Developers</span></span>



## <a name="timeline"></a><span data-ttu-id="8da10-103">時間軸</span><span class="sxs-lookup"><span data-stu-id="8da10-103">Timeline</span></span>

<span data-ttu-id="8da10-104">第一種支援調適型卡片的 Windows 體驗是時程表, 這是 Windows 10 1803 首次引進的全新體驗。</span><span class="sxs-lookup"><span data-stu-id="8da10-104">The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803.</span></span> 

![時間軸](media/windows/timeline.png)

### <a name="useractivity-api"></a><span data-ttu-id="8da10-106">UserActivity API</span><span class="sxs-lookup"><span data-stu-id="8da10-106">UserActivity API</span></span>

<span data-ttu-id="8da10-107">[`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API 會將活動填入時程表。</span><span class="sxs-lookup"><span data-stu-id="8da10-107">The [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.</span></span>

<span data-ttu-id="8da10-108">調適型卡片會透過的`Content` `VisualElement`屬性提供, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="8da10-108">The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:</span></span>

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a><span data-ttu-id="8da10-109">進一步了解</span><span class="sxs-lookup"><span data-stu-id="8da10-109">Learn more</span></span>

<span data-ttu-id="8da10-110">在組建2017的這個會話涵蓋 detial 中的使用者活動。</span><span class="sxs-lookup"><span data-stu-id="8da10-110">This session at Build 2017 covers User Activities in detial.</span></span>

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a><span data-ttu-id="8da10-111">其他 Windows 介面</span><span class="sxs-lookup"><span data-stu-id="8da10-111">Other Windows Surfaces</span></span>
<span data-ttu-id="8da10-112">我們尚無任何共用專案, 但我們正努力將調適型卡片納入更多 Windows 體驗中。</span><span class="sxs-lookup"><span data-stu-id="8da10-112">We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.</span></span>

## <a name="dive-in"></a><span data-ttu-id="8da10-113">深入瞭解!</span><span class="sxs-lookup"><span data-stu-id="8da10-113">Dive in!</span></span>

<span data-ttu-id="8da10-114">本教學課程中的表面並不多, 因此請稍後回來查看並流覽下列連結, 以深入瞭解調適型卡片。</span><span class="sxs-lookup"><span data-stu-id="8da10-114">We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.</span></span>

* <span data-ttu-id="8da10-115">[流覽範例卡片](http://adaptivecards.io/samples/)以取得靈感</span><span class="sxs-lookup"><span data-stu-id="8da10-115">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="8da10-116">使用 [[架構瀏覽器](http://adaptivecards.io/explorer)] 學習可用的元素</span><span class="sxs-lookup"><span data-stu-id="8da10-116">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="8da10-117">使用[互動式視覺化檢視](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)建立卡片</span><span class="sxs-lookup"><span data-stu-id="8da10-117">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="8da10-118">隨時[掌握](http://adaptivecards.io/connect)您的意見反應</span><span class="sxs-lookup"><span data-stu-id="8da10-118">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>

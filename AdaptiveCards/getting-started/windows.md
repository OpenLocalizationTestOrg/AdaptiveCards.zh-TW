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
# <a name="adaptive-cards-for-windows-developers"></a>適用于 Windows 開發人員的調適型卡片



## <a name="timeline"></a>時間軸

第一種支援調適型卡片的 Windows 體驗是時程表, 這是 Windows 10 1803 首次引進的全新體驗。 

![時間軸](media/windows/timeline.png)

### <a name="useractivity-api"></a>UserActivity API

[`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API 會將活動填入時程表。

調適型卡片會透過的`Content` `VisualElement`屬性提供, 如下所示:

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a>進一步了解

在組建2017的這個會話涵蓋 detial 中的使用者活動。

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a>其他 Windows 介面
我們尚無任何共用專案, 但我們正努力將調適型卡片納入更多 Windows 體驗中。

## <a name="dive-in"></a>深入瞭解!

本教學課程中的表面並不多, 因此請稍後回來查看並流覽下列連結, 以深入瞭解調適型卡片。

* [流覽範例卡片](http://adaptivecards.io/samples/)以取得靈感
* 使用 [[架構瀏覽器](http://adaptivecards.io/explorer)] 學習可用的元素
* 使用[互動式視覺化檢視](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)建立卡片
* 隨時[掌握](http://adaptivecards.io/connect)您的意見反應

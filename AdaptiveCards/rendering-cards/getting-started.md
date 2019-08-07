---
title: 在您的應用程式內呈現卡片
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: a562a05a91676dc5e6d8b51690acc4788802fb99
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732605"
---
# <a name="rendering-cards-inside-your-application"></a>在您的應用程式內呈現卡片

您可以輕鬆地在應用程式內呈現調適型卡片。 我們會提供適用于所有通用平臺的 Sdk, 並提供建立您自己的調適型卡片轉譯器的[詳細規格](implement-a-renderer.md)。

1. **安裝**轉譯器 SDK-適用于您的目標平臺。
2. **建立**轉譯器實例-設定您的應用程式樣式、規則和動作事件處理常式。
3. 將**卡片轉譯為原生 UI** , 並自動將其樣式化至您的應用程式。

## <a name="adaptive-cards-sdks"></a>調適型卡片 Sdk

|平台|安裝|組建|Docs|狀態|
|---|---|---|---|---|
| JavaScript | [![npm 安裝](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/nodejs)| [Docs](../sdk/rendering-cards/javascript/getting-started.md) | ![組建狀態](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20564.svg) |
| .NET WPF | [![Nuget 安裝](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet)| [Docs](../sdk/rendering-cards/net-wpf/getting-started.md) | ![組建狀態](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| .NET HTML | [![Nuget 安裝](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Html.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Html) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet) | [Docs](../sdk/rendering-cards/net-html/getting-started.md) | ![組建狀態](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| Windows UWP | [![Nuget 安裝](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Uwp.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Uwp) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/uwp) | [Docs](../sdk/rendering-cards/uwp/getting-started.md) | ![組建狀態](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20583.svg) |
| Android | [![Maven 中部](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/android) | [Docs](../sdk/rendering-cards/android/getting-started.md) | ![組建狀態](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/17651.svg)
| iOS | [![CocoaPods](https://img.shields.io/cocoapods/v/AdaptiveCards.svg)](https://cocoapods.org/pods/AdaptiveCards) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/ios) | [Docs](../sdk/rendering-cards/ios/getting-started.md) |  ![組建狀態](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/16990.svg) |

## <a name="create-an-instance-of-the-renderer"></a>建立轉譯器的實例

下一個步驟是建立的實例`AdaptiveCardRenderer`。 

### <a name="hook-up-action-events"></a>連結動作事件

根據預設, 動作將會轉譯為卡片上的按鈕, 但會由您的應用程式決定, 使其行為如預期般運作。 每個 SDK 都有相當於`OnAction`您必須處理的事件。

* **OpenUrl** -開啟指定`url`的。  
* **動作。提交**-接受提交的結果, 並將其傳送至來源。 您要如何將它傳送到卡片的來源, 完全由您決定。
* **ShowCard** -叫用對話方塊, 並將子卡片轉譯成該對話方塊。 請注意, 如果`ShowCardActionMode`設定為`popup`, 您只需要處理此情況。

## <a name="render-a-card"></a>呈現卡片

取得卡片承載之後, 只要呼叫轉譯器並傳入卡片即可。 您將會取回由卡片內容組成的原生 UI 物件。 現在, 請將此 UI 放在應用程式中的某處。

## <a name="customization"></a>自訂

有數種方式可以自訂轉譯的內容。 

### <a name="hostconfig"></a>HostConfig

[HostConfig](host-config.md)是共用的跨平臺設定物件, 可控制應用程式內的卡片基本樣式和行為。 它會定義字型大小、元素間的間距、色彩、支援的動作數目等事項。 

### <a name="native-platform-styling"></a>原生平臺樣式

大部分的 UI 架構都可讓您使用原生 UI 架構樣式設定轉譯的卡片。 例如, 在 HTML 中, 您可以指定 HTML 的 CSS 類別, 或在 XAML 中傳入自訂 ResourceDictionary, 以進行更精細的輸出控制。

### <a name="customize-per-element-rendering"></a>自訂每個元素的轉譯

每個 SDK 都可讓您覆寫任何元素的轉譯, 或甚至加入您定義之全新元素的支援。  例如, 您可以變更`Input.Date`轉譯器以發出您自己的自訂控制項, 同時仍保留轉譯器的其他輸出。 或者, 您可以加入您定義之`Rating`自訂專案的支援。




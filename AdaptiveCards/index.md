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
# <a name="adaptive-cards-overview"></a>調適型卡片總覽 

調適型卡片是一種開放式卡片交換格式, 可讓開發人員以通用且一致的方式交換 UI 內容。

<video controls width="100%" poster="./content/videoposter.png">
    <source src="https://adaptivecardsblob.blob.core.windows.net/assets/AdaptiveCardsOverviewVideo.mp4" type="video/mp4">
</video>

## <a name="how-they-work"></a>其工作方式

[**卡片作者**](authoring-cards/getting-started.md)將其內容描述為簡單的 JSON 物件。 接著, 該內容可以在[**主應用程式**](rendering-cards/getting-started.md)內以原生方式轉譯, 並自動適應主機的外觀與風格。

例如, Contoso Bot 可以透過 Bot Framework 撰寫調適型卡片, 而在傳送至 Skype 時, 它看起來就像是 Skype 卡。 將相同的承載傳送給 Microsoft 小組時, 它看起來像是 Microsoft 團隊。 當有更多主機應用程式開始支援調適型卡片時, 相同的承載會自動在這些應用程式中出現, 但仍然可以完全在應用程式中運作。

使用者贏了, 因為大家都很熟悉。 主機應用程式勝出, 因為它們控制了使用者經驗。 而且卡片作者獲勝, 因為他們的內容會變得更廣泛, 而不需要任何額外的工作。

## <a name="goals"></a>目標 

調適型卡片的目標如下:

* **可移植**-適用于任何應用程式、裝置和 UI 架構
* **開放**程式庫和架構是開放原始碼且共用
* **低成本**-容易定義、容易使用
* **表達**性-以開發人員想要產生之內容的長結尾為目標
* **純粹宣告**-不需要或不允許程式碼
* **自動樣式**-裝載應用程式 UX 和品牌指導方針

## <a name="for-card-authors"></a>針對卡片作者
調適型卡片適用于卡片作者:

* **一個架構**-您可以取得單一格式, 將建立卡片的成本降到最低, 並將可使用的位置數目最大化。
* **更豐富的運算式**-您的內容可能會比您想要的更緊密地對齊, 因為您有更豐富的調色板可供繪製。
* **涵蓋範圍廣泛**-您的內容會在一組更廣泛的應用程式上工作, 而不需要學習新的架構。
* **輸入控制項**-您的卡片可以包含輸入控制項, 用來從正在查看卡片的使用者收集資訊。
* **更好的工具**-開放式卡片生態系統表示每個人都能分享更好的工具。

## <a name="for-experience-owners"></a>針對經驗擁有者
如果您是想要利用協力廠商內容生態系統的應用程式開發人員, 您會喜歡調適型卡片, 因為:

* **一致的使用者體驗**-確保您的使用者擁有一致的體驗, 因為您擁有的是轉譯的卡片樣式。
* **原**生效-您可以取得原生效能, 因為它會直接以您的 UI 架構為目標。
* **安全**-內容會在安全的承載中傳遞, 因此您不需要開啟 UI 架構來進行原始標記和腳本編寫。
* **輕鬆實行**-您可以從機架程式庫輕鬆地在您支援的任何平臺上進行整合 
* **免費檔**-您可以節省時間, 因為您不需要製作專屬的架構並加以記載。
* **共用的工具**-您可以節省時間, 因為您不需要建立自訂工具。

## <a name="core-design-principles"></a>核心設計原則 

調適型卡片是由一組[指導原則](resources/principles.md)所驅動, 這些準則有助於保持設計的進度。 

### <a name="semantic-instead-of-pixel-perfect"></a>語義, 而不是圖元完美
我們盡可能 striven 語義值和概念, 而不是純圖元完美的版面配置。 語義運算式的範例會以色彩、大小和元素 (如 FactSet 和 ImageSet) 顯示。 這些全都讓主應用程式能夠對實際的外觀與風格做出更佳的決策。

### <a name="card-authors-own-the-content-host-app-owns-the-look-and-feel"></a>卡片作者擁有內容, 主應用程式擁有外觀與風格
卡片作者擁有他們想要說的內容, 但顯示它的應用程式擁有其應用程式內容中卡片的外觀與風格。

### <a name="keep-it-simple-but-expressive"></a>保持簡單, 但表達
我們想要調適型卡片是可表達和一般用途, 但我們不想要建立 UI 架構。  其目標是要建立一個「合理」的中繼層, 這種方式的 Markdown 對檔而言就已經足夠表達。

藉由將重點放在簡化和表達, Markdown 建立了一個簡單且一致的檔內容描述。  同樣地, 我們相信調適型卡片可以建立一個簡單易懂的方法來描述卡片內容。

### <a name="when-in-doubt-keep-it-out"></a>不確定時, 請將它保留
稍後新增的作業會更容易, 並出現錯誤。 如果我們發現自己的地爭論是否應該加入東西, 我們選擇將它排除。使用我們不需要支援的舊版來新增屬性, 一律會更容易。


## <a name="build-2018-session"></a>組建2018會話

下列組建2018的會話展示了 Bot、Cortana、Outlook 和 Windows 中的調適型卡片。 

<iframe src="https://medius.studios.ms/Embed/Video/BRK2401?SFYT=true" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

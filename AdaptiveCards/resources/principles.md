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
# <a name="motivations-and-principles"></a>動機和原則

以下是 govering 調適型卡片格式演進的動機和原則。

## <a name="motivations-behind-the-format"></a>格式背後的動機

在2016年初, Microsoft 的幾個小組 (包括 Outlook、Windows 和 Bot Framework) 都是要實現的, 它們都想要有非常相似的東西 (「卡片」), 而且每一個都是獨立設計自己的解決方案:

- Windows 有自己的動態磚和通知格式
-  Bot framework 使用一組預先定義的卡片範本, 開發人員可以在傳送 Bot 訊息時從中選擇
- Outlook 針對其可採取動作的訊息功能使用自己的 MessageCard 格式

同時, 其他平臺 (例如線條、FaceBook Messenger、時差和更多) 會定義自己專屬的「卡片」格式。 因此, 有些 Microsoft 員工會收集並開始工作, 以定義單一的開放式卡片格式和一組 Sdk, 如下所示:

- 有助於在主機之間交換卡片
- 允許每部主機控制卡片的樣式, 以確保視覺效果一致性
- 可讓主應用程式輕鬆地透過立即可用的 Sdk, 以最少的工作顯示卡片
- 此外, 這也會為協力廠商提供價值, 而且最終會被業界普遍採用

## <a name="principles-governing-adaptive-cards"></a>管理調適型卡片的原則

1.  **調適型卡片是_簡單_且_宣告_式的卡片格式**

    1.  這不是為了 HTML 或 XAML 取代/替代
    2.  調適型卡片沒有「程式**代碼後**置」
        1. 卡片作者無法使用其裝載來內嵌自訂/任意程式碼, 因此調適型卡片主機永遠不需要執行協力廠商程式碼
        2. 動性和互動性僅透過宣告式標記來達成
    3.  這可確保為新的平臺建立調適型卡片 SDK 所需的努力仍然合理

2.  **調適型卡片格式不能強制使用任何特定的基礎技術**

    1.  調適型卡片格式不依賴 JavaScript、 C#、Python 或任何其他語言
    2.  同樣地, 它也不依賴 HTML 或 XAML 或任何其他圖形/UI 架構
    3.  如此一來, 只要轉譯器存在, 調適型卡片就可以在任何平臺上以原生方式呈現

3.  **調適型卡片格式是_共用屬性_**

    1.  連同其 Sdk, 其格式是開放原始碼, 且其演進團體已驅動
    2.  因此, 此格式不是任何一個小組所擁有或驅動的

4.  **調適型卡片格式不是設計為「僅供 Microsoft 使用」**

    1.  相反地, 它是為了符合各種應用程式和使用案例的需求而設計的

5.  **調適型_卡片工作群組負責_控制格式的演進**

    1.  此工作群組是由一組 Microsoft 員工所組成, 它們全都牽涉到該格式的成功
    2.  工作群組會執行每週的會議 (目前在星期一), 在這段期間會檢查功能提案、解決開放問題並進行分級, 以及追蹤 vNext 工作專案的整體進度
    3.  工作群組會使用來自大型小組的意見反應 (包括內部 Microsoft 團隊) 來決定如何演變格式
        1. 任何人都可以透過在 GitHub 中開啟問題來參與工作群組 (請參閱下文)
        2. 以「調適型卡片」架構 (做為主機或卡片作者) 的實際使用方式的問題/功能要求, 對未來格式的影響最大。
    4.  若要由工作群組核准, 建議的新功能:
        1. 必須以實際使用案例來對齊
        2. 必須具有功能規格
    5.  已核准的新功能會新增至待處理專案, 並考慮 vNext
        1. 用來設定新功能優先順序的準則包括功能所啟用的各種案例、複雜度/維護性等
        2. 當您不確定時, 請繼續進行! 引進一個設計良好的功能, 比起永遠不小心的情況更容易。
    6.  所有的新功能都會在所有支援的 Sdk 中執行
    7.  所有的新功能都已記載, 並與 [範例] 資料夾中發行的測試卡片相關聯
    8.  新版本的格式和 Sdk 會經歷搶鮮版 (Beta) 階段
    9.  調適型卡片架構和 SDK 版本的發行排程是由品質而非日期所驅動

6.  **互通性**
    1.  根據記載的格式 (例如, 未使用任何主機專屬的延伸模組) 所撰寫的卡片, 會在任何調適型卡片支援的主機中正確呈現
    2.  此原則唯一的例外是:
        1.  某些主機可能不允許互動, 因此不會呈現輸入或動作
        2.  執行動作。提交動作是由主機決定, 而且並非所有主機都必須正確處理所有動作。請提交裝載。 此外, 某些主機可能不支援動作。全部提交

7.  **格式必須是可擴充的**

    1.  主機應該要能夠自由加入自訂專案或自訂動作的支援, 但其格式不能超過
    2.  這對動作特別重要, 因為各種主機不一定支援相同的一組動作
    3.  這些新增專案是主機的判斷
        1. 它們並不是調適型卡片規格的實際補充
        2. 因此, 它們會使用與主流調適型卡片格式不相容的承載
        3. 不過, 它們可以呈現給工作群組, 並提議為未來版本格式的新功能, 如 point #5 中所述。

8.  **卡片作者擁有內容, 主應用程式擁有外觀與風格**

    1.  主機應用程式會強加其樣式, 讓卡片外觀與風格類似于應用程式體驗的原生延伸模組
    2.  卡片作者仍然可以指定樣式, 但只能透過色彩、大小等的語義運算式。

9.  **Sdk 將提供給最熱門的開發人員平臺**

    1.  Sdk 可讓您輕鬆地在任何主機中呈現調適型卡片承載
    2.  這可確保進入的屏障與協力廠商開發人員和 Microsoft 團隊一樣低
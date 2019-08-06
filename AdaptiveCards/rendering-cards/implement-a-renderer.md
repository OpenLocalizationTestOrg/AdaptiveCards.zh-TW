---
title: 執行轉譯器
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: 607ce40e70e0e54e61a572853a521d2dd70a5c23
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732610"
---
# <a name="adaptive-card-renderer-specification"></a>調適型卡片轉譯器規格

下列規格說明如何在任何 UI 平臺上執行調適型卡片轉譯器。

> [!IMPORTANT]
> 
> 此內容尚未完成。 請稍後再回來查看。

## <a name="sdk-versioning"></a>SDK 版本控制

1. SDK 主要和次要版本**應**符合`schema`版本。 
1. Patch/build**應該**用於沒有架構變更的轉譯器更新。

## <a name="parsing-json"></a>剖析 JSON

### <a name="error-conditions"></a>錯誤狀況
1. 剖析器**必須**檢查它是否為有效的 JSON 內容
1. 剖析器**必須**針對架構進行驗證 (必要屬性等等)
1. 上述錯誤**必須**回報給主應用程式 (例外狀況或對應項)

### <a name="unknown-types"></a>未知的類型
1. 如果遇到未知的「類型」, 就**必須**從結果中卸載它們
1. 裝載應用程式的任何變更 (如上述)**應**回報為警告

### <a name="unknown-properties"></a>未知的屬性
1. 剖析器**必須**在元素上包含**其他**屬性

### <a name="additional-considerations"></a>其他考量
1. 屬性可能包含 SSML 標記, 而且必須以指定的方式傳回至主機應用程式 `speak`

## <a name="parsing-host-config"></a>正在剖析主機設定
1. TODO

## <a name="versioning"></a>版本控制

1. 轉譯器**必須**執行特定版本的架構。 
1. 此`AdaptiveCard`函 式`version`必須根據目前的架構版本, 為屬性提供預設值 
1. 如果轉譯器`AdaptiveCard`在中`version`遇到的屬性高於支援的版本`fallbackText` , 則**必須**改為傳回。

## <a name="rendering"></a>正在轉譯

`AdaptiveCard` 包含`body`和。`actions` `body`是的`CardElement`集合, 轉譯器將依序列舉和轉譯。 

1. 每個元素**都必須**延展到其父系的寬度 ( `display: block`以 HTML 表示)。
1. 轉譯器**必須**忽略未知的元素類型, 並繼續呈現其餘的裝載。

### <a name="spacing-and-separators"></a>間距和分隔符號

1. 每`spacing`個專案上的屬性會影響**目前**專案與**之前**的專案之間的空間量。
1. **只有**當專案前面有一個專案時, 才能套用間距。 (例如, 將不會套用至陣列中的第一個專案)
1. 轉譯器**必須**從套用至目前元素的列舉值的`hostConfig`間距中, 查閱要使用的空間量。
1. 如果元素`separator`的`true`值為, 則**必須**在目前的專案和其前面繪製可見行。
1. 分隔線**必須**使用`container.style.default.foregroundColor`繪製。
1. 只有當專案**不是**陣列中的第一個時,**才必須**繪製分隔符號。

### <a name="columns"></a>資料行

1. `Column`必須以「自動」、「延展」或加權比例來解讀。 `width`

### <a name="textblock"></a>TextBlock

1. 除非`wrap`屬性 為`true`, 否則 TextBlock 必須佔用一行。 
1. 文字區塊**應該**以省略號 (...) 修剪任何多餘的文字

#### <a name="markdown"></a>Markdown

1. 調適型卡片允許 Markdown 子集, 而且**應該**在中`TextBlock`支援。 
1. 查看完整的[markdown 需求](../authoring-cards/text-features.md)

#### <a name="formatting-functions"></a>格式化函數

1. `TextBlock`允許每個轉譯器都**必須**支援的[日期/時間格式函數](../authoring-cards/text-features.md)。
1. **所有失敗都必須**顯示卡中的原始字串。 未嘗試任何易記訊息。 (要讓開發人員立即察覺的目標是問題)

1. 待辦事項：包含 RegEx

### <a name="images"></a>影像

1. 轉譯器**應**允許主機應用程式知道所有的 HTTP 影像何時已下載, 且該卡片已「完全呈現」
1. 在下載 HTTP 映射時, 轉譯`maxImageSize`器必須檢查主機 Config param
1. 轉譯器**必須**支援`.png`和`.jpeg`
1. 轉譯器**應**支援`.gif`影像

### <a name="host-config"></a>主機設定

* 待辦事項：預設值是什麼？ 他們應該共用嗎？ 我們應該將通用的 hostConfig json 檔案內嵌在二進位檔中嗎？
* 待辦事項：我認為 HostConfig 需要進行版本設定, 才能進行剖析嗎？

[`HostConfig`](host-config.md)是共用的設定物件, 可指定調適型卡片轉譯器如何產生 UI。  

這可讓平臺不可知的屬性在不同平臺和裝置上的轉譯器之間共用。 它也允許建立工具, 讓您瞭解介面卡對指定環境的外觀與風格。

1. 轉譯器**必須**將**主機 Config**參數公開給裝載應用程式
1. 所有元素都**必須**根據其各自的主機配置設定來設計樣式

### <a name="native-platform-styling"></a>原生平臺樣式

1. 每個專案類型**都應該**附加原生平臺樣式與產生的 UI 元素。 例如, 在 HTML 中, 我們將 CSS 類別加入至專案類型, 而在 XAML 中, 我們會指派特定樣式。

## <a name="extensibility"></a>擴充性 

1. 轉譯器**必須**允許主應用程式覆寫預設元素轉譯器。 例如, 以自己`TextBlock`的邏輯取代呈現。
1. 轉譯器**必須**允許主機應用程式註冊自訂元素類型。 例如, 新增自訂`Rating`元素的支援
1. 轉譯器**必須**允許主應用程式移除對 default 元素的支援。 例如, 如果不`Action.Submit`想要支援, 請移除。

## <a name="actions"></a>動作

1. 如果 HostConfig `supportsInteractivity`為`false`, 轉譯器就**不**能呈現任何動作。
1. 屬性必須轉譯成某種動作列中的按鈕, 通常是在卡片的底部。 `actions` 
1. 當按鈕被按時, 它**必須**允許主應用程式處理事件。 
1. 事件**必須**連同動作一起傳遞所有相關聯的屬性
1. 事件**必須**沿著已執行的`AdaptiveCard`傳遞

動作 | 行為
--- | ---
**Action.OpenUrl** | 開啟外部 URL 進行觀看
**Action.ShowCard** | 要求將子卡片向使用者顯示。
**Action.Submit** | 要求將所有輸入專案收集到物件中, 然後透過主應用程式所定義的某些方法傳送給您。

### <a name="actionopenurl"></a>Action.OpenUrl
1. `Action.OpenUrl`**應該**使用原生平臺機制來開啟 URL
1. 如果無法這麼做, 則**必須**將事件引發至主機應用程式, 以處理開啟 URL。 此事件**必須**允許主機應用程式覆寫預設行為。 例如, 讓他們在自己的應用程式中開啟 URL。

### <a name="actionshowcard"></a>Action.ShowCard

1. `Action.ShowCard`**必須**以某種方式支援, 以 hostConfig 設定為基礎。 有兩種模式: inline 和 popup。 內嵌卡**應該**會自動切換卡片可見度。 在快顯模式中,**應該**對主機應用程式引發事件, 以某種方式顯示卡片。

### <a name="actionsubmit"></a>Action.Submit

[提交] 動作的行為就像是 HTML 表單提交, 不同之處在于 HTML 通常會觸發 HTTP post, 調適型卡片會將它放在每個主應用程式, 以判斷「提交」對它們的意義。 

1. 當這**必須**引發事件時, 使用者會按下叫用的動作。  
1. 屬性必須包含在回呼裝載中。 `data`
1. 針對`Action.Submit`, 轉譯器**必須**收集卡片上的所有輸入, 並取出其值。 

### <a name="selectaction"></a>selectAction

1. 如果主機`supportedInteractivity`設定為`false` , 則`selectAction` **不**能轉譯為觸控目標。
1. `Image`、 `ColumnSet`和`Column`會提供`selectAction`屬性,**應該**在使用者叫用它時執行, 例如, 藉由點擊元素。

## <a name="inputs"></a>輸入

1. 如果 HostConfig `supportsInteractivity`是`false`轉譯器, 則**不**能呈現任何輸入。
2. 輸入**應該**盡可能以最高的精確度呈現。 例如, `Input.Date`在理想情況下, 會為使用者提供日期選擇器, 但如果您無法在 UI 堆疊上這麼做, 則轉譯器**必須**切換回呈現標準的文字方塊。
3. 轉譯器**應該會**顯示`placeholderText` (如果可能)
4. 轉譯器不需要執行輸入的驗證。 調適型卡片的使用者必須計畫在其結尾驗證任何收到的資料。
5. 輸入值系結**必須**正確地進行轉義

6. 物件**必須**傳回給主應用程式, 如下所示:

   我們不會對調適型卡片中的輸入驗證做出任何承諾, 因此由接收方合作, 以適當地剖析回應。 例如, 輸入數可能會傳回 "hello", 而且需要為其做好準備。


## <a name="events"></a>事件

1. 當專案的可見度變更時, 轉譯器**應該會**引發事件, 讓主機應用程式能夠將卡片滾動到位置。

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
# <a name="adaptive-card-renderer-specification"></a><span data-ttu-id="a05aa-102">調適型卡片轉譯器規格</span><span class="sxs-lookup"><span data-stu-id="a05aa-102">Adaptive Card Renderer Specification</span></span>

<span data-ttu-id="a05aa-103">下列規格說明如何在任何 UI 平臺上執行調適型卡片轉譯器。</span><span class="sxs-lookup"><span data-stu-id="a05aa-103">The following specification describes how implement an Adaptive Card renderer on any UI platform.</span></span>

> [!IMPORTANT]
> 
> <span data-ttu-id="a05aa-104">此內容尚未完成。</span><span class="sxs-lookup"><span data-stu-id="a05aa-104">This content is not finished yet.</span></span> <span data-ttu-id="a05aa-105">請稍後再回來查看。</span><span class="sxs-lookup"><span data-stu-id="a05aa-105">Check back shortly.</span></span>

## <a name="sdk-versioning"></a><span data-ttu-id="a05aa-106">SDK 版本控制</span><span class="sxs-lookup"><span data-stu-id="a05aa-106">SDK Versioning</span></span>

1. <span data-ttu-id="a05aa-107">SDK 主要和次要版本**應**符合`schema`版本。</span><span class="sxs-lookup"><span data-stu-id="a05aa-107">The SDK major and minor version **SHOULD** match the `schema` version.</span></span> 
1. <span data-ttu-id="a05aa-108">Patch/build**應該**用於沒有架構變更的轉譯器更新。</span><span class="sxs-lookup"><span data-stu-id="a05aa-108">Patch/build **SHOULD** be used for renderer updates that don't have schema changes.</span></span>

## <a name="parsing-json"></a><span data-ttu-id="a05aa-109">剖析 JSON</span><span class="sxs-lookup"><span data-stu-id="a05aa-109">Parsing JSON</span></span>

### <a name="error-conditions"></a><span data-ttu-id="a05aa-110">錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="a05aa-110">Error conditions</span></span>
1. <span data-ttu-id="a05aa-111">剖析器**必須**檢查它是否為有效的 JSON 內容</span><span class="sxs-lookup"><span data-stu-id="a05aa-111">A parser **MUST** check that it's valid JSON content</span></span>
1. <span data-ttu-id="a05aa-112">剖析器**必須**針對架構進行驗證 (必要屬性等等)</span><span class="sxs-lookup"><span data-stu-id="a05aa-112">A parser **MUST** validate against the schema (required properties, etc)</span></span>
1. <span data-ttu-id="a05aa-113">上述錯誤**必須**回報給主應用程式 (例外狀況或對應項)</span><span class="sxs-lookup"><span data-stu-id="a05aa-113">The above errors **MUST** be reported to the host app (exception or equivalent)</span></span>

### <a name="unknown-types"></a><span data-ttu-id="a05aa-114">未知的類型</span><span class="sxs-lookup"><span data-stu-id="a05aa-114">Unknown types</span></span>
1. <span data-ttu-id="a05aa-115">如果遇到未知的「類型」, 就**必須**從結果中卸載它們</span><span class="sxs-lookup"><span data-stu-id="a05aa-115">If unknown "types" are encountered they **MUST BE DROPPED** from the result</span></span>
1. <span data-ttu-id="a05aa-116">裝載應用程式的任何變更 (如上述)**應**回報為警告</span><span class="sxs-lookup"><span data-stu-id="a05aa-116">Any alterations of the payload (like above) **SHOULD** be reported as warnings to the host app</span></span>

### <a name="unknown-properties"></a><span data-ttu-id="a05aa-117">未知的屬性</span><span class="sxs-lookup"><span data-stu-id="a05aa-117">Unknown properties</span></span>
1. <span data-ttu-id="a05aa-118">剖析器**必須**在元素上包含**其他**屬性</span><span class="sxs-lookup"><span data-stu-id="a05aa-118">A parser **MUST** include **additional** properties on elements</span></span>

### <a name="additional-considerations"></a><span data-ttu-id="a05aa-119">其他考量</span><span class="sxs-lookup"><span data-stu-id="a05aa-119">Additional considerations</span></span>
1. <span data-ttu-id="a05aa-120">屬性可能包含 SSML 標記, 而且必須以指定的方式傳回至主機應用程式 `speak`</span><span class="sxs-lookup"><span data-stu-id="a05aa-120">The `speak` property may contain SSML markup and **MUST** be returned to the host app as-specified</span></span>

## <a name="parsing-host-config"></a><span data-ttu-id="a05aa-121">正在剖析主機設定</span><span class="sxs-lookup"><span data-stu-id="a05aa-121">Parsing Host Config</span></span>
1. <span data-ttu-id="a05aa-122">TODO</span><span class="sxs-lookup"><span data-stu-id="a05aa-122">TODO</span></span>

## <a name="versioning"></a><span data-ttu-id="a05aa-123">版本控制</span><span class="sxs-lookup"><span data-stu-id="a05aa-123">Versioning</span></span>

1. <span data-ttu-id="a05aa-124">轉譯器**必須**執行特定版本的架構。</span><span class="sxs-lookup"><span data-stu-id="a05aa-124">A renderer **MUST** implement a particular version of the schema.</span></span> 
1. <span data-ttu-id="a05aa-125">此`AdaptiveCard`函 式`version`必須根據目前的架構版本, 為屬性提供預設值</span><span class="sxs-lookup"><span data-stu-id="a05aa-125">The `AdaptiveCard` constructor **MUST** give the `version` property a default value based on the current schema version</span></span> 
1. <span data-ttu-id="a05aa-126">如果轉譯器`AdaptiveCard`在中`version`遇到的屬性高於支援的版本`fallbackText` , 則**必須**改為傳回。</span><span class="sxs-lookup"><span data-stu-id="a05aa-126">If a renderer encounters a `version` property in the `AdaptiveCard` that is higher than the supported version, it **MUST** return the `fallbackText` instead.</span></span>

## <a name="rendering"></a><span data-ttu-id="a05aa-127">正在轉譯</span><span class="sxs-lookup"><span data-stu-id="a05aa-127">Rendering</span></span>

<span data-ttu-id="a05aa-128">`AdaptiveCard` 包含`body`和。`actions`</span><span class="sxs-lookup"><span data-stu-id="a05aa-128">An `AdaptiveCard` consists of a `body` and `actions`.</span></span> <span data-ttu-id="a05aa-129">`body`是的`CardElement`集合, 轉譯器將依序列舉和轉譯。</span><span class="sxs-lookup"><span data-stu-id="a05aa-129">The `body` is a collection of `CardElement`s that a renderer will enumerate and render in order.</span></span> 

1. <span data-ttu-id="a05aa-130">每個元素**都必須**延展到其父系的寬度 ( `display: block`以 HTML 表示)。</span><span class="sxs-lookup"><span data-stu-id="a05aa-130">Each Element **MUST** stretch to the width of its parent (think `display: block` in HTML).</span></span>
1. <span data-ttu-id="a05aa-131">轉譯器**必須**忽略未知的元素類型, 並繼續呈現其餘的裝載。</span><span class="sxs-lookup"><span data-stu-id="a05aa-131">A renderer **MUST** ignore unknown element types, and continue rendering the rest of the payload.</span></span>

### <a name="spacing-and-separators"></a><span data-ttu-id="a05aa-132">間距和分隔符號</span><span class="sxs-lookup"><span data-stu-id="a05aa-132">Spacing and Separators</span></span>

1. <span data-ttu-id="a05aa-133">每`spacing`個專案上的屬性會影響**目前**專案與**之前**的專案之間的空間量。</span><span class="sxs-lookup"><span data-stu-id="a05aa-133">The `spacing` property on every element influences the amount of space between the **CURRENT** element and the one **BEFORE** it.</span></span>
1. <span data-ttu-id="a05aa-134">**只有**當專案前面有一個專案時, 才能套用間距。</span><span class="sxs-lookup"><span data-stu-id="a05aa-134">Spacing **MUST ONLY** apply when there actually is an element preceding it.</span></span> <span data-ttu-id="a05aa-135">(例如, 將不會套用至陣列中的第一個專案)</span><span class="sxs-lookup"><span data-stu-id="a05aa-135">(E.g., won't apply to the first item in an array)</span></span>
1. <span data-ttu-id="a05aa-136">轉譯器**必須**從套用至目前元素的列舉值的`hostConfig`間距中, 查閱要使用的空間量。</span><span class="sxs-lookup"><span data-stu-id="a05aa-136">A renderer **MUST** look up the amount of space to use from the `hostConfig` spacing for the enum value applied to the current element.</span></span>
1. <span data-ttu-id="a05aa-137">如果元素`separator`的`true`值為, 則**必須**在目前的專案和其前面繪製可見行。</span><span class="sxs-lookup"><span data-stu-id="a05aa-137">If the element has a `separator` value of `true`, then a visible line **MUST** be drawn between the current element and the one before it.</span></span>
1. <span data-ttu-id="a05aa-138">分隔線**必須**使用`container.style.default.foregroundColor`繪製。</span><span class="sxs-lookup"><span data-stu-id="a05aa-138">The separator line **MUST** be drawn using the `container.style.default.foregroundColor`.</span></span>
1. <span data-ttu-id="a05aa-139">只有當專案**不是**陣列中的第一個時,**才必須**繪製分隔符號。</span><span class="sxs-lookup"><span data-stu-id="a05aa-139">A separator **MUST ONLY** be drawn if the item **IS NOT** the first in the array.</span></span>

### <a name="columns"></a><span data-ttu-id="a05aa-140">資料行</span><span class="sxs-lookup"><span data-stu-id="a05aa-140">Columns</span></span>

1. <span data-ttu-id="a05aa-141">`Column`必須以「自動」、「延展」或加權比例來解讀。 `width`</span><span class="sxs-lookup"><span data-stu-id="a05aa-141">`Column` `width` **MUST** be interpreted by "auto", "stretch" or a weighted ratio.</span></span>

### <a name="textblock"></a><span data-ttu-id="a05aa-142">TextBlock</span><span class="sxs-lookup"><span data-stu-id="a05aa-142">TextBlock</span></span>

1. <span data-ttu-id="a05aa-143">除非`wrap`屬性 為`true`, 否則 TextBlock 必須佔用一行。</span><span class="sxs-lookup"><span data-stu-id="a05aa-143">A TextBlock **MUST** take up a single line unless the `wrap` property is `true`.</span></span> 
1. <span data-ttu-id="a05aa-144">文字區塊**應該**以省略號 (...) 修剪任何多餘的文字</span><span class="sxs-lookup"><span data-stu-id="a05aa-144">The text block **SHOULD** trim any excess text with an ellipsis (...)</span></span>

#### <a name="markdown"></a><span data-ttu-id="a05aa-145">Markdown</span><span class="sxs-lookup"><span data-stu-id="a05aa-145">Markdown</span></span>

1. <span data-ttu-id="a05aa-146">調適型卡片允許 Markdown 子集, 而且**應該**在中`TextBlock`支援。</span><span class="sxs-lookup"><span data-stu-id="a05aa-146">Adaptive Cards allow for a subset of Markdown and **SHOULD** be supported in `TextBlock`.</span></span> 
1. <span data-ttu-id="a05aa-147">查看完整的[markdown 需求](../authoring-cards/text-features.md)</span><span class="sxs-lookup"><span data-stu-id="a05aa-147">See full [markdown requirements](../authoring-cards/text-features.md)</span></span>

#### <a name="formatting-functions"></a><span data-ttu-id="a05aa-148">格式化函數</span><span class="sxs-lookup"><span data-stu-id="a05aa-148">Formatting functions</span></span>

1. <span data-ttu-id="a05aa-149">`TextBlock`允許每個轉譯器都**必須**支援的[日期/時間格式函數](../authoring-cards/text-features.md)。</span><span class="sxs-lookup"><span data-stu-id="a05aa-149">`TextBlock` allows [DATE/TIME formatting functions](../authoring-cards/text-features.md) that **MUST** be supported on every renderer.</span></span>
1. <span data-ttu-id="a05aa-150">**所有失敗都必須**顯示卡中的原始字串。</span><span class="sxs-lookup"><span data-stu-id="a05aa-150">**ALL FAILURES MUST** display the raw string in the card.</span></span> <span data-ttu-id="a05aa-151">未嘗試任何易記訊息。</span><span class="sxs-lookup"><span data-stu-id="a05aa-151">No friendly message attempted.</span></span> <span data-ttu-id="a05aa-152">(要讓開發人員立即察覺的目標是問題)</span><span class="sxs-lookup"><span data-stu-id="a05aa-152">(The goal being to make the developer immediately aware there is a problem)</span></span>

1. <span data-ttu-id="a05aa-153">待辦事項：包含 RegEx</span><span class="sxs-lookup"><span data-stu-id="a05aa-153">TODO: Include regex</span></span>

### <a name="images"></a><span data-ttu-id="a05aa-154">影像</span><span class="sxs-lookup"><span data-stu-id="a05aa-154">Images</span></span>

1. <span data-ttu-id="a05aa-155">轉譯器**應**允許主機應用程式知道所有的 HTTP 影像何時已下載, 且該卡片已「完全呈現」</span><span class="sxs-lookup"><span data-stu-id="a05aa-155">A renderer **SHOULD** allow host apps to know when all HTTP images have been downloaded and the card is "fully rendered"</span></span>
1. <span data-ttu-id="a05aa-156">在下載 HTTP 映射時, 轉譯`maxImageSize`器必須檢查主機 Config param</span><span class="sxs-lookup"><span data-stu-id="a05aa-156">A renderer **MUST** inspect the Host Config `maxImageSize` param when downloading HTTP images</span></span>
1. <span data-ttu-id="a05aa-157">轉譯器**必須**支援`.png`和`.jpeg`</span><span class="sxs-lookup"><span data-stu-id="a05aa-157">A renderer **MUST** support `.png` and `.jpeg`</span></span>
1. <span data-ttu-id="a05aa-158">轉譯器**應**支援`.gif`影像</span><span class="sxs-lookup"><span data-stu-id="a05aa-158">A renderer **SHOULD** support `.gif` images</span></span>

### <a name="host-config"></a><span data-ttu-id="a05aa-159">主機設定</span><span class="sxs-lookup"><span data-stu-id="a05aa-159">Host Config</span></span>

* <span data-ttu-id="a05aa-160">待辦事項：預設值是什麼？</span><span class="sxs-lookup"><span data-stu-id="a05aa-160">TODO: What should the defaults be?</span></span> <span data-ttu-id="a05aa-161">他們應該共用嗎？</span><span class="sxs-lookup"><span data-stu-id="a05aa-161">Should they all share it?</span></span> <span data-ttu-id="a05aa-162">我們應該將通用的 hostConfig json 檔案內嵌在二進位檔中嗎？</span><span class="sxs-lookup"><span data-stu-id="a05aa-162">Should we embed a common hostConfig.json file in the binaries?</span></span>
* <span data-ttu-id="a05aa-163">待辦事項：我認為 HostConfig 需要進行版本設定, 才能進行剖析嗎？</span><span class="sxs-lookup"><span data-stu-id="a05aa-163">TODO: I think HostConfig needs to be versioned as well for parsing?</span></span>

<span data-ttu-id="a05aa-164">[`HostConfig`](host-config.md)是共用的設定物件, 可指定調適型卡片轉譯器如何產生 UI。</span><span class="sxs-lookup"><span data-stu-id="a05aa-164">[`HostConfig`](host-config.md) is a shared configuration object that specifies how an Adaptive Card Renderer generates UI.</span></span>  

<span data-ttu-id="a05aa-165">這可讓平臺不可知的屬性在不同平臺和裝置上的轉譯器之間共用。</span><span class="sxs-lookup"><span data-stu-id="a05aa-165">This allows properties which are platform agnostic to be shared among renderers on different platforms and devices.</span></span> <span data-ttu-id="a05aa-166">它也允許建立工具, 讓您瞭解介面卡對指定環境的外觀與風格。</span><span class="sxs-lookup"><span data-stu-id="a05aa-166">It also allows tooling to be created which gives you an idea of the look and feel that card would have for a given environment.</span></span>

1. <span data-ttu-id="a05aa-167">轉譯器**必須**將**主機 Config**參數公開給裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="a05aa-167">Renderers **MUST** expose a **Host Config** parameter to host apps</span></span>
1. <span data-ttu-id="a05aa-168">所有元素都**必須**根據其各自的主機配置設定來設計樣式</span><span class="sxs-lookup"><span data-stu-id="a05aa-168">All elements **MUST** be styled according to their respective Host Config settings</span></span>

### <a name="native-platform-styling"></a><span data-ttu-id="a05aa-169">原生平臺樣式</span><span class="sxs-lookup"><span data-stu-id="a05aa-169">Native platform styling</span></span>

1. <span data-ttu-id="a05aa-170">每個專案類型**都應該**附加原生平臺樣式與產生的 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="a05aa-170">Each element type **SHOULD** attach a native platform style with the generated UI element.</span></span> <span data-ttu-id="a05aa-171">例如, 在 HTML 中, 我們將 CSS 類別加入至專案類型, 而在 XAML 中, 我們會指派特定樣式。</span><span class="sxs-lookup"><span data-stu-id="a05aa-171">E.g., in HTML we added a CSS class to the element types, and in XAML we assign a specific Style.</span></span>

## <a name="extensibility"></a><span data-ttu-id="a05aa-172">擴充性</span><span class="sxs-lookup"><span data-stu-id="a05aa-172">Extensibility</span></span> 

1. <span data-ttu-id="a05aa-173">轉譯器**必須**允許主應用程式覆寫預設元素轉譯器。</span><span class="sxs-lookup"><span data-stu-id="a05aa-173">A renderer **MUST** allow host apps to override default element renderers.</span></span> <span data-ttu-id="a05aa-174">例如, 以自己`TextBlock`的邏輯取代呈現。</span><span class="sxs-lookup"><span data-stu-id="a05aa-174">E.g., replace `TextBlock` rendering with their own logic.</span></span>
1. <span data-ttu-id="a05aa-175">轉譯器**必須**允許主機應用程式註冊自訂元素類型。</span><span class="sxs-lookup"><span data-stu-id="a05aa-175">A renderer **MUST** allow host apps to register custom element types.</span></span> <span data-ttu-id="a05aa-176">例如, 新增自訂`Rating`元素的支援</span><span class="sxs-lookup"><span data-stu-id="a05aa-176">E.g., add support for a custom `Rating` element</span></span>
1. <span data-ttu-id="a05aa-177">轉譯器**必須**允許主應用程式移除對 default 元素的支援。</span><span class="sxs-lookup"><span data-stu-id="a05aa-177">A renderer **MUST** allow host apps to remove support for a default element.</span></span> <span data-ttu-id="a05aa-178">例如, 如果不`Action.Submit`想要支援, 請移除。</span><span class="sxs-lookup"><span data-stu-id="a05aa-178">E.g., remove `Action.Submit` if they don't want it supported.</span></span>

## <a name="actions"></a><span data-ttu-id="a05aa-179">動作</span><span class="sxs-lookup"><span data-stu-id="a05aa-179">Actions</span></span>

1. <span data-ttu-id="a05aa-180">如果 HostConfig `supportsInteractivity`為`false`, 轉譯器就**不**能呈現任何動作。</span><span class="sxs-lookup"><span data-stu-id="a05aa-180">If HostConfig `supportsInteractivity` is `false`, a renderer **MUST NOT** render any actions.</span></span>
1. <span data-ttu-id="a05aa-181">屬性必須轉譯成某種動作列中的按鈕, 通常是在卡片的底部。 `actions`</span><span class="sxs-lookup"><span data-stu-id="a05aa-181">The `actions` property **MUST** be rendered as buttons in some kind of action bar, usually at the bottom of the card.</span></span> 
1. <span data-ttu-id="a05aa-182">當按鈕被按時, 它**必須**允許主應用程式處理事件。</span><span class="sxs-lookup"><span data-stu-id="a05aa-182">When a button is tapped it **MUST** allow the host app to handle the event.</span></span> 
1. <span data-ttu-id="a05aa-183">事件**必須**連同動作一起傳遞所有相關聯的屬性</span><span class="sxs-lookup"><span data-stu-id="a05aa-183">The event **MUST** pass along all associated properties with the action</span></span>
1. <span data-ttu-id="a05aa-184">事件**必須**沿著已執行的`AdaptiveCard`傳遞</span><span class="sxs-lookup"><span data-stu-id="a05aa-184">The event **MUST** pass along the `AdaptiveCard` which was executed</span></span>

<span data-ttu-id="a05aa-185">動作</span><span class="sxs-lookup"><span data-stu-id="a05aa-185">Action</span></span> | <span data-ttu-id="a05aa-186">行為</span><span class="sxs-lookup"><span data-stu-id="a05aa-186">Behavior</span></span>
--- | ---
<span data-ttu-id="a05aa-187">**Action.OpenUrl**</span><span class="sxs-lookup"><span data-stu-id="a05aa-187">**Action.OpenUrl**</span></span> | <span data-ttu-id="a05aa-188">開啟外部 URL 進行觀看</span><span class="sxs-lookup"><span data-stu-id="a05aa-188">Open an external URL for viewing</span></span>
<span data-ttu-id="a05aa-189">**Action.ShowCard**</span><span class="sxs-lookup"><span data-stu-id="a05aa-189">**Action.ShowCard**</span></span> | <span data-ttu-id="a05aa-190">要求將子卡片向使用者顯示。</span><span class="sxs-lookup"><span data-stu-id="a05aa-190">Requests a sub-card to be shown to the user.</span></span>
<span data-ttu-id="a05aa-191">**Action.Submit**</span><span class="sxs-lookup"><span data-stu-id="a05aa-191">**Action.Submit**</span></span> | <span data-ttu-id="a05aa-192">要求將所有輸入專案收集到物件中, 然後透過主應用程式所定義的某些方法傳送給您。</span><span class="sxs-lookup"><span data-stu-id="a05aa-192">Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

### <a name="actionopenurl"></a><span data-ttu-id="a05aa-193">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="a05aa-193">Action.OpenUrl</span></span>
1. <span data-ttu-id="a05aa-194">`Action.OpenUrl`**應該**使用原生平臺機制來開啟 URL</span><span class="sxs-lookup"><span data-stu-id="a05aa-194">`Action.OpenUrl` **SHOULD** open a URL using the native platform mechanism</span></span>
1. <span data-ttu-id="a05aa-195">如果無法這麼做, 則**必須**將事件引發至主機應用程式, 以處理開啟 URL。</span><span class="sxs-lookup"><span data-stu-id="a05aa-195">If this is not possible it **MUST** raise an event to the host app to handle opening the URL.</span></span> <span data-ttu-id="a05aa-196">此事件**必須**允許主機應用程式覆寫預設行為。</span><span class="sxs-lookup"><span data-stu-id="a05aa-196">This event **MUST** allow the host app to override the default behavior.</span></span> <span data-ttu-id="a05aa-197">例如, 讓他們在自己的應用程式中開啟 URL。</span><span class="sxs-lookup"><span data-stu-id="a05aa-197">E.g., let them open the URL within their own app.</span></span>

### <a name="actionshowcard"></a><span data-ttu-id="a05aa-198">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="a05aa-198">Action.ShowCard</span></span>

1. <span data-ttu-id="a05aa-199">`Action.ShowCard`**必須**以某種方式支援, 以 hostConfig 設定為基礎。</span><span class="sxs-lookup"><span data-stu-id="a05aa-199">`Action.ShowCard` **MUST** be supported in some way, based on the hostConfig setting.</span></span> <span data-ttu-id="a05aa-200">有兩種模式: inline 和 popup。</span><span class="sxs-lookup"><span data-stu-id="a05aa-200">There are two modes: inline, and popup.</span></span> <span data-ttu-id="a05aa-201">內嵌卡**應該**會自動切換卡片可見度。</span><span class="sxs-lookup"><span data-stu-id="a05aa-201">Inline cards **SHOULD** toggle the card visibility automatically.</span></span> <span data-ttu-id="a05aa-202">在快顯模式中,**應該**對主機應用程式引發事件, 以某種方式顯示卡片。</span><span class="sxs-lookup"><span data-stu-id="a05aa-202">In popup mode, an event **SHOULD** be fired to the host app to show the card in some way.</span></span>

### <a name="actionsubmit"></a><span data-ttu-id="a05aa-203">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="a05aa-203">Action.Submit</span></span>

<span data-ttu-id="a05aa-204">[提交] 動作的行為就像是 HTML 表單提交, 不同之處在于 HTML 通常會觸發 HTTP post, 調適型卡片會將它放在每個主應用程式, 以判斷「提交」對它們的意義。</span><span class="sxs-lookup"><span data-stu-id="a05aa-204">The Submit Action behaves like an HTML form submit, except that where HTML typically triggers an HTTP post, Adaptive Cards leaves it up to each host app to determine what "submit" means to them.</span></span> 

1. <span data-ttu-id="a05aa-205">當這**必須**引發事件時, 使用者會按下叫用的動作。</span><span class="sxs-lookup"><span data-stu-id="a05aa-205">When this **MUST** raise an event the user taps the action invoked.</span></span>  
1. <span data-ttu-id="a05aa-206">屬性必須包含在回呼裝載中。 `data`</span><span class="sxs-lookup"><span data-stu-id="a05aa-206">The `data` property **MUST** be included in the callback payload.</span></span>
1. <span data-ttu-id="a05aa-207">針對`Action.Submit`, 轉譯器**必須**收集卡片上的所有輸入, 並取出其值。</span><span class="sxs-lookup"><span data-stu-id="a05aa-207">For `Action.Submit`, a renderer **MUST** gather all inputs on the card and retrieve their values.</span></span> 

### <a name="selectaction"></a><span data-ttu-id="a05aa-208">selectAction</span><span class="sxs-lookup"><span data-stu-id="a05aa-208">selectAction</span></span>

1. <span data-ttu-id="a05aa-209">如果主機`supportedInteractivity`設定為`false` , 則`selectAction` **不**能轉譯為觸控目標。</span><span class="sxs-lookup"><span data-stu-id="a05aa-209">If Host Config `supportedInteractivity` is `false` then a `selectAction` **MUST NOT** render as a touch target.</span></span>
1. <span data-ttu-id="a05aa-210">`Image`、 `ColumnSet`和`Column`會提供`selectAction`屬性,**應該**在使用者叫用它時執行, 例如, 藉由點擊元素。</span><span class="sxs-lookup"><span data-stu-id="a05aa-210">`Image`, `ColumnSet`, and `Column` offer a `selectAction` property, which **SHOULD** be executed when the user invokes it, e.g., by tapping the element.</span></span>

## <a name="inputs"></a><span data-ttu-id="a05aa-211">輸入</span><span class="sxs-lookup"><span data-stu-id="a05aa-211">Inputs</span></span>

1. <span data-ttu-id="a05aa-212">如果 HostConfig `supportsInteractivity`是`false`轉譯器, 則**不**能呈現任何輸入。</span><span class="sxs-lookup"><span data-stu-id="a05aa-212">If HostConfig `supportsInteractivity` is `false` a renderer **MUST NOT** render any inputs.</span></span>
2. <span data-ttu-id="a05aa-213">輸入**應該**盡可能以最高的精確度呈現。</span><span class="sxs-lookup"><span data-stu-id="a05aa-213">Inputs **SHOULD** render with the highest fidelity possible.</span></span> <span data-ttu-id="a05aa-214">例如, `Input.Date`在理想情況下, 會為使用者提供日期選擇器, 但如果您無法在 UI 堆疊上這麼做, 則轉譯器**必須**切換回呈現標準的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="a05aa-214">For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then the renderer **MUST** fall back to rendering a standard text box.</span></span>
3. <span data-ttu-id="a05aa-215">轉譯器**應該會**顯示`placeholderText` (如果可能)</span><span class="sxs-lookup"><span data-stu-id="a05aa-215">A renderer **SHOULD** display the `placeholderText` if possible</span></span>
4. <span data-ttu-id="a05aa-216">轉譯器不需要執行輸入的驗證。</span><span class="sxs-lookup"><span data-stu-id="a05aa-216">A renderer **DOES NOT** have to implement validation of the input.</span></span> <span data-ttu-id="a05aa-217">調適型卡片的使用者必須計畫在其結尾驗證任何收到的資料。</span><span class="sxs-lookup"><span data-stu-id="a05aa-217">Users of Adaptive Cards must plan to validate any received data on their end.</span></span>
5. <span data-ttu-id="a05aa-218">輸入值系結**必須**正確地進行轉義</span><span class="sxs-lookup"><span data-stu-id="a05aa-218">Input value binding **MUST** be properly escaped</span></span>

6. <span data-ttu-id="a05aa-219">物件**必須**傳回給主應用程式, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="a05aa-219">The object **MUST** be returned to the host app as follows:</span></span>

   <span data-ttu-id="a05aa-220">我們不會對調適型卡片中的輸入驗證做出任何承諾, 因此由接收方合作, 以適當地剖析回應。</span><span class="sxs-lookup"><span data-stu-id="a05aa-220">We do not make any promises of input validation in adaptive cards, so it's up to the receiving party to properly parse the response.</span></span> <span data-ttu-id="a05aa-221">例如, 輸入數可能會傳回 "hello", 而且需要為其做好準備。</span><span class="sxs-lookup"><span data-stu-id="a05aa-221">E.g., a Input.Number could return "hello" and they need to be prepared for that.</span></span>


## <a name="events"></a><span data-ttu-id="a05aa-222">事件</span><span class="sxs-lookup"><span data-stu-id="a05aa-222">Events</span></span>

1. <span data-ttu-id="a05aa-223">當專案的可見度變更時, 轉譯器**應該會**引發事件, 讓主機應用程式能夠將卡片滾動到位置。</span><span class="sxs-lookup"><span data-stu-id="a05aa-223">A renderer **SHOULD** fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.</span></span>

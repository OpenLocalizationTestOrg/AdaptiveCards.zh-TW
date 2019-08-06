---
title: 調適型卡片工具
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: f0c5a61d3406e1defffefc575ee0a6ec78fba93d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733025"
---
# <a name="tools-and-samples"></a><span data-ttu-id="4e861-102">工具和範例</span><span class="sxs-lookup"><span data-stu-id="4e861-102">Tools and Samples</span></span>

## <a name="card-designer"></a><span data-ttu-id="4e861-103">卡片設計工具</span><span class="sxs-lookup"><span data-stu-id="4e861-103">Card Designer</span></span> 

<span data-ttu-id="4e861-104">需要工具來設計您的卡片嗎？</span><span class="sxs-lookup"><span data-stu-id="4e861-104">Need for a tool to design your cards?</span></span> <span data-ttu-id="4e861-105">看起來不只是以瀏覽器為基礎的調適型卡片設計工具, 網址為[https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="4e861-105">Look no further than the browser-based adaptive card designer at [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span></span>

<span data-ttu-id="4e861-106">[![設計工具螢幕擷取畫面](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="4e861-106">[![designer screenshot](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span></span>

### <a name="embed-the-designer-into-your-app"></a><span data-ttu-id="4e861-107">將設計工具內嵌至您的應用程式</span><span class="sxs-lookup"><span data-stu-id="4e861-107">Embed the designer into your app</span></span>

<span data-ttu-id="4e861-108">但是當您使用 JavaScript 程式庫, 將**卡片設計工具直接內嵌到 web**應用程式時, 為什麼要將您的使用者傳送到該處。</span><span class="sxs-lookup"><span data-stu-id="4e861-108">But why send your users there when you can **embed the card designer directly into your web** app using our JavaScript library.</span></span> 

<span data-ttu-id="4e861-109">請查看[adaptivecards 設計](https://npmjs.com/adaptivecards-designer)工具套件以開始使用。</span><span class="sxs-lookup"><span data-stu-id="4e861-109">Check out the [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) package to get started.</span></span>

## <a name="schema-validation"></a><span data-ttu-id="4e861-110">結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="4e861-110">Schema validation</span></span>

<span data-ttu-id="4e861-111">架構驗證是讓撰寫變得更容易和啟用工具的強大方式。</span><span class="sxs-lookup"><span data-stu-id="4e861-111">Schema validation is a powerful way of making authoring easier and enabling tooling.</span></span>

<span data-ttu-id="4e861-112">我們提供了完整的[Json 架構](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json)檔案, 可用於編輯和驗證 json 中的調適型卡片。</span><span class="sxs-lookup"><span data-stu-id="4e861-112">We have provided a complete [JSON Schema file](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) for editing and validating adaptive cards in json.</span></span> <span data-ttu-id="4e861-113">請注意, 架構 URL 已建立版本, 較新版本的調適型卡片將會有對應的 URL。</span><span class="sxs-lookup"><span data-stu-id="4e861-113">Note that the schema URL is versioned, newer versions of Adaptive Cards will have a corresponding URL.</span></span>

<span data-ttu-id="4e861-114">在 Visual Studio 和 Visual Studio Code 中, 您可以藉由加入`$schema`參考來取得自動 Intellisense。</span><span class="sxs-lookup"><span data-stu-id="4e861-114">In Visual Studio and Visual Studio Code you can get automatic Intellisense by including a `$schema` reference.</span></span>

![bad](media/tools/invalidjson1.png)

![autocomplete](media/tools/autocomplete.png)

## <a name="example"></a><span data-ttu-id="4e861-117">範例</span><span class="sxs-lookup"><span data-stu-id="4e861-117">Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extension"></a><span data-ttu-id="4e861-118">Visual Studio Code 延伸模組</span><span class="sxs-lookup"><span data-stu-id="4e861-118">Visual Studio Code Extension</span></span>

<span data-ttu-id="4e861-119">我們建立了一個 Visual Studio 的程式碼延伸模組, 可讓您以視覺化方式呈現在編輯器內即時編輯的卡片。</span><span class="sxs-lookup"><span data-stu-id="4e861-119">We have created a Visual Studio code extension which allows you to visualize the card you are editing in real time inside the editor itself.</span></span> 

![擴充功能](media/tools/vscode-extension.png)

<span data-ttu-id="4e861-121">若要安裝, 請開啟 [擴充功能 **]**[Marketplace], 然後搜尋調適型卡片</span><span class="sxs-lookup"><span data-stu-id="4e861-121">To install, open Extensions Marketplace and search for **Adaptive Card Viewer**.</span></span>

![化](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a><span data-ttu-id="4e861-123">使用量</span><span class="sxs-lookup"><span data-stu-id="4e861-123">Usage</span></span>

<span data-ttu-id="4e861-124">當您編輯具有調適型卡片`$schema`屬性的 json 檔案時, 可以使用`Ctrl+Shift+V A`來查看。</span><span class="sxs-lookup"><span data-stu-id="4e861-124">When you are editing a .json file with an Adaptive Card `$schema` property you can view by using `Ctrl+Shift+V A`.</span></span>
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a><span data-ttu-id="4e861-125">選項</span><span class="sxs-lookup"><span data-stu-id="4e861-125">Options</span></span>

<span data-ttu-id="4e861-126">下列 Visual Studio Code 設定適用于 AdaptiveCards 檢視器。</span><span class="sxs-lookup"><span data-stu-id="4e861-126">The following Visual Studio Code setting is available for the AdaptiveCards Viewer.</span></span> <span data-ttu-id="4e861-127">這可以在 [使用者設定] 或 [工作區設定] 中設定。</span><span class="sxs-lookup"><span data-stu-id="4e861-127">This can be set in User Settings or Workspace Settings.</span></span>

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="4e861-128">WPF 視覺化檢視範例</span><span class="sxs-lookup"><span data-stu-id="4e861-128">WPF Visualizer Sample</span></span>

<span data-ttu-id="4e861-129">[WPF 視覺化檢視範例專案](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer)可讓您使用 Windows 電腦上的 WPF/Xaml 視覺化卡片。</span><span class="sxs-lookup"><span data-stu-id="4e861-129">The [WPF visualizer sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF/Xaml on a Windows machine.</span></span>  <span data-ttu-id="4e861-130">內`hostconfig`建編輯器來編輯和查看主機設定。</span><span class="sxs-lookup"><span data-stu-id="4e861-130">A `hostconfig` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="4e861-131">將這些設定儲存為 JSON, 以在應用程式中轉譯時使用它們。</span><span class="sxs-lookup"><span data-stu-id="4e861-131">Save these settings as a JSON to use them in rendering in your application.</span></span>

![wpf 視覺化檢視](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a><span data-ttu-id="4e861-133">WPF ImageRender 範例</span><span class="sxs-lookup"><span data-stu-id="4e861-133">WPF ImageRender Sample</span></span>

<span data-ttu-id="4e861-134">[ImageRender 範例專案](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender)會使用 WPF, 從命令列將任何卡片轉換成 PNG。</span><span class="sxs-lookup"><span data-stu-id="4e861-134">The [ImageRender sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) turns any card into a PNG from the command line using WPF.</span></span> 

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
# <a name="tools-and-samples"></a>工具和範例

## <a name="card-designer"></a>卡片設計工具 

需要工具來設計您的卡片嗎？ 看起來不只是以瀏覽器為基礎的調適型卡片設計工具, 網址為[https://adaptivecards.io/designer](https://adaptivecards.io/designer)

[![設計工具螢幕擷取畫面](media/tools/designer.jpg)](https://adaptivecards.io/designer)

### <a name="embed-the-designer-into-your-app"></a>將設計工具內嵌至您的應用程式

但是當您使用 JavaScript 程式庫, 將**卡片設計工具直接內嵌到 web**應用程式時, 為什麼要將您的使用者傳送到該處。 

請查看[adaptivecards 設計](https://npmjs.com/adaptivecards-designer)工具套件以開始使用。

## <a name="schema-validation"></a>結構描述驗證

架構驗證是讓撰寫變得更容易和啟用工具的強大方式。

我們提供了完整的[Json 架構](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json)檔案, 可用於編輯和驗證 json 中的調適型卡片。 請注意, 架構 URL 已建立版本, 較新版本的調適型卡片將會有對應的 URL。

在 Visual Studio 和 Visual Studio Code 中, 您可以藉由加入`$schema`參考來取得自動 Intellisense。

![bad](media/tools/invalidjson1.png)

![autocomplete](media/tools/autocomplete.png)

## <a name="example"></a>範例

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extension"></a>Visual Studio Code 延伸模組

我們建立了一個 Visual Studio 的程式碼延伸模組, 可讓您以視覺化方式呈現在編輯器內即時編輯的卡片。 

![擴充功能](media/tools/vscode-extension.png)

若要安裝, 請開啟 [擴充功能 **]**[Marketplace], 然後搜尋調適型卡片

![化](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a>使用量

當您編輯具有調適型卡片`$schema`屬性的 json 檔案時, 可以使用`Ctrl+Shift+V A`來查看。
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a>選項

下列 Visual Studio Code 設定適用于 AdaptiveCards 檢視器。 這可以在 [使用者設定] 或 [工作區設定] 中設定。

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a>WPF 視覺化檢視範例

[WPF 視覺化檢視範例專案](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer)可讓您使用 Windows 電腦上的 WPF/Xaml 視覺化卡片。  內`hostconfig`建編輯器來編輯和查看主機設定。 將這些設定儲存為 JSON, 以在應用程式中轉譯時使用它們。

![wpf 視覺化檢視](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a>WPF ImageRender 範例

[ImageRender 範例專案](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender)會使用 WPF, 從命令列將任何卡片轉換成 PNG。 

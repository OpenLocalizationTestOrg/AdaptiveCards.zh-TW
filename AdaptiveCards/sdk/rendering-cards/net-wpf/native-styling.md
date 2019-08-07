---
title: 原生樣式-.NET WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 204845f942be4e7d04e20e9cd64d826daef26e93
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732720"
---
# <a name="native-styling---net-wpf"></a>原生樣式-.NET WPF

雖然主機設定會讓您在每個平臺上取得最大的方法, 但您可能必須在每個平臺上執行一些原生樣式。 

WPF 可讓您傳遞 ResourceDictionary 以進行更細緻的樣式設定、行為、動畫等, 讓您輕鬆進行。

| 項目 | 樣式名稱 |
|---|---|
| AdaptiveCard | Adaptive.Card| 
| Action.OpenUrl  | Adaptive.Action.OpenUrl  |
| Action.ShowCard | Adaptive.Action.ShowCard |
| Action.Submit  | Adaptive.Action.Submit  |
| 「資料行」 | Adaptive.Column, Adaptive.Action.Tap |
| ColumnSet | Adaptive.ColumnSet, Adaptive.VerticalSeparator |
| 容器 | Adaptive.Container|
| Input.ChoiceSet | Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem |
| Input.Date | Adaptive.Input.Text.Date
| Input.Number | Adaptive.Input.Text.Number |
| Input.Text | Adaptive.Input.Text |
| Input.Time | Adaptive.Input.Text.Time |
| Input.Toggle| Adaptive.Input.Toggle|
| Image  | Adaptive.Image |
| ImageSet  | Adaptive.ImageSet |
| FactSet | Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value |
| TextBlock  | Adaptive.TextBlock |

這個範例 XAML 資源字典會將所有 Textblock 的背景設定為淺綠色。 您可能想要比這個更先進的東西😁

```xml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <Style x:Key="Adaptive.TextBlock" TargetType="TextBlock">
        <Setter Property="Background" Value="Aqua"></Setter>
    </Style>
</ResourceDictionary>
```
```csharp
// Use a ResourceDictionary instance
// DON'T use this property if rendering from a server
renderer.Resources = myResourceDictionary;

// ... or load it from a file path
// USE this if rendering from a server
renderer.ResourcesPath = <path-to-my-resource-dictionary.xaml>;
```

> [!IMPORTANT]
> **伺服器端映射產生的相關注意事項**WPF 轉譯器會提供`RenderCardToImageAsync`可用於產生伺服器端映射的方法。 只有在此環境中`ResourcesPath`使用時, 您才必須使用屬性。 如需詳細資訊, 請參閱[影像](../net-image/getting-started.md)轉譯檔
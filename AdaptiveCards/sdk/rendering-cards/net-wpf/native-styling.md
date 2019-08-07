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
# <a name="native-styling---net-wpf"></a><span data-ttu-id="0edee-102">原生樣式-.NET WPF</span><span class="sxs-lookup"><span data-stu-id="0edee-102">Native styling - .NET WPF</span></span>

<span data-ttu-id="0edee-103">雖然主機設定會讓您在每個平臺上取得最大的方法, 但您可能必須在每個平臺上執行一些原生樣式。</span><span class="sxs-lookup"><span data-stu-id="0edee-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="0edee-104">WPF 可讓您傳遞 ResourceDictionary 以進行更細緻的樣式設定、行為、動畫等, 讓您輕鬆進行。</span><span class="sxs-lookup"><span data-stu-id="0edee-104">WPF makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="0edee-105">項目</span><span class="sxs-lookup"><span data-stu-id="0edee-105">Element</span></span> | <span data-ttu-id="0edee-106">樣式名稱</span><span class="sxs-lookup"><span data-stu-id="0edee-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="0edee-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="0edee-107">AdaptiveCard</span></span> | <span data-ttu-id="0edee-108">Adaptive.Card</span><span class="sxs-lookup"><span data-stu-id="0edee-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="0edee-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="0edee-109">Action.OpenUrl</span></span>  | <span data-ttu-id="0edee-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="0edee-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="0edee-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="0edee-111">Action.ShowCard</span></span> | <span data-ttu-id="0edee-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="0edee-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="0edee-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="0edee-113">Action.Submit</span></span>  | <span data-ttu-id="0edee-114">Adaptive.Action.Submit</span><span class="sxs-lookup"><span data-stu-id="0edee-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="0edee-115">「資料行」</span><span class="sxs-lookup"><span data-stu-id="0edee-115">Column</span></span> | <span data-ttu-id="0edee-116">Adaptive.Column, Adaptive.Action.Tap</span><span class="sxs-lookup"><span data-stu-id="0edee-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="0edee-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="0edee-117">ColumnSet</span></span> | <span data-ttu-id="0edee-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="0edee-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="0edee-119">容器</span><span class="sxs-lookup"><span data-stu-id="0edee-119">Container</span></span> | <span data-ttu-id="0edee-120">Adaptive.Container</span><span class="sxs-lookup"><span data-stu-id="0edee-120">Adaptive.Container</span></span>|
| <span data-ttu-id="0edee-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="0edee-121">Input.ChoiceSet</span></span> | <span data-ttu-id="0edee-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="0edee-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="0edee-123">Input.Date</span><span class="sxs-lookup"><span data-stu-id="0edee-123">Input.Date</span></span> | <span data-ttu-id="0edee-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="0edee-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="0edee-125">Input.Number</span><span class="sxs-lookup"><span data-stu-id="0edee-125">Input.Number</span></span> | <span data-ttu-id="0edee-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="0edee-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="0edee-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="0edee-127">Input.Text</span></span> | <span data-ttu-id="0edee-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="0edee-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="0edee-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="0edee-129">Input.Time</span></span> | <span data-ttu-id="0edee-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="0edee-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="0edee-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="0edee-131">Input.Toggle</span></span>| <span data-ttu-id="0edee-132">Adaptive.Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="0edee-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="0edee-133">Image</span><span class="sxs-lookup"><span data-stu-id="0edee-133">Image</span></span>  | <span data-ttu-id="0edee-134">Adaptive.Image</span><span class="sxs-lookup"><span data-stu-id="0edee-134">Adaptive.Image</span></span> |
| <span data-ttu-id="0edee-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="0edee-135">ImageSet</span></span>  | <span data-ttu-id="0edee-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="0edee-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="0edee-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="0edee-137">FactSet</span></span> | <span data-ttu-id="0edee-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="0edee-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="0edee-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="0edee-139">TextBlock</span></span>  | <span data-ttu-id="0edee-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="0edee-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="0edee-141">這個範例 XAML 資源字典會將所有 Textblock 的背景設定為淺綠色。</span><span class="sxs-lookup"><span data-stu-id="0edee-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="0edee-142">您可能想要比這個更先進的東西😁</span><span class="sxs-lookup"><span data-stu-id="0edee-142">You will probably want something more advanced than this 😁</span></span>

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
> <span data-ttu-id="0edee-143">**伺服器端映射產生的相關注意事項**WPF 轉譯器會提供`RenderCardToImageAsync`可用於產生伺服器端映射的方法。</span><span class="sxs-lookup"><span data-stu-id="0edee-143">**A note about server-side image generation** The WPF renderer provides a `RenderCardToImageAsync` method that can be used for server-side image generation.</span></span> <span data-ttu-id="0edee-144">只有在此環境中`ResourcesPath`使用時, 您才必須使用屬性。</span><span class="sxs-lookup"><span data-stu-id="0edee-144">You must only use the `ResourcesPath` property if used in this environment.</span></span> <span data-ttu-id="0edee-145">如需詳細資訊, 請參閱[影像](../net-image/getting-started.md)轉譯檔</span><span class="sxs-lookup"><span data-stu-id="0edee-145">See the [Image Rendering](../net-image/getting-started.md) docs for more</span></span>
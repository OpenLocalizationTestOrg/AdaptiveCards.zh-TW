---
title: 原生樣式-UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: 565c61535adc5b316cb8b1f3ad77e511012e7612
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732540"
---
# <a name="native-styling---uwp"></a><span data-ttu-id="db934-102">原生樣式-UWP</span><span class="sxs-lookup"><span data-stu-id="db934-102">Native styling - UWP</span></span>

<span data-ttu-id="db934-103">雖然主機設定會讓您在每個平臺上取得最大的方法, 但您可能必須在每個平臺上執行一些原生樣式。</span><span class="sxs-lookup"><span data-stu-id="db934-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="db934-104">UWP 藉由讓您傳遞 ResourceDictionary 以進行更精細的樣式設定、行為、動畫等, 讓您輕鬆完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="db934-104">UWP makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="db934-105">項目</span><span class="sxs-lookup"><span data-stu-id="db934-105">Element</span></span> | <span data-ttu-id="db934-106">樣式名稱</span><span class="sxs-lookup"><span data-stu-id="db934-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="db934-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="db934-107">AdaptiveCard</span></span> | <span data-ttu-id="db934-108">Adaptive.Card</span><span class="sxs-lookup"><span data-stu-id="db934-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="db934-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="db934-109">Action.OpenUrl</span></span>  | <span data-ttu-id="db934-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="db934-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="db934-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="db934-111">Action.ShowCard</span></span> | <span data-ttu-id="db934-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="db934-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="db934-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="db934-113">Action.Submit</span></span>  | <span data-ttu-id="db934-114">Adaptive.Action.Submit</span><span class="sxs-lookup"><span data-stu-id="db934-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="db934-115">「資料行」</span><span class="sxs-lookup"><span data-stu-id="db934-115">Column</span></span> | <span data-ttu-id="db934-116">Adaptive.Column, Adaptive.Action.Tap</span><span class="sxs-lookup"><span data-stu-id="db934-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="db934-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="db934-117">ColumnSet</span></span> | <span data-ttu-id="db934-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="db934-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="db934-119">容器</span><span class="sxs-lookup"><span data-stu-id="db934-119">Container</span></span> | <span data-ttu-id="db934-120">Adaptive.Container</span><span class="sxs-lookup"><span data-stu-id="db934-120">Adaptive.Container</span></span>|
| <span data-ttu-id="db934-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="db934-121">Input.ChoiceSet</span></span> | <span data-ttu-id="db934-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="db934-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="db934-123">Input.Date</span><span class="sxs-lookup"><span data-stu-id="db934-123">Input.Date</span></span> | <span data-ttu-id="db934-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="db934-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="db934-125">Input.Number</span><span class="sxs-lookup"><span data-stu-id="db934-125">Input.Number</span></span> | <span data-ttu-id="db934-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="db934-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="db934-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="db934-127">Input.Text</span></span> | <span data-ttu-id="db934-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="db934-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="db934-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="db934-129">Input.Time</span></span> | <span data-ttu-id="db934-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="db934-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="db934-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="db934-131">Input.Toggle</span></span>| <span data-ttu-id="db934-132">Adaptive.Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="db934-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="db934-133">Image</span><span class="sxs-lookup"><span data-stu-id="db934-133">Image</span></span>  | <span data-ttu-id="db934-134">Adaptive.Image</span><span class="sxs-lookup"><span data-stu-id="db934-134">Adaptive.Image</span></span> |
| <span data-ttu-id="db934-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="db934-135">ImageSet</span></span>  | <span data-ttu-id="db934-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="db934-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="db934-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="db934-137">FactSet</span></span> | <span data-ttu-id="db934-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="db934-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="db934-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="db934-139">TextBlock</span></span>  | <span data-ttu-id="db934-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="db934-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="db934-141">這個範例 XAML 資源字典會將所有 Textblock 的背景設定為淺綠色。</span><span class="sxs-lookup"><span data-stu-id="db934-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="db934-142">您可能想要比這個更先進的東西😁</span><span class="sxs-lookup"><span data-stu-id="db934-142">You will probably want something more advanced than this 😁</span></span>

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
```

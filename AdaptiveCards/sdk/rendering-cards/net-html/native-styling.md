---
title: 原生樣式-.NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 5b829d9eefe933f133c8532030856849802c5eb5
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732835"
---
# <a name="native-styling---net-html"></a><span data-ttu-id="fd8e7-102">原生樣式-.NET HTML</span><span class="sxs-lookup"><span data-stu-id="fd8e7-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="fd8e7-103">雖然主機設定會讓您在每個平臺上取得最大的方法, 但您可能必須在每個平臺上執行一些原生樣式。</span><span class="sxs-lookup"><span data-stu-id="fd8e7-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="fd8e7-104">HTML 藉由將 CSS 類別加入至每個專案, 來簡化這項程式。</span><span class="sxs-lookup"><span data-stu-id="fd8e7-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="fd8e7-105">項目</span><span class="sxs-lookup"><span data-stu-id="fd8e7-105">Element</span></span> | <span data-ttu-id="fd8e7-106">CSS 類別</span><span class="sxs-lookup"><span data-stu-id="fd8e7-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="fd8e7-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="fd8e7-107">AdaptiveCard</span></span> | <span data-ttu-id="fd8e7-108">ac-adaptivecard</span><span class="sxs-lookup"><span data-stu-id="fd8e7-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="fd8e7-109">所有動作</span><span class="sxs-lookup"><span data-stu-id="fd8e7-109">All Actions</span></span> | <span data-ttu-id="fd8e7-110">ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="fd8e7-110">ac-pushButton</span></span> | 
| <span data-ttu-id="fd8e7-111">選取動作</span><span class="sxs-lookup"><span data-stu-id="fd8e7-111">Select Actions</span></span> | <span data-ttu-id="fd8e7-112">ac-selectable</span><span class="sxs-lookup"><span data-stu-id="fd8e7-112">ac-selectable</span></span> |
| <span data-ttu-id="fd8e7-113">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="fd8e7-113">Action.OpenUrl</span></span>  | <span data-ttu-id="fd8e7-114">ac-action-openUrl</span><span class="sxs-lookup"><span data-stu-id="fd8e7-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="fd8e7-115">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="fd8e7-115">Action.ShowCard</span></span> | <span data-ttu-id="fd8e7-116">ac-action-showCard</span><span class="sxs-lookup"><span data-stu-id="fd8e7-116">ac-action-showCard</span></span> |
| <span data-ttu-id="fd8e7-117">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="fd8e7-117">Action.Submit</span></span>  | <span data-ttu-id="fd8e7-118">ac-action-submit</span><span class="sxs-lookup"><span data-stu-id="fd8e7-118">ac-action-submit</span></span>  |
| <span data-ttu-id="fd8e7-119">ActionSet</span><span class="sxs-lookup"><span data-stu-id="fd8e7-119">ActionSet</span></span> | <span data-ttu-id="fd8e7-120">ac-actionset</span><span class="sxs-lookup"><span data-stu-id="fd8e7-120">ac-actionset</span></span> |
| <span data-ttu-id="fd8e7-121">「資料行」</span><span class="sxs-lookup"><span data-stu-id="fd8e7-121">Column</span></span> | <span data-ttu-id="fd8e7-122">ac-column</span><span class="sxs-lookup"><span data-stu-id="fd8e7-122">ac-column</span></span> |
| <span data-ttu-id="fd8e7-123">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="fd8e7-123">ColumnSet</span></span> | <span data-ttu-id="fd8e7-124">ac-columnset</span><span class="sxs-lookup"><span data-stu-id="fd8e7-124">ac-columnset</span></span> |
| <span data-ttu-id="fd8e7-125">容器</span><span class="sxs-lookup"><span data-stu-id="fd8e7-125">Container</span></span> | <span data-ttu-id="fd8e7-126">ac-container</span><span class="sxs-lookup"><span data-stu-id="fd8e7-126">ac-container</span></span> |
| <span data-ttu-id="fd8e7-127">所有輸入</span><span class="sxs-lookup"><span data-stu-id="fd8e7-127">All Inputs</span></span> | <span data-ttu-id="fd8e7-128">ac-input</span><span class="sxs-lookup"><span data-stu-id="fd8e7-128">ac-input</span></span> |
| <span data-ttu-id="fd8e7-129">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="fd8e7-129">Input.ChoiceSet</span></span> | <span data-ttu-id="fd8e7-130">ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="fd8e7-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="fd8e7-131">Input.Date</span><span class="sxs-lookup"><span data-stu-id="fd8e7-131">Input.Date</span></span> | <span data-ttu-id="fd8e7-132">ac-dateInput</span><span class="sxs-lookup"><span data-stu-id="fd8e7-132">ac-dateInput</span></span> |
| <span data-ttu-id="fd8e7-133">Input.Number</span><span class="sxs-lookup"><span data-stu-id="fd8e7-133">Input.Number</span></span> | <span data-ttu-id="fd8e7-134">ac-numberInput</span><span class="sxs-lookup"><span data-stu-id="fd8e7-134">ac-numberInput</span></span> |
| <span data-ttu-id="fd8e7-135">Input.Text</span><span class="sxs-lookup"><span data-stu-id="fd8e7-135">Input.Text</span></span> | <span data-ttu-id="fd8e7-136">ac-textInput</span><span class="sxs-lookup"><span data-stu-id="fd8e7-136">ac-textInput</span></span> |
| <span data-ttu-id="fd8e7-137">Input.Time</span><span class="sxs-lookup"><span data-stu-id="fd8e7-137">Input.Time</span></span> | <span data-ttu-id="fd8e7-138">ac-timeInput</span><span class="sxs-lookup"><span data-stu-id="fd8e7-138">ac-timeInput</span></span> |
| <span data-ttu-id="fd8e7-139">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="fd8e7-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="fd8e7-140">Image</span><span class="sxs-lookup"><span data-stu-id="fd8e7-140">Image</span></span>  | <span data-ttu-id="fd8e7-141">ac-image</span><span class="sxs-lookup"><span data-stu-id="fd8e7-141">ac-image</span></span> |
| <span data-ttu-id="fd8e7-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="fd8e7-142">ImageSet</span></span>  | <span data-ttu-id="fd8e7-143">ac-imageset</span><span class="sxs-lookup"><span data-stu-id="fd8e7-143">ac-imageset</span></span> |
| <span data-ttu-id="fd8e7-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="fd8e7-144">FactSet</span></span> | <span data-ttu-id="fd8e7-145">ac-factset</span><span class="sxs-lookup"><span data-stu-id="fd8e7-145">ac-factset</span></span> |
| <span data-ttu-id="fd8e7-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="fd8e7-146">TextBlock</span></span>  | <span data-ttu-id="fd8e7-147">ac-textblock</span><span class="sxs-lookup"><span data-stu-id="fd8e7-147">ac-textblock</span></span> |
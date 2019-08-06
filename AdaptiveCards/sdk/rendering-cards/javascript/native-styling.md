---
title: 原生樣式-JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 687a90dd572ba2df786816fdd9dc313746cca982
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732620"
---
# <a name="native-styling---javascript"></a><span data-ttu-id="dd0ad-102">原生樣式-JavaScript</span><span class="sxs-lookup"><span data-stu-id="dd0ad-102">Native styling - JavaScript</span></span>

<span data-ttu-id="dd0ad-103">使用 CSS 來進行卡片 HTML 的精細樣式設定。</span><span class="sxs-lookup"><span data-stu-id="dd0ad-103">Use CSS for fine-grained styling of the card HTML.</span></span>

<span data-ttu-id="dd0ad-104">下列 CSS 類別將會新增至各種元素。</span><span class="sxs-lookup"><span data-stu-id="dd0ad-104">The following CSS classes will be added to various elements.</span></span>

| <span data-ttu-id="dd0ad-105">CSS 類別</span><span class="sxs-lookup"><span data-stu-id="dd0ad-105">CSS class</span></span> | <span data-ttu-id="dd0ad-106">使用量</span><span class="sxs-lookup"><span data-stu-id="dd0ad-106">Usage</span></span> |
|---|---|
| <span data-ttu-id="dd0ad-107">.ac-container</span><span class="sxs-lookup"><span data-stu-id="dd0ad-107">.ac-container</span></span> | <span data-ttu-id="dd0ad-108">容器</span><span class="sxs-lookup"><span data-stu-id="dd0ad-108">containers</span></span> |
| <span data-ttu-id="dd0ad-109">.ac-selectable</span><span class="sxs-lookup"><span data-stu-id="dd0ad-109">.ac-selectable</span></span>  | <span data-ttu-id="dd0ad-110">元素具有`selectAction`</span><span class="sxs-lookup"><span data-stu-id="dd0ad-110">elements with `selectAction`</span></span> |
| <span data-ttu-id="dd0ad-111">.ac-image</span><span class="sxs-lookup"><span data-stu-id="dd0ad-111">.ac-image</span></span> | <span data-ttu-id="dd0ad-112">影像</span><span class="sxs-lookup"><span data-stu-id="dd0ad-112">image</span></span> |
| <span data-ttu-id="dd0ad-113">.ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="dd0ad-113">.ac-pushButton</span></span> | <span data-ttu-id="dd0ad-114">像按鈕一樣呈現的動作</span><span class="sxs-lookup"><span data-stu-id="dd0ad-114">actions rendered like buttons</span></span> |
| <span data-ttu-id="dd0ad-115">.ac-linkButton</span><span class="sxs-lookup"><span data-stu-id="dd0ad-115">.ac-linkButton</span></span>  | <span data-ttu-id="dd0ad-116">呈現的動作, 例如連結</span><span class="sxs-lookup"><span data-stu-id="dd0ad-116">actions rendered like links</span></span> |
| <span data-ttu-id="dd0ad-117">.ac-input</span><span class="sxs-lookup"><span data-stu-id="dd0ad-117">.ac-input</span></span> | <span data-ttu-id="dd0ad-118">輸入控制項</span><span class="sxs-lookup"><span data-stu-id="dd0ad-118">input controls</span></span>|
| <span data-ttu-id="dd0ad-119">.ac-textInput</span><span class="sxs-lookup"><span data-stu-id="dd0ad-119">.ac-textInput</span></span>| <span data-ttu-id="dd0ad-120">文字輸入</span><span class="sxs-lookup"><span data-stu-id="dd0ad-120">text input</span></span> |
| <span data-ttu-id="dd0ad-121">.ac-multiline</span><span class="sxs-lookup"><span data-stu-id="dd0ad-121">.ac-multiline</span></span> | <span data-ttu-id="dd0ad-122">多行文字輸入</span><span class="sxs-lookup"><span data-stu-id="dd0ad-122">multiline text input</span></span> |
| <span data-ttu-id="dd0ad-123">.ac-numberInput</span><span class="sxs-lookup"><span data-stu-id="dd0ad-123">.ac-numberInput</span></span> | <span data-ttu-id="dd0ad-124">數位輸入</span><span class="sxs-lookup"><span data-stu-id="dd0ad-124">number input</span></span>|
| <span data-ttu-id="dd0ad-125">.ac-dateInput</span><span class="sxs-lookup"><span data-stu-id="dd0ad-125">.ac-dateInput</span></span> | <span data-ttu-id="dd0ad-126">日期輸入</span><span class="sxs-lookup"><span data-stu-id="dd0ad-126">date input</span></span>|
| <span data-ttu-id="dd0ad-127">.ac-timeInput</span><span class="sxs-lookup"><span data-stu-id="dd0ad-127">.ac-timeInput</span></span> | <span data-ttu-id="dd0ad-128">時間輸入</span><span class="sxs-lookup"><span data-stu-id="dd0ad-128">time input</span></span> |
| <span data-ttu-id="dd0ad-129">.ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="dd0ad-129">.ac-multichoiceInput</span></span> | <span data-ttu-id="dd0ad-130">multichoice 輸入</span><span class="sxs-lookup"><span data-stu-id="dd0ad-130">multichoice input</span></span>|
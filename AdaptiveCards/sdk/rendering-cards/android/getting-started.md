---
title: Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 4723175bf94685c22d99fb15f3d1887ac37b8c57
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733005"
---
# <a name="getting-started---android"></a><span data-ttu-id="c31ad-102">開始使用-Android</span><span class="sxs-lookup"><span data-stu-id="c31ad-102">Getting started - Android</span></span>

<span data-ttu-id="c31ad-103">這是以 Android 原生控制項為目標的轉譯器。</span><span class="sxs-lookup"><span data-stu-id="c31ad-103">This is a renderer which targets Android native controls.</span></span>

## <a name="install-maven-package"></a><span data-ttu-id="c31ad-104">安裝 Maven 套件</span><span class="sxs-lookup"><span data-stu-id="c31ad-104">Install Maven package</span></span>

<span data-ttu-id="c31ad-105">[![Maven 中部](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span><span class="sxs-lookup"><span data-stu-id="c31ad-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span></span>

<span data-ttu-id="c31ad-106">您可以找到已發佈的封裝</span><span class="sxs-lookup"><span data-stu-id="c31ad-106">You can find the published packages</span></span> ![這裡](https://search.maven.org/search?q=g:io.adaptivecards)

<span data-ttu-id="c31ad-108">若要在專案中包含程式庫, 您必須將這一行包含在專案 gradle 中。 [相依性] 區段下的 [組建]</span><span class="sxs-lookup"><span data-stu-id="c31ad-108">To include library to your project you must include this line into your project gradle.build under the dependencies section</span></span>

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
<span data-ttu-id="c31ad-109">您必須根據想要包含在專案中的版本來變更版本號碼</span><span class="sxs-lookup"><span data-stu-id="c31ad-109">You need to change the version number depending on the version you want to include into your project</span></span>

## <a name="add-import"></a><span data-ttu-id="c31ad-110">加入匯入</span><span class="sxs-lookup"><span data-stu-id="c31ad-110">Add import</span></span>

<span data-ttu-id="c31ad-111">若要包含物件模型, 請新增此匯入</span><span class="sxs-lookup"><span data-stu-id="c31ad-111">To include the object model, add this import</span></span>

```
 import io.adaptivecards.objectmodel.*;
```

<span data-ttu-id="c31ad-112">若要包含轉譯器, 請新增此匯入</span><span class="sxs-lookup"><span data-stu-id="c31ad-112">To include the renderer, add this import</span></span>

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a><span data-ttu-id="c31ad-113">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c31ad-113">Next steps</span></span>

<span data-ttu-id="c31ad-114">請參閱[呈現卡片](render-a-card.md)以進行後續步驟!</span><span class="sxs-lookup"><span data-stu-id="c31ad-114">See [Render a card](render-a-card.md) for the next steps!</span></span>

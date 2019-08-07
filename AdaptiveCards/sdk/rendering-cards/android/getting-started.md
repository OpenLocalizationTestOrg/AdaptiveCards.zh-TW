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
# <a name="getting-started---android"></a>開始使用-Android

這是以 Android 原生控制項為目標的轉譯器。

## <a name="install-maven-package"></a>安裝 Maven 套件

[![Maven 中部](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)

您可以找到已發佈的封裝 ![這裡](https://search.maven.org/search?q=g:io.adaptivecards)

若要在專案中包含程式庫, 您必須將這一行包含在專案 gradle 中。 [相依性] 區段下的 [組建]

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
您必須根據想要包含在專案中的版本來變更版本號碼

## <a name="add-import"></a>加入匯入

若要包含物件模型, 請新增此匯入

```
 import io.adaptivecards.objectmodel.*;
```

若要包含轉譯器, 請新增此匯入

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a>後續步驟

請參閱[呈現卡片](render-a-card.md)以進行後續步驟!

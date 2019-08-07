---
title: 調適型卡片的 JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 07/26/2019
ms.topic: article
ms.openlocfilehash: 4ddff841ec073c60a8aa6184f309e94052cb002d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732550"
---
# <a name="javascript-sdk-for-creating-cards"></a>建立卡片的 JavaScript SDK

> [!IMPORTANT]
> 序列化 JSON 的程式庫仍在開發中, 而您的 milage 可能會有所不同。

如我們在[消費者入門](../../authoring-cards/getting-started.md)中所述, 調適型卡片只是卡片物件模型的序列化 JSON 物件。  為了讓操作物件模型變得更容易, 我們定義了一些程式庫, 定義了可輕鬆序列化/還原序列化 json 的強型別類別階層。

您可以使用任何您想要建立調適型卡片 json 的工具。

`adaptivecards` Npm 套件會定義可在 javascript 中使用調適型卡片的程式庫

## <a name="to-install"></a>安裝
```console
npm install adaptivecards
```

## <a name="example"></a>範例

下列 API 顯示如何使用物件模型來建立調適型卡片, 並將其序列化為 JSON。

```typescript
let card = new Adaptive.AdaptiveCard();
card.version = new Adaptive.Version(1, 0);

let textBlock = new Adaptive.TextBlock();
textBlock.text = "Hello World";

card.addItem(textBlock);

let json = card.toJSON();
```

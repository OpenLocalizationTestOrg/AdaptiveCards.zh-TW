---
title: 擴充性-iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 13245ced3f4f657e13793bfdf1d212e44d2b6a41
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732945"
---
# <a name="extensibility---ios"></a><span data-ttu-id="ae784-102">擴充性-iOS</span><span class="sxs-lookup"><span data-stu-id="ae784-102">Extensibility - iOS</span></span>

## <a name="changing-per-element-rendering"></a><span data-ttu-id="ae784-103">變更每個元素轉譯</span><span class="sxs-lookup"><span data-stu-id="ae784-103">Changing per element rendering</span></span>

<span data-ttu-id="ae784-104">開發人員可以自訂 renderred AdaptiveCards 元素 (例如 TextBlock) 的外觀。</span><span class="sxs-lookup"><span data-stu-id="ae784-104">Developers can customize the look of renderred AdaptiveCards elements such as TextBlock.</span></span>
<span data-ttu-id="ae784-105">下列範例顯示如何變更 NumberInput 的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="ae784-105">Following example shows how one can change background color of NumberInput.</span></span>

```objective-c
ACRRegistration *registration = [ACRRegistration getInstance];
// register custom renderer with registration
// custom renderer must implement ACRIBaseCardElementRenderer protocol
// for more information, please refer to CustomInputNumberRenderer.mm
 [registration setBaseCardElementRenderer:[CustomInputNumberRenderer getInstance] cardElementType:ACRNumberInput];
 ...
/// CustiomInputNumberRenderer.mm
- (UIView *)render:(UIView<ACRIContentHoldingView> *)viewGroup
              rootViewController:(UIViewController *)vc
              inputs:(NSArray *)inputs
     baseCardElement:(ACOBaseCardElement *)acoElem
          hostConfig:(ACOHostConfig *)acoConfig
  {
      ACRInputNumberRenderer *defaultRenderer = [ACRInputNumberRenderer getInstance];
 
      UIView *input = [defaultRenderer render:viewGroup
                           rootViewController:vc
                                       inputs:inputs
                              baseCardElement:acoElem
                                   hostConfig:acoConfig];
      if(input)
      {   
          // customize background color of input
          [input setBackgroundColor: [UIColor colorWithRed:1.0
                                                     green:59.0/255.0
                                                      blue:48.0/255.0
                                                     alpha:1.0]];
      }
      return input;
  }
  ```

 ## <a name="additional-property"></a><span data-ttu-id="ae784-106">其他屬性</span><span class="sxs-lookup"><span data-stu-id="ae784-106">Additional Property</span></span>

 <span data-ttu-id="ae784-107">開發人員也可以將其他屬性當做 json 承載的一部分傳送。</span><span class="sxs-lookup"><span data-stu-id="ae784-107">Developers can also send in additional properties as part of json payload.</span></span>
<span data-ttu-id="ae784-108">例如, 除了 BaseCardElement 的 json 承載的「間距」和「識別碼」, 可以將 TextBlock 角落的半徑新增至其 json 承載。</span><span class="sxs-lookup"><span data-stu-id="ae784-108">For example, in addition to "spacing" and "id" of json payload for BaseCardElement, one can add radius for corners of TextBlock to its json payload.</span></span>

 ```objective-c
 "type":"TextBlock",
 ...
 "radius":20,
 ...
 ```

 ```objective-c
         NSData *additionalProperty = [acoElem additionalProperty];
          if(additionalProperty) {
              NSDictionary *dictionary = [NSJSONSerialization JSONObjectWithData:additionalProperty options:NSJSONReadingMutableLeaves error:nil];
              radiusForMyTextBlock = dictionary[@"radius"];
          ...
```
 ## <a name="custom-parsing"></a><span data-ttu-id="ae784-109">自訂剖析</span><span class="sxs-lookup"><span data-stu-id="ae784-109">Custom Parsing</span></span>

<span data-ttu-id="ae784-110">開發人員也可以進行自訂剖析, 並將新的 UI 元素新增至 adpative 卡, 例如進度列。</span><span class="sxs-lookup"><span data-stu-id="ae784-110">Developers can also have custom parsing and have new UI element added to adpative card such as progress bar.</span></span> <span data-ttu-id="ae784-111">請檢查 CustomProgressBarRenderer.mm 以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ae784-111">Please check CustomProgressBarRenderer.mm for detail.</span></span>
<span data-ttu-id="ae784-112">自訂剖析器必須執行 ACOIBaseCardElementParser 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="ae784-112">Custom parser must implement ACOIBaseCardElementParser protocol.</span></span> <span data-ttu-id="ae784-113">deserializeToCustomElement 方法應該會剖析指定為以外 nsdata 的指定 json 承載, 並傳回 UIView 物件的指標, 以加入 AdaptiveCard 轉譯的物件。</span><span class="sxs-lookup"><span data-stu-id="ae784-113">deserializeToCustomElement method should parses given json payload given as NSData and return a pointer to UIView object that will be added to AdaptiveCard rendered object.</span></span>

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c
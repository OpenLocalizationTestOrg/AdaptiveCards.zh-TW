---
title: 呈現卡片-iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: d47b94595c22afa51a0d4cf9666771203cd79c7e
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732920"
---
# <a name="render-a-card---ios"></a>呈現卡片-iOS

以下說明如何使用 iOS SDK 呈現卡片。

## <a name="create-a-card-from-a-json-string"></a>從 JSON 字串建立卡片

AdaptiveCard 是從 JSON 字串產生

```objective-c

NSString *jsonStr = @"{ \"type\": \"AdaptiveCard\", \"version\": \"1.0\", \"body\": [ { \"type\": \"Image\", \"url\": \"http://adaptivecards.io/content/adaptive-card-50.png\", \"horizontalAlignment\":\"center\" }, { \"type\": \"TextBlock\", \"horizontalAlignment\":\"center\", \"text\": \"Hello **Adaptive Cards!**\" } ], \"actions\": [ { \"type\": \"Action.OpenUrl\", \"title\": \"Learn more\", \"url\": \"http://adaptivecards.io\" }, { \"type\": \"Action.OpenUrl\", \"title\": \"GitHub\", \"url\": \"http://github.com/Microsoft/AdaptiveCards\" } ] }";
ACOAdaptiveCardParseResult *cardParseResult = [ACOAdaptiveCard fromJson:jsonStr];

/// access for parse warnings and errors
NSArray<NSError *> errors = cardParseResult.parseErrors;
NSArray<ACRParseWarning *> warnings = cardPraseResult.parseWarnings;
```

## <a name="render-a-card"></a>呈現卡片

Rederer 會使用調適型卡片和主機設定。HostConfig 可以是 nil, 如果是 nil, 則會使用預設值。
傳回的 UIView 會使用自動版式。 寬度會限制為 widthConstraint 所設定的值。 如果使用0值, 則不會系結。
Height 不會系結, 而當傳回時, 其高度會呈現所有內容的總和。 若要系結視圖維度, 請使用 NSLayoutConstraint。 如果使用 ACRViewController, 則可以從其 superview 頂端的 viewcontroller 的 viewDidLayoutSubview 內容或它的方法, 以相同的名稱存取確切的維度。

```objective-c
ACRRenderResult *renderResult;
if(cardParseResult.isValid){
    renderResult = [ACRRenderer render:cardParseResult.card config:nil widthConstraint:335];
}
``` 
### <a name="example"></a>範例

```objective-c
--------------------------------------------------------------------------------
ViewController.m
--------------------------------------------------------------------------------
#import "ViewController.h"
#import <SafariServices/SafariServices.h>

@interface ViewController ()

@end

@implementation ViewController

- (void)viewDidLoad {
    [super viewDidLoad];

    NSString *jsonStr = @"{ \"type\": \"AdaptiveCard\", \"version\": \"1.0\", \"body\": [ { \"type\": \"Image\", \"url\": \"http://adaptivecards.io/content/adaptive-card-50.png\", \"horizontalAlignment\":\"center\" }, { \"type\": \"TextBlock\", \"horizontalAlignment\":\"center\", \"text\": \"Hello **Adaptive Cards!**\" } ], \"actions\": [ { \"type\": \"Action.OpenUrl\", \"title\": \"Learn more\", \"url\": \"http://adaptivecards.io\" }, { \"type\": \"Action.OpenUrl\", \"title\": \"GitHub\", \"url\": \"http://github.com/Microsoft/AdaptiveCards\" } ] }";
    ACRRenderResult *renderResult;
    ACOAdaptiveCardParseResult *cardParseResult = [ACOAdaptiveCard fromJson:jsonStr];
    if(cardParseResult.isValid){
        renderResult = [ACRRenderer render:cardParseResult.card config:nil widthConstraint:335];
    }

    if(renderResult.succeeded)
    {
        ACRView *ad = renderResult.view;
        ad.acrActionDelegate = self;
        
        UIView *view = self.view;
        view.autoresizingMask |= UIViewAutoresizingFlexibleHeight;
        [self.view addSubview:ad];
        ad.translatesAutoresizingMaskIntoConstraints = NO;
        
        [NSLayoutConstraint constraintWithItem:ad attribute:NSLayoutAttributeCenterX relatedBy:NSLayoutRelationEqual toItem:view attribute:NSLayoutAttributeCenterX multiplier:1.0 constant:0].active = YES;

        [NSLayoutConstraint constraintWithItem:ad attribute:NSLayoutAttributeCenterY relatedBy:NSLayoutRelationEqual toItem:view attribute:NSLayoutAttributeCenterY multiplier:1.0 constant:3].active = YES;
    }
}

- (void)didFetchUserResponses:(ACOAdaptiveCard *)card action:(ACOBaseActionElement *)action
{
    if(action.type == ACROpenUrl){
        NSURL *url = [NSURL URLWithString:[action url]];
        SFSafariViewController *svc = [[SFSafariViewController alloc] initWithURL:url];
        [self presentViewController:svc animated:YES completion:nil];
    }
}

@end

```

```swift
--------------------------------------------------------------------------------
ViewController.swft
--------------------------------------------------------------------------------

import UIKit
import SafariServices

class ViewController: UIViewController, ACRActionDelegate {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
        let jsonStr = "{ \"type\": \"AdaptiveCard\", \"version\": \"1.0\", \"body\": [ { \"type\": \"Image\", \"url\": \"http://adaptivecards.io/content/adaptive-card-50.png\", \"horizontalAlignment\":\"center\" }, { \"type\": \"TextBlock\", \"horizontalAlignment\":\"center\", \"text\": \"Hello **Adaptive Cards!**\" } ], \"actions\": [ { \"type\": \"Action.OpenUrl\", \"title\": \"Learn more\", \"url\": \"http://adaptivecards.io\" }, { \"type\": \"Action.OpenUrl\", \"title\": \"GitHub\", \"url\": \"http://github.com/Microsoft/AdaptiveCards\" } ] }";

        let cardParseResult = ACOAdaptiveCard.fromJson(jsonStr);
        if((cardParseResult?.isValid)!){
            let renderResult = ACRRenderer.render(cardParseResult!.card, config: nil, widthConstraint: 335);

            if(renderResult?.succeeded ?? false)
            {
                let ad = renderResult?.view;
                ad!.acrActionDelegate = (self as ACRActionDelegate);
                self.view.autoresizingMask = [.flexibleHeight];
                self.view.addSubview(ad!);
                ad!.translatesAutoresizingMaskIntoConstraints = false;
    
                NSLayoutConstraint(item: ad!, attribute: .centerX, relatedBy: .equal, toItem: view, attribute: .centerX, multiplier: 1.0, constant: 0).isActive = true;
                NSLayoutConstraint(item: ad!, attribute: .centerY, relatedBy: .equal, toItem: view, attribute: .centerY, multiplier: 1.0, constant: 3).isActive = true;
            }
        }
    }

    func didFetchUserResponses(_ card: ACOAdaptiveCard, action: ACOBaseActionElement)
    {
        if(action.type == ACRActionType.openUrl){
            let url = URL.init(string:action.url());
            let svc = SFSafariViewController.init(url: url!);
            self.present(svc, animated: true, completion: nil);
        }
    }

}
```

---
title: 調適型卡片的 HostConfig
author: paulcam206
ms.author: paulcam
ms.date: 09/18/2018
ms.topic: reference
ms.openlocfilehash: 848ce3dd2ccca1f975dfd330c1c88292c753641d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733095"
---
# <a name="what-is-hostconfig"></a>什麼是 HostConfig？
`HostConfig`是一種**跨平臺設定物件**, 可指定調適型卡片轉譯器如何產生 UI。

這可讓平臺不可知的屬性在不同平臺和裝置上的轉譯器之間共用。 它也允許建立工具, 讓您瞭解介面卡對指定環境的外觀與風格。

請參閱[HostConfig](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json)範例, 以瞭解其內容。

---

   * [`AdaptiveCardConfig`](#schema-adaptivecardconfig)-Toplevel 選項`AdaptiveCards`
   * [`ActionsConfig`](#schema-actionsconfig)-的`Action`選項
   * [`ContainerStylesConfig`](#schema-containerstylesconfig)-控制項預設和強調容器的樣式
   * [`FactSetConfig`](#schema-factsetconfig)-控制`FactSet`s 的顯示
   * [`FontSizesConfig`](#schema-fontsizesconfig)-控制不同文字樣式的字型大小度量
   * [`FontWeightsConfig`](#schema-fontweightsconfig)-控制字型粗細計量
   * [`ForegroundColorsConfig`](#schema-foregroundcolorsconfig)-控制各種字型色彩
   * [`ImageSetConfig`](#schema-imagesetconfig)-控制如何`ImageSet`顯示 s
   * [`ImageSizesConfig`](#schema-imagesizesconfig)-控制項`Image`大小
   * [`MediaConfig`](#schema-mediaconfig)-控制`Media`元素的顯示和行為
   * [`SeparatorConfig`](#schema-separatorconfig)-控制分隔符號的顯示方式
   * [`ShowCardConfig`](#schema-showcardconfig)-控制的行為和樣式`Action.ShowCard`
   * [`SpacingsConfig`](#schema-spacingsconfig)-控制元素的配置方式
   * [`TextBlockConfig`](#schema-textblockconfig)-控制文字顯示的參數

# <a name="card-configuration"></a>卡片設定

<a name="schema-adaptivecardconfig"></a>
## <a name="adaptivecardconfig"></a>AdaptiveCardConfig

的 Toplevel 選項`AdaptiveCards`

|屬性|類型|必要|說明|版本|
|--------|----|--------|-----------|-------|
|**allowCustomStyle**|`boolean`| 否, 預設值:`true`|控制是否允許自訂樣式|1.0
|**supportsInteractivity**|`boolean`| 否, 預設值:`true`|控制是否允許`Action`叫用互動式 s|1.0
|**imageBaseUrl**|`string`| 否|載入資源時要使用的基底 URL|1.0
|**fontFamily**|`string`| 否, 預設值:`"Calibri"`|呈現文字時要使用的字型|1.0
|**actions**|`object`| 否|S 的`Action`選項|1.0
|**adaptiveCard**|`object`| 否|的 Toplevel 選項`AdaptiveCards`|1.0
|**containerStyles**|`object`| 否|控制項預設和強調容器的樣式|1.0
|**imageSizes**|`object`| 否|控制項`Image`大小|1.0
|**imageSet**|`object`| 否|控制如何`ImageSet`顯示 s|1.0
|**factSet**|`object`| 否|控制`FactSet`s 的顯示|1.0
|**fontSizes**|`object`| 否|控制不同文字樣式的字型大小度量|1.0
|**fontWeights**|`object`| 否|控制字型粗細計量|1.0
|**spacing**|`object`| 否|控制元素的配置方式|1.0
|**separator**|`object`| 否|控制分隔符號的顯示方式|1.0
|**media**|`object`| 否|控制`Media`元素的顯示和行為|1.1


<a name="schema-actionsconfig"></a>
## <a name="actionsconfig"></a>ActionsConfig

S 的`Action`選項

|屬性|類型|必要|描述|版本|
|--------|----|--------|-----------|-------|
|**actionsOrientation**|`string`| 否, 預設值:`"horizontal"`|控制按鈕的配置方式|1.0
|**actionAlignment**|`string`| 否, 預設值:`"stretch"`|按鈕的控制項版面配置|1.0
|**buttonSpacing**|`integer`| 否, 預設值:`10`|控制按鈕之間要使用多少間距|1.0
|**maxActions**|`integer`| 否, 預設值:`5`|控制總共允許多少個動作|1.0
|**spacing**|`string`| 否, 預設值:`"default"`|控制 action 元素的整體間距|1.0
|**showCard**|`object`| 否|控制的行為和樣式`Action.ShowCard`|1.0
|**iconPlacement**|`string`| 否, 預設值:`"aboveTitle"`|控制要放置動作圖示的位置|1.0
|**iconSize**|`integer`| 否, 預設值:`30`|控制動作圖示的大小|1.0


<a name="schema-containerstylesconfig"></a>
## <a name="containerstylesconfig"></a>ContainerStylesConfig

控制項預設和強調容器的樣式

|屬性|類型|必要|描述|版本|
|--------|----|--------|-----------|-------|
|**default**|`object`| 否|預設容器樣式|1.0
|**emphasis**|`object`| 否|用於強調的容器樣式|1.0


<a name="schema-factsetconfig"></a>
## <a name="factsetconfig"></a>FactSetConfig

控制`FactSet`s 的顯示

|屬性|類型|必要|說明|版本|
|--------|----|--------|-----------|-------|
|**標題**|`object`| 否, 預設值:`{"weight":"bolder","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":150}`|控制文字顯示的參數|1.0
|**value**|`object`| 否, 預設值:`{"weight":"default","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":0}`|控制文字顯示的參數|1.0
|**spacing**|`integer`| 否, 預設值:`10`|&nbsp;|1.0


<a name="schema-fontsizesconfig"></a>
## <a name="fontsizesconfig"></a>FontSizesConfig

控制不同文字樣式的字型大小度量

|屬性|類型|必要|說明|版本|
|--------|----|--------|-----------|-------|
|**small**|`integer`| 否, 預設值:`10`|小字型大小|1.0
|**default**|`integer`| 否, 預設值:`12`|預設字型大小|1.0
|**medium**|`integer`| 否, 預設值:`14`|中字型大小|1.0
|**large**|`integer`| 否, 預設值:`17`|大字型大小|1.0
|**extraLarge**|`integer`| 否, 預設值:`20`|超大型字型大小|1.0


<a name="schema-fontweightsconfig"></a>
## <a name="fontweightsconfig"></a>FontWeightsConfig

控制字型粗細計量

|屬性|類型|必要|說明|版本|
|--------|----|--------|-----------|-------|
|**lighter**|`integer`| 否, 預設值:`200`|&nbsp;|1.0
|**default**|`integer`| 否, 預設值:`400`|&nbsp;|1.0
|**bolder**|`integer`| 否, 預設值:`800`|&nbsp;|1.0


<a name="schema-foregroundcolorsconfig"></a>
## <a name="foregroundcolorsconfig"></a>ForegroundColorsConfig

控制各種字型色彩

|屬性|類型|必要|說明|版本|
|--------|----|--------|-----------|-------|
|**default**|`object`| 否, 預設值:`{"default":"#FF000000","subtle":"#B2000000"}`|&nbsp;|1.0
|**accent**|`object`| 否, 預設值:`{"default":"#FF0000FF","subtle":"#B20000FF"}`|&nbsp;|1.0
|**dark**|`object`| 否, 預設值:`{"default":"#FF101010","subtle":"#B2101010"}`|&nbsp;|1.0
|**light**|`object`| 否, 預設值:`{"default":"#FFFFFFFF","subtle":"#B2FFFFFF"}`|&nbsp;|1.0
|**good**|`object`| 否, 預設值:`{"default":"#FF008000","subtle":"#B2008000"}`|&nbsp;|1.0
|**warning**|`object`| 否, 預設值:`{"default":"#FFFFD700","subtle":"#B2FFD700"}`|&nbsp;|1.0
|**attention**|`object`| 否, 預設值:`{"default":"#FF8B0000","subtle":"#B28B0000"}`|&nbsp;|1.0


<a name="schema-imagesetconfig"></a>
## <a name="imagesetconfig"></a>ImageSetConfig

控制如何`ImageSet`顯示 s

|屬性|類型|必要|描述|版本|
|--------|----|--------|-----------|-------|
|**imageSize**|`string`| 否, 預設值:`"auto"`|控制個別影像大小|1.0
|**maxImageHeight**|`integer`| 否, 預設值:`100`|將影像高度限制為這個值|1.0


<a name="schema-imagesizesconfig"></a>
## <a name="imagesizesconfig"></a>ImageSizesConfig

控制項`Image`大小

|屬性|類型|必要|描述|版本|
|--------|----|--------|-----------|-------|
|**small**|`integer`| 否, 預設值:`80`|小型影像大小值|1.0
|**medium**|`integer`| 否, 預設值:`120`|中影像大小值|1.0
|**large**|`integer`| 否, 預設值:`180`|大型影像大小值|1.0


<a name="schema-mediaconfig"></a>
## <a name="mediaconfig"></a>MediaConfig

控制`Media`元素的顯示和行為

#### <a name="introduced-in-version-11"></a>1.1 版中引進

|屬性|類型|必要|描述|版本|
|--------|----|--------|-----------|-------|
|**defaultPoster**|`string`| 否|未叫用 [播放] 按鈕時要顯示之影像的 URI|1.1
|**playButton**|`string`| 否|要顯示為播放按鈕的影像|1.1
|**allowInlinePlayback**|`boolean`| 否, 預設值:`true`|是否要顯示內嵌媒體或在外部叫用|1.1


<a name="schema-separatorconfig"></a>
## <a name="separatorconfig"></a>SeparatorConfig

控制分隔符號的顯示方式

|屬性|類型|必要|說明|版本|
|--------|----|--------|-----------|-------|
|**lineThickness**|`integer`| 否, 預設值:`1`|分隔線的粗細|1.0
|**lineColor**|`string,null`| 否, 預設值:`#B2000000`|繪製分隔線時要使用的色彩|1.0


<a name="schema-showcardconfig"></a>
## <a name="showcardconfig"></a>ShowCardConfig

控制的行為和樣式`Action.ShowCard`

|屬性|類型|必要|說明|版本|
|--------|----|--------|-----------|-------|
|**actionMode**|`string`| 否, 預設值:`"inline"`|控制卡片的顯示方式|1.0
|**style**|`object`| 否, 預設值:`emphasis`|控制容器的樣式|1.0
|**inlineTopMargin**|`integer`| 否, 預設值:`16`|顯示卡片時要使用的邊界數量|1.0


<a name="schema-spacingsconfig"></a>
## <a name="spacingsconfig"></a>SpacingsConfig

控制元素的配置方式

|屬性|類型|必要|描述|版本|
|--------|----|--------|-----------|-------|
|**small**|`integer`| 否, 預設值:`3`|小間距值|1.0
|**default**|`integer`| 否, 預設值:`8`|預設間距值|1.0
|**medium**|`integer`| 否, 預設值:`20`|中間距值|1.0
|**large**|`integer`| 否, 預設值:`30`|大間距值|1.0
|**extraLarge**|`integer`| 否, 預設值:`40`|多餘的大間距值|1.0
|**padding**|`integer`| 否, 預設值:`20`|填補值|1.0


<a name="schema-textblockconfig"></a>
## <a name="textblockconfig"></a>TextBlockConfig

控制文字顯示的參數

|屬性|類型|必要|說明|版本|
|--------|----|--------|-----------|-------|
|**size**|`string`| 否, 預設值:`"default"`|卡片未指定時要使用的字型大小|1.0
|**weight**|`string`| 否, 預設值:`"normal"`|卡片未指定時要使用的字型粗細|1.0
|**color**|`string`| 否, 預設值:`"default"`|卡片未指定時要使用的字型色彩|1.0
|**isSubtle**|`boolean`| 否, 預設值:`false`|如果卡片未指定, 應該將文字細微|1.0
|**wrap**|`boolean`| 否, 預設值:`true`|如果卡片未指定, 應該將文字換行|1.0
|**maxWidth**|`integer`| 否, 預設值:`0`|卡片未指定時要使用的最大寬度|1.0

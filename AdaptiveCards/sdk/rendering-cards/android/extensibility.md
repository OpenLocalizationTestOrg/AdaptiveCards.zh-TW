---
title: Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: e565606f4a112d4f1fa08e2989f392f1abf0887f
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732535"
---
# <a name="extensibility---android"></a>擴充性-Android

Android 轉譯器可以擴充以支援多個案例, 包括:
* [卡片元素的自訂剖析](#custom-parsing-of-card-elements)
* [卡片元素的自訂呈現](#custom-rendering-of-card-elements)
* [動作的自訂](#custom-rendering-of-actions)轉譯(自1.2 版開始)
* [自訂映射載入](#custom-image-loading)(自 v 1.0.1 起)
* [自訂媒體載入](#custom-media-loading)(從 v1.1 開始)

## <a name="custom-parsing-of-card-elements"></a>卡片元素的自訂剖析

您可以擴充剖析器, 以支援您已定義的卡片元素。 例如, 假設我們有一個新的元素型別, 如下所示:
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

然後, 下列程式程式碼會示範如何將它剖析成從 BaseCardElement 擴充的 CardElement:
```java
public class MyCustomCardElement extends BaseCardElement
{

    public MyCustomCardElement(CardElementType type) {
        super(type);
    }

    public String getMyTypeData()
    {
        return myTypeData;
    }

    public void setMyTypeData(String data)
    {
        myTypeData = data;
    }

    private String myTypeData;
}

public class MyCardElementParser extends BaseCardElementParser
{
    @Override
    public BaseCardElement Deserialize(ElementParserRegistration elementParserRegistration, ActionParserRegistration actionParserRegistration, JsonValue value)
    {
        MyCustomCardElement element = new CustomCardElement(CardElementType.Custom);
        element.SetElementTypeString("MyType");
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setMyTypeData(obj.getString("secret"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setMyTypeData("Failed");
        }
        return element;
    }
}
```

這就是如何註冊剖析器, 並取得包含自訂元素的 AdaptiveCard 物件:
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

下一步是呈現自訂元素

## <a name="custom-rendering-of-card-elements"></a>卡片元素的自訂呈現

> [!IMPORTANT]
>
> **重大變更的清單**
>
> [1.2 版的重大變更](#breaking-changes-for-v12)

若要為型別定義自己的自訂轉譯器, 我們必須先建立一個可```BaseCardElementRenderer```延伸的類別:
```java
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(Context context, FragmentManager fragmentManager, ViewGroup viewGroup, BaseCardElement baseCardElement, Vector<IInputHandler> inputActionHandlerList, ICardActionHandler cardActionHandler, HostConfig hostConfig, ContainerStyle containerStyle) {

        //Call findImplObj on baseCardElement to get the instance we returned at parse. We can then cast that object to our type
        CustomCardElement element = (CustomCardElement) baseCardElement.findImplObj();

        //Create some view and add it to the view group
        TextView textView = new TextView(context);
        textView.setText(element.getMyTypeData());
        textView.setAllCaps(true);
        viewGroup.addView(textView);

        //return the view
        return textView;
    }
}
```

然後, 我們會註冊此轉譯器, 如下所示:
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler,  hostConfig);
```

### <a name="breaking-changes-for-v12"></a>1.2 版的重大變更

方法已變更為```RenderedAdaptiveCard```包含參數, 而且```ContainerStyle```已針對現在包含 ContainerStyle 的 RenderArgs 變更, 因此擴充 BaseCardElementRenderer 的類別看起來應該像這樣```render```

```
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(RenderedAdaptiveCard renderedAdaptiveCard, Context context, FragmentManager fragmentManager, ViewGroup viewGroup,
                       BaseCardElement baseCardElement, ICardActionHandler cardActionHandler, HostConfig hostConfig, RenderArgs renderArgs)
    { }
}
```

## <a name="custom-parsing-of-card-actions"></a>自訂介面卡動作的剖析

類似于剖析1.2 版中的自訂卡片元素, 已引進剖析自訂動作的可能性。 例如, 假設我們有一個新的動作型別, 如下所示:
```json
{
    "type" : "MyAction",
    "ActionData" : "My data"
}
```

然後, 下列程式程式碼會示範如何將它剖析成從延伸的```BaseActionElement```ActionElement:
```java
public class MyActionElement extends BaseActionElement
{
    public MyActionElement(ActionType type) 
    {
        super(type);
    }

    public String getActionData()
    {
        return mActionData;
    }

    public void setActionData(String s)
    {
        mActionData = s;
    }

    private String mActionData;
    public static final String MyActionId = "myAction";
}

public class MyActionParser extends ActionElementParser
{
    @Override
    public BaseActionElement Deserialize(ParseContext context, JsonValue value)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setActionData(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setActionData("Failure");
        }
        return element;
    }

    @Override
    public BaseActionElement DeserializeFromString(ParseContext context, String jsonString)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        try {
            JSONObject obj = new JSONObject(jsonString);
            element.setBackwardString(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setBackwardString("Failure");
        }
        return element;
    }
}
```

接下來的幾行示範如何註冊剖析器, 並取得包含自訂 action 元素的 AdaptiveCard 物件:
```java
// Create an ActionParserRegistration and add your parser to it
ActionParserRegistration actionParserRegistration = new ActionParserRegistration();
actionParserRegistration.AddParser(MyActionElement.MyActionId, new MyActionParser());

ParseContext context = new ParseContext(null, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

下一步是呈現自訂動作

## <a name="custom-rendering-of-actions"></a>動作的自訂轉譯

若要為類型定義自己的自訂動作轉譯器, 我們必須先建立可從```BaseActionElementRenderer```下列範圍擴充的類別:
```java
public class MyActionRenderer extends BaseActionElementRenderer
{
    @Override
    public Button render(RenderedAdaptiveCard renderedCard,
                         Context context,
                         FragmentManager fragmentManager,
                         ViewGroup viewGroup,
                         BaseActionElement baseActionElement,
                         ICardActionHandler cardActionHandler,
                         HostConfig hostConfig,
                         RenderArgs renderArgs)
    {
        Button myActionButton = new Button(context);

        CustomActionElement customAction = (CustomActionElement) baseActionElement.findImplObj();

        myActionButton.setBackgroundColor(getResources().getColor(R.color.greenActionColor));
        myActionButton.setText(customAction.getMessage());
        myActionButton.setAllCaps(false);
        myActionButton.setOnClickListener(new BaseActionElementRenderer.ActionOnClickListener(renderedCard, baseActionElement, cardActionHandler));

        viewGroup.addView(myActionButton);

        return myActionButton;
    }
}
```

然後, 我們會註冊此轉譯器, 如下所示:
```java
CardRendererRegistration.getInstance().registerActionRenderer("myAction", new CustomActionRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
```

## <a name="custom-rendering-of-actions"></a>動作的自訂轉譯

[!IMPORTANT]
> 對自訂動作呈現的變更已針對 v5.2 進行規劃, 但尚未完成

## <a name="custom-image-loading"></a>自訂映射載入

### <a name="ionlineimageloader"></a>IOnlineImageLoader

> [!IMPORTANT]
> **只有一個 IOnlineImageLoader 可以註冊, 而且優先于抓取影像的預設方式**

為了讓開發人員能夠取得無法直接從線上來源下載或抓取的影像, 或在抓取之前需要先前的步驟, 已新增 IOnlineImageLoader 來解決這種情況。 若要執行 OnlineImageLoader, 您必須只執行方法 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

以下是 OnlineImageLoader 的範例, 其會變更 cat 映射的所有影像

```java
public class OnlineImageLoader implements IOnlineImageLoader
{
    public OnlineImageLoader(){}

    @Override
    public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
    {
        String catImnageUri = "http://adaptivecards.io/content/cats/1.png";
        byte[] bytes = HttpRequestHelper.get(catImnageUri);
        if (bytes == null)
        {
            throw new IOException("Failed to retrieve content from " + catImnageUri);
        }

        Bitmap bitmap = BitmapFactory.decodeByteArray(bytes, 0, bytes.length);

        if (bitmap == null)
        {
            throw new IOException("Failed to convert content to bitmap: " + new String(bytes));
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

最後, 若要註冊此映射載入器, 您必須只將這一行新增至您的程式碼。

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a>IResourceResolver (deprecates IOnlineImageLoader)

針對1.2 版, 已將完整 ResourceResolvers 的支援新增至 android 轉譯器。 資源解析程式的執行與 IOnlineImageLoader 的方式非常類似, 但擁有 ResourceResolvers 可讓開發人員新增多種方法, 從單一卡片中的任何一種來源取得影像, 這是藉由連結每個 ResourceResolver 來完成。在嘗試抓取影像時, 將會查詢的唯一前置詞。 

您可以執行類似下列的 ResourceResolver

```java
public class ResourceResolver implements IResourceResolver
{
    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);
        byte[] decodedByteArray = Util.getBytes(decodedDataUri);
        bitmap = BitmapFactory.decodeByteArray(decodedByteArray, 0, decodedByteArray.length);

        return new HttpRequestResult<>(bitmap);
    }

    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);

        if (uri.startsWith("data:image/svg")) {
            String svgString = AdaptiveBase64Util.ExtractDataFromUri(uri);
            String decodedSvgString = URLDecoder.decode(svgString, "UTF-8");
            Sharp sharp = Sharp.loadString(decodedSvgString);
            Drawable drawable = sharp.getDrawable();
            bitmap = ImageUtil.drawableToBitmap(drawable, maxWidth);
        }
        else
        {
            try
            {
                return genericImageLoaderAsync.loadDataUriImage(uri);
            }
            catch (Exception e)
            {
                return new HttpRequestResult<>(e);
            }
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

如先前所述, 您可以註冊多個 ResourceResolvers, 以註冊 ResourceResolver, 您可以執行此動作

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a>將 IOnlineImageLoader 轉換成 IResourceResolver 

將 IOnlineImageLoader 轉換成 IResourceResolver 是相當簡單的工作, 因為後者的方法嘗試盡可能與 IOnlineImageLoader 保持相似

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

如您所見, 最大的變更為

* ```loadOnlineImage(String, GenericImageLoaderAsync)```已重新命名為```resolveImageResource(String, GenericImageLoaderAsync)```
* 已將的多載新增```resolveImageResource(String, GenericImageLoaderAsync, int)```為, 以支援需要最大寬度的案例```resolveImageResource(String, GenericImageLoaderAsync)```

## <a name="custom-media-loading"></a>自訂媒體載入

> [!IMPORTANT]
> **請```IOnlineMediaLoader```記住```MediaDataSource``` , 您必須在 API 層級23或 Android M 中新增此功能**

除了包含 media 元素之外, 也包含 IOnlineMediaLoader 介面, 可讓開發人員覆寫用於基礎 mediaPlayer 元素的[MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) 。 **(需要 android M)**

第一個需要做的事, 就是建立一個可執行 IOnlineImageLoader 的類別

```java
@RequiresApi(api = Build.VERSION_CODES.M)
public class OnlineMediaLoader implements IOnlineMediaLoader
{
    /* This class checks if the media source exists */
    public class OnlineFileAvailableChecker extends AsyncTask<String, Void, Boolean>
    {
        public OnlineFileAvailableChecker(String uri)
        {
            m_uri = uri;
        }

        @Override
        protected Boolean doInBackground(String... strings) {
            // if the provided uri is a valid uri or is valid with the resource resolver, then use that
            // otherwise, try to get the media from a local file
            try
            {
                HttpRequestHelper.query(m_uri);
                return true;
            }
            catch (Exception e)
            {
                // Do nothing if the media was not found at all
                e.printStackTrace();
                return false;
            }
        }

        private String m_uri;
   }

       
   @Override
   public MediaDataSource loadOnlineMedia(MediaSourceVector mediaSources, IMediaDataSourceOnPreparedListener mediaDataSourceOnPreparedListener)
   {
       final long mediaSourcesSize = mediaSources.size();
       for(int i = 0; i < mediaSourcesSize; i++)
       {
           String mediaUri = mediaSources.get(i).GetUrl();

           OnlineFileAvailableChecker checker = new OnlineFileAvailableChecker(mediaUri);
           try
           {
               Boolean fileExists = checker.execute("").get();
               if(fileExists)
               {
                   return new MediaDataSourceImpl(mediaUri, mediaDataSourceOnPreparedListener);
               }
           }
           catch (Exception e) { }
       }
       return null;
    }
}
```

一旦執行此類別, 您就可以藉由新增來註冊 OnlineMediaLoader 類別 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```

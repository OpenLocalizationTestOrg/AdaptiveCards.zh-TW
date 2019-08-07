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
# <a name="extensibility---android"></a><span data-ttu-id="5b878-102">擴充性-Android</span><span class="sxs-lookup"><span data-stu-id="5b878-102">Extensibility - Android</span></span>

<span data-ttu-id="5b878-103">Android 轉譯器可以擴充以支援多個案例, 包括:</span><span class="sxs-lookup"><span data-stu-id="5b878-103">The Android renderer can be extended to support multiple scenarios including:</span></span>
* [<span data-ttu-id="5b878-104">卡片元素的自訂剖析</span><span class="sxs-lookup"><span data-stu-id="5b878-104">Custom Parsing of Card Elements</span></span>](#custom-parsing-of-card-elements)
* [<span data-ttu-id="5b878-105">卡片元素的自訂呈現</span><span class="sxs-lookup"><span data-stu-id="5b878-105">Custom Rendering of Card Elements</span></span>](#custom-rendering-of-card-elements)
* <span data-ttu-id="5b878-106">[動作的自訂](#custom-rendering-of-actions)轉譯(自1.2 版開始)</span><span class="sxs-lookup"><span data-stu-id="5b878-106">[Custom Rendering of Actions](#custom-rendering-of-actions) (Since v1.2)</span></span>
* <span data-ttu-id="5b878-107">[自訂映射載入](#custom-image-loading)(自 v 1.0.1 起)</span><span class="sxs-lookup"><span data-stu-id="5b878-107">[Custom Image Loading](#custom-image-loading) (Since v1.0.1)</span></span>
* <span data-ttu-id="5b878-108">[自訂媒體載入](#custom-media-loading)(從 v1.1 開始)</span><span class="sxs-lookup"><span data-stu-id="5b878-108">[Custom Media Loading](#custom-media-loading) (Since v1.1)</span></span>

## <a name="custom-parsing-of-card-elements"></a><span data-ttu-id="5b878-109">卡片元素的自訂剖析</span><span class="sxs-lookup"><span data-stu-id="5b878-109">Custom Parsing of Card Elements</span></span>

<span data-ttu-id="5b878-110">您可以擴充剖析器, 以支援您已定義的卡片元素。</span><span class="sxs-lookup"><span data-stu-id="5b878-110">You may extend the parser to support card elements that you have defined.</span></span> <span data-ttu-id="5b878-111">例如, 假設我們有一個新的元素型別, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="5b878-111">For example, say we have a new element type that looks like this:</span></span>
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

<span data-ttu-id="5b878-112">然後, 下列程式程式碼會示範如何將它剖析成從 BaseCardElement 擴充的 CardElement:</span><span class="sxs-lookup"><span data-stu-id="5b878-112">Then the following lines demonstrate how to parse it into a CardElement that extends from the BaseCardElement:</span></span>
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

<span data-ttu-id="5b878-113">這就是如何註冊剖析器, 並取得包含自訂元素的 AdaptiveCard 物件:</span><span class="sxs-lookup"><span data-stu-id="5b878-113">And this is how to register the parser and get an AdaptiveCard object that contains the custom element:</span></span>
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

<span data-ttu-id="5b878-114">下一步是呈現自訂元素</span><span class="sxs-lookup"><span data-stu-id="5b878-114">Next comes rendering the custom element</span></span>

## <a name="custom-rendering-of-card-elements"></a><span data-ttu-id="5b878-115">卡片元素的自訂呈現</span><span class="sxs-lookup"><span data-stu-id="5b878-115">Custom Rendering of Card Elements</span></span>

> [!IMPORTANT]
>
> <span data-ttu-id="5b878-116">**重大變更的清單**</span><span class="sxs-lookup"><span data-stu-id="5b878-116">**List of Breaking Changes**</span></span>
>
> [<span data-ttu-id="5b878-117">1.2 版的重大變更</span><span class="sxs-lookup"><span data-stu-id="5b878-117">Breaking changes for v1.2</span></span>](#breaking-changes-for-v12)

<span data-ttu-id="5b878-118">若要為型別定義自己的自訂轉譯器, 我們必須先建立一個可```BaseCardElementRenderer```延伸的類別:</span><span class="sxs-lookup"><span data-stu-id="5b878-118">To define our own custom renderer for our type, we must first create a class that extends from ```BaseCardElementRenderer```:</span></span>
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

<span data-ttu-id="5b878-119">然後, 我們會註冊此轉譯器, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="5b878-119">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler,  hostConfig);
```

### <a name="breaking-changes-for-v12"></a><span data-ttu-id="5b878-120">1.2 版的重大變更</span><span class="sxs-lookup"><span data-stu-id="5b878-120">Breaking changes for v1.2</span></span>

<span data-ttu-id="5b878-121">方法已變更為```RenderedAdaptiveCard```包含參數, 而且```ContainerStyle```已針對現在包含 ContainerStyle 的 RenderArgs 變更, 因此擴充 BaseCardElementRenderer 的類別看起來應該像這樣```render```</span><span class="sxs-lookup"><span data-stu-id="5b878-121">The ```render``` method was changed to include the ```RenderedAdaptiveCard``` parameter and ```ContainerStyle``` was changed for a RenderArgs where the ContainerStyle is now contained so a class that extends BaseCardElementRenderer should look like this</span></span>

```
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(RenderedAdaptiveCard renderedAdaptiveCard, Context context, FragmentManager fragmentManager, ViewGroup viewGroup,
                       BaseCardElement baseCardElement, ICardActionHandler cardActionHandler, HostConfig hostConfig, RenderArgs renderArgs)
    { }
}
```

## <a name="custom-parsing-of-card-actions"></a><span data-ttu-id="5b878-122">自訂介面卡動作的剖析</span><span class="sxs-lookup"><span data-stu-id="5b878-122">Custom Parsing of Card Actions</span></span>

<span data-ttu-id="5b878-123">類似于剖析1.2 版中的自訂卡片元素, 已引進剖析自訂動作的可能性。</span><span class="sxs-lookup"><span data-stu-id="5b878-123">Similarly to parsing custom card elements in v1.2 the possibility to parse custom actions was introduced.</span></span> <span data-ttu-id="5b878-124">例如, 假設我們有一個新的動作型別, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="5b878-124">For example, say we have a new action type that looks like this:</span></span>
```json
{
    "type" : "MyAction",
    "ActionData" : "My data"
}
```

<span data-ttu-id="5b878-125">然後, 下列程式程式碼會示範如何將它剖析成從延伸的```BaseActionElement```ActionElement:</span><span class="sxs-lookup"><span data-stu-id="5b878-125">Then the following lines demonstrate how to parse it into a ActionElement that extends from the ```BaseActionElement```:</span></span>
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

<span data-ttu-id="5b878-126">接下來的幾行示範如何註冊剖析器, 並取得包含自訂 action 元素的 AdaptiveCard 物件:</span><span class="sxs-lookup"><span data-stu-id="5b878-126">And the next lines demonstrate how to register the parser and get an AdaptiveCard object that contains the custom action element:</span></span>
```java
// Create an ActionParserRegistration and add your parser to it
ActionParserRegistration actionParserRegistration = new ActionParserRegistration();
actionParserRegistration.AddParser(MyActionElement.MyActionId, new MyActionParser());

ParseContext context = new ParseContext(null, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="5b878-127">下一步是呈現自訂動作</span><span class="sxs-lookup"><span data-stu-id="5b878-127">Next comes rendering the custom action</span></span>

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="5b878-128">動作的自訂轉譯</span><span class="sxs-lookup"><span data-stu-id="5b878-128">Custom Rendering of Actions</span></span>

<span data-ttu-id="5b878-129">若要為類型定義自己的自訂動作轉譯器, 我們必須先建立可從```BaseActionElementRenderer```下列範圍擴充的類別:</span><span class="sxs-lookup"><span data-stu-id="5b878-129">To define our own custom action renderer for our type, we must first create a class that extends from ```BaseActionElementRenderer```:</span></span>
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

<span data-ttu-id="5b878-130">然後, 我們會註冊此轉譯器, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="5b878-130">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerActionRenderer("myAction", new CustomActionRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
```

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="5b878-131">動作的自訂轉譯</span><span class="sxs-lookup"><span data-stu-id="5b878-131">Custom rendering of actions</span></span>

[!IMPORTANT]
> <span data-ttu-id="5b878-132">對自訂動作呈現的變更已針對 v5.2 進行規劃, 但尚未完成</span><span class="sxs-lookup"><span data-stu-id="5b878-132">Changes to the custom rendering of actions are planned for v1.2 but are not completed yet</span></span>

## <a name="custom-image-loading"></a><span data-ttu-id="5b878-133">自訂映射載入</span><span class="sxs-lookup"><span data-stu-id="5b878-133">Custom image loading</span></span>

### <a name="ionlineimageloader"></a><span data-ttu-id="5b878-134">IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="5b878-134">IOnlineImageLoader</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b878-135">**只有一個 IOnlineImageLoader 可以註冊, 而且優先于抓取影像的預設方式**</span><span class="sxs-lookup"><span data-stu-id="5b878-135">**Only one IOnlineImageLoader can be registered and it takes precedence against the default way of retrieving images**</span></span>

<span data-ttu-id="5b878-136">為了讓開發人員能夠取得無法直接從線上來源下載或抓取的影像, 或在抓取之前需要先前的步驟, 已新增 IOnlineImageLoader 來解決這種情況。</span><span class="sxs-lookup"><span data-stu-id="5b878-136">In order to allow developers to get images that could not just be downloaded or retrieved from an online source or required previous steps before they could be retrieved, the IOnlineImageLoader was added to solve this kind of situations.</span></span> <span data-ttu-id="5b878-137">若要執行 OnlineImageLoader, 您必須只執行方法</span><span class="sxs-lookup"><span data-stu-id="5b878-137">To implement an OnlineImageLoader you must only implement the method</span></span> 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

<span data-ttu-id="5b878-138">以下是 OnlineImageLoader 的範例, 其會變更 cat 映射的所有影像</span><span class="sxs-lookup"><span data-stu-id="5b878-138">Here's an example of an OnlineImageLoader which changes all images for a cat image</span></span>

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

<span data-ttu-id="5b878-139">最後, 若要註冊此映射載入器, 您必須只將這一行新增至您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5b878-139">Finally, to register this image loader, you must only add this line to your code.</span></span>

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a><span data-ttu-id="5b878-140">IResourceResolver (deprecates IOnlineImageLoader)</span><span class="sxs-lookup"><span data-stu-id="5b878-140">IResourceResolver (deprecates IOnlineImageLoader)</span></span>

<span data-ttu-id="5b878-141">針對1.2 版, 已將完整 ResourceResolvers 的支援新增至 android 轉譯器。</span><span class="sxs-lookup"><span data-stu-id="5b878-141">For v1.2, the support for full ResourceResolvers was added to the android renderer.</span></span> <span data-ttu-id="5b878-142">資源解析程式的執行與 IOnlineImageLoader 的方式非常類似, 但擁有 ResourceResolvers 可讓開發人員新增多種方法, 從單一卡片中的任何一種來源取得影像, 這是藉由連結每個 ResourceResolver 來完成。在嘗試抓取影像時, 將會查詢的唯一前置詞。</span><span class="sxs-lookup"><span data-stu-id="5b878-142">The implementation of a resource resolver is really similar to that of a IOnlineImageLoader but having ResourceResolvers allows a developer to add multiple ways to retrieve images from any kind of source in a single card, this is done by linking each ResourceResolver to a unique prefix which will be queried when trying to retrieve an image.</span></span> 

<span data-ttu-id="5b878-143">您可以執行類似下列的 ResourceResolver</span><span class="sxs-lookup"><span data-stu-id="5b878-143">You can implement a ResourceResolver similar to this</span></span>

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

<span data-ttu-id="5b878-144">如先前所述, 您可以註冊多個 ResourceResolvers, 以註冊 ResourceResolver, 您可以執行此動作</span><span class="sxs-lookup"><span data-stu-id="5b878-144">As mentioned previously, you can register multiple ResourceResolvers, to register a ResourceResolver you can do this</span></span>

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a><span data-ttu-id="5b878-145">將 IOnlineImageLoader 轉換成 IResourceResolver</span><span class="sxs-lookup"><span data-stu-id="5b878-145">Transforming an IOnlineImageLoader to an IResourceResolver</span></span> 

<span data-ttu-id="5b878-146">將 IOnlineImageLoader 轉換成 IResourceResolver 是相當簡單的工作, 因為後者的方法嘗試盡可能與 IOnlineImageLoader 保持相似</span><span class="sxs-lookup"><span data-stu-id="5b878-146">Transforming an IOnlineImageLoader to an IResourceResolver is a fairly easy task as the methods for the latter were tried to keep as similar as the IOnlineImageLoader as possible</span></span>

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

<span data-ttu-id="5b878-147">如您所見, 最大的變更為</span><span class="sxs-lookup"><span data-stu-id="5b878-147">As you can see, the biggest changes are</span></span>

* <span data-ttu-id="5b878-148">```loadOnlineImage(String, GenericImageLoaderAsync)```已重新命名為```resolveImageResource(String, GenericImageLoaderAsync)```</span><span class="sxs-lookup"><span data-stu-id="5b878-148">```loadOnlineImage(String, GenericImageLoaderAsync)``` was renamed to ```resolveImageResource(String, GenericImageLoaderAsync)```</span></span>
* <span data-ttu-id="5b878-149">已將的多載新增```resolveImageResource(String, GenericImageLoaderAsync, int)```為, 以支援需要最大寬度的案例```resolveImageResource(String, GenericImageLoaderAsync)```</span><span class="sxs-lookup"><span data-stu-id="5b878-149">an overload for ```resolveImageResource(String, GenericImageLoaderAsync)``` was added as ```resolveImageResource(String, GenericImageLoaderAsync, int)``` in order to support scenarios where the max width is required</span></span>

## <a name="custom-media-loading"></a><span data-ttu-id="5b878-150">自訂媒體載入</span><span class="sxs-lookup"><span data-stu-id="5b878-150">Custom Media Loading</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b878-151">**請```IOnlineMediaLoader```記住```MediaDataSource``` , 您必須在 API 層級23或 Android M 中新增此功能**</span><span class="sxs-lookup"><span data-stu-id="5b878-151">**Remember ```IOnlineMediaLoader``` requires ```MediaDataSource``` which was added in API level 23 or Android M**</span></span>

<span data-ttu-id="5b878-152">除了包含 media 元素之外, 也包含 IOnlineMediaLoader 介面, 可讓開發人員覆寫用於基礎 mediaPlayer 元素的[MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) 。</span><span class="sxs-lookup"><span data-stu-id="5b878-152">Along with the inclusion of the media element, also was the inclusion of the IOnlineMediaLoader interface which allows developers to override the [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) used for the underlying mediaPlayer element.</span></span> <span data-ttu-id="5b878-153">**(需要 android M)**</span><span class="sxs-lookup"><span data-stu-id="5b878-153">**(Requires android M)**</span></span>

<span data-ttu-id="5b878-154">第一個需要做的事, 就是建立一個可執行 IOnlineImageLoader 的類別</span><span class="sxs-lookup"><span data-stu-id="5b878-154">The first needed thing to do is creating a class that implements IOnlineImageLoader</span></span>

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

<span data-ttu-id="5b878-155">一旦執行此類別, 您就可以藉由新增來註冊 OnlineMediaLoader 類別</span><span class="sxs-lookup"><span data-stu-id="5b878-155">Once this class has been implemented, you can register your OnlineMediaLoader class by adding</span></span> 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```

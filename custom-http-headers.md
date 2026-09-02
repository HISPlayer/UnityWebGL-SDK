# Custom HTTP Headers
Custom HTTP Headers allow attaching additional key-value pairs to the network requests made for a given video content. This is useful for scenarios such as authentication tokens, custom CDN headers, or any server-side requirement that depends on specific HTTP header values.

Use **Multi Stream Properties** to set the Custom HTTP Headers fields. It is possible to add headers both in the editor and from code (see AddStream and AddVideoContent in [HISPlayer API](/hisplayer-api.md) for more details):

* <span style="color:blue">**HTTP Headers**</span>: Add custom HTTP headers for the content URL. Each entry is composed of a **Key** and a **Value**. There should be one list of headers per content URL. This field will have effect during the AddVideoContent functionality.

Below is an example of the usage of the Custom HTTP Headers fields in the editor. The HTTP Headers list contains the necessary Key-Value pairs, e.g. X-Test-Header / HeaderValue:

<p align="center">
<img width="1202" height="541" alt="image" src="https://github.com/user-attachments/assets/6796a585-0364-4bbd-938a-9be8614914ab" />
</p>

## Usage from code
Custom HTTP Headers can also be set programmatically using the **HTTPHeaderList** class, which wraps a list of **HTTPHeader** (key-value pairs). These headers can then be passed to **AddVideoContent** or **ChangeVideoContent**:

```csharp
HTTPHeaderList httpHeaderList = new HTTPHeaderList();
httpHeaderList.Add("X-Test-Header", "HeaderValue");

AddVideoContent(playerIndex, url, httpHeaderList);
```

Please refer to the [HISPlayer API](/hisplayer-api.md) documentation for more details about **HTTPHeaderList**, **AddVideoContent** and **ChangeVideoContent**.

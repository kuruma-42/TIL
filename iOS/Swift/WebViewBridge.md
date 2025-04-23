# WebView Bridge 추상화

### 추상화란?

-   추상화란 어떤 대상의 본질이나 성질을 추출하여 파악하는 것
-   반대로 생각해보면 가장 큰 본질이나 특성을 모아보면 해당 대상에 가깝게 된다.

### 추상화

```
public protocol WebScriptMessageHandlable {
  var names: [String] { get }
  func handle(with message: WKScriptMessage)
}
```

-   메세지를 핸들링 하는 부분이 가장 큰 특징
-   Handler가 이름을 갖는 것이 두 번째 특징

### 웹뷰 코드

```
public struct WKWebSwiftUIView: UIViewRepresentable {

  public var url: String
  public var urlOpenCallBack: ((String) -> Void)?
  public var alertAction: ((String) -> Void)?
  public var backgroundColor: UIColor?
  public var cornerRadius: CGFloat
  private let handler: WebScriptMessageHandlable?

  public init(
    url: String,
    urlOpenCallBack: ((String) -> Void)? = nil,
    alertAction: ((String) -> Void)? = nil,
    backgroundColor: UIColor? = nil,
    cornerRadius: CGFloat = 0,
    handler: WebScriptMessageHandlable? = nil
  ) {
    self.url = url
    self.urlOpenCallBack = urlOpenCallBack
    self.alertAction = alertAction
    self.backgroundColor = backgroundColor
    self.cornerRadius = cornerRadius
    self.handler = handler
  }

  public func makeUIView(context: Context) -> WKWebView {
    let configuration = WKWebViewConfiguration()
    if let handler {
      let controller = WKUserContentController()
      handler.names.forEach {
        controller.add(context.coordinator, name: $0)
      }
      configuration.userContentController = controller
    }
    let webView = WKWebView(frame: .zero, configuration: configuration)
    if let backgroundColor {
      webView.isOpaque = false
      webView.backgroundColor = backgroundColor
    }
    webView.clipsToBounds = true
    webView.layer.cornerRadius = cornerRadius
    webView.configuration.defaultWebpagePreferences.allowsContentJavaScript = true
    webView.configuration.preferences.javaScriptCanOpenWindowsAutomatically = true
    if let url = URL(string: url) {
      webView.load(URLRequest(url: url))
    }
    return webView
  }

  public func updateUIView(_ webView: WKWebView, context: UIViewRepresentableContext<WKWebSwiftUIView>) {
    if let backgroundColor {
      webView.isOpaque = false
      webView.backgroundColor = backgroundColor
    }
    webView.uiDelegate = context.coordinator
    webView.navigationDelegate = context.coordinator
    webView.clipsToBounds = true
    webView.layer.cornerRadius = cornerRadius
    guard let url = URL(string: url) else { return }
    webView.load(URLRequest(url: url))
  }

  public class Coordinator: NSObject, WKUIDelegate, WKNavigationDelegate, WKScriptMessageHandler {

    private let parent: WKWebSwiftUIView

    public init(_ parent: WKWebSwiftUIView) {
      self.parent = parent
    }

    public func webView(
      _ webView: WKWebView,
      decidePolicyFor navigationAction: WKNavigationAction,
      decisionHandler: @escaping @MainActor @Sendable (WKNavigationActionPolicy) -> Void
    ) {
      if let url = navigationAction.request.url?.absoluteString {
        parent.urlOpenCallBack?(url)
      }
      decisionHandler(.allow)
    }

    public func webView(
      _ webView: WKWebView,
      runJavaScriptAlertPanelWithMessage message: String,
      initiatedByFrame frame: WKFrameInfo,
      completionHandler: @escaping @MainActor @Sendable () -> Void
    ) {
      parent.alertAction?(message)
      completionHandler()
    }

    public func webView(
      _ webView: WKWebView,
      runJavaScriptConfirmPanelWithMessage message: String,
      initiatedByFrame frame: WKFrameInfo,
      completionHandler: @escaping @MainActor @Sendable (Bool) -> Void
    ) {
      completionHandler(true)
    }

    public func webView(
        _ webView: WKWebView,
        didFail navigation: WKNavigation!,
        withError error: any Error
    ) {
      parent.alertAction?(error.localizedDescription)
    }

    public func userContentController(
      _ userContentController: WKUserContentController,
      didReceive message: WKScriptMessage
    ) {
      parent.handler?.handle(with: message)
    }

  }

  public func makeCoordinator() -> Coordinator {
    Coordinator(self)
  }

}
```

### 구현체

```
public struct WebViewScriptHandler: WebScriptMessageHandlable {

  public let names: [String]
  private let didReceive: (_ result: WebViewMessageModel) -> Void

  public init(
    names: [String],
    didReceive: @escaping (_ result: WebViewMessageModel) -> Void
  ) {
    self.names = names
    self.didReceive = didReceive
  }

  public func handle(with message: WKScriptMessage) {
    guard names.contains(message.name) else { return }
    didReceive(
      .init(
        name: message.name,
        body: message.body
      )
    )
  }

}
```

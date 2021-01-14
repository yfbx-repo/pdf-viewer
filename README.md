# pdf-viewer

Android 预览PDF文件

- **方式一**    Android本地        

  将html和js文件复制到assets目录中，然后用WebView加载：      
  ```
  @SuppressLint("SetJavaScriptEnabled")
    private fun showPDF(webView: WebView, pdfUrl: String) {
        val webSettings = webView.settings
        webSettings.javaScriptEnabled = true
        webSettings.allowFileAccess = true
        webSettings.allowFileAccessFromFileURLs = true
        webSettings.allowUniversalAccessFromFileURLs = true

        webView.loadUrl("file:///android_asset/pdf-index.html?$pdfUrl")
    }
  
  ```
  这种方式会增大APK体积,建议使用方式二      
  
  
- **方式二**    服务端   
  服务端部署以上文件，Android端 Webview加载链接
  ```
  webView.loadUrl("http://mozilla.github.io/pdf.js/web/viewer.html?file=$pdfUrl")
  
  webView.loadUrl("https://yfbx-repo.github.io/pdf-viewer/pdf-index.html?$pdfUrl")
  ```



[来源于 mozilla/pdf.js](https://github.com/mozilla/pdf.js)

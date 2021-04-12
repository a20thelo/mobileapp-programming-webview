Koden för appen hämtades hem från profilen lenasys på github genom att projektet forkades. För att kunna öppna det som ett eget clonat projekt i Android Studios importerades url:en genom version control. 
Appens namn byttes ut till a20theloWebWiewApp från namnet WebViewApp genom foldern resurser, värden och strings. Koden som användes till det var: 
```<string name="app_name">a20thelo WebViewApp</string>```
Koden: ```<uses-permission android:name="android.permission.INTERNET" /> ```
gjorde så att internet kunde användas på enheten. Koden skrevs i foldern manifest -> androidmanifesrt.xml. Nästa steg var att skapa ett WebView- element i foldern layout -> content_main.xml. Såhär såg koden till WebView-elementet ut: ```android:id="@+id/my_webview". Det tidigare TextView-elementet som låg på samma plats togs bort för att bli ersatt med WebView. Som man kan se i koden ovanför fick WebView också en eget id ”my_webview”```. 
En private member variabel skulle skapas och det gjordes genom kodraden:
```myWebView = findViewById(R.id.my_webview)```.
Den klistrades in i java foldern -> main activity. För att JavaScript kod skulle exekveras var man först tvungen att tillåta JavaScript exekvering genom WebView, koden som användes till det var:   
 ```WebViewClient myWebViewClient = new WebViewClient();
WebSettings webSettings = myWebView.getSettings();
webSettings.setJavaScriptEnabled(true);```

En HTML-sida skulle läggas till i Android studios och för kunna lägga in HTML koden någonstans skapades en folder ”assets”.  På platsen about.html klistrades koden från HTML-dokumentet in, en ytterlgiare folder skapades för bilder ”img”. 
Koden som gjorde att den externa samt den interna sidan kunde visas var den här:  

``` public void showExternalWebPage(){
        myWebView.loadUrl("https://his.se");
    }
    public void showInternalWebPage(){
        myWebView.loadUrl("file:///android_asset/about.html");
    }```

Beroende på vad användaren väljer för sida, intern eller extern kommer den valda sidan kunna visas. Det görs genom ett villkor i en if-sats med koden: 
  ``` if (id == R.id.action_external_web) {
            Log.d("==>","Will display external web page");
            showExternalWebPage();
            return true;
        }
        if (id == R.id.action_internal_web) {
            Log.d("==>","Will display internal web page");
            showInternalWebPage();
            return true;
        }
```

deviceready
===========

このイベントはPhoneGapが完全にロードされた際に発行されます。

    document.addEventListener("deviceready", yourCallbackFunction, false);

詳細
-------

このイベントは全てのPhoneGapアプリケーションで使用される重要なイベントです。

PhoneGapはJavaScriptとネイティブコードの二つのコード要素から構成されています。ネイティブコードがロードされている間、カスタムのローディング画像が表示されます。しかしながら、JavaScriptはDOMがロードされた後でのみロードされます。

PhoneGapの `deviceready` イベントはPhoneGapが完全にロードされた際に発動します。このイベントの発動後のみPhoneGap APIを安全に使用することができます。

通常イベントを登録する際には `deviceready` イベントを拾った後で `document.addEventListener` を使うことで登録します。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    document.addEventListener("deviceready", onDeviceReady, false);

    function onDeviceReady() {
        // PhoneGap APIを安全にしようできます。
    }

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>PhoneGap Device Ready Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapの準備が完了した時に'onDeviceReady'関数を呼び出します。
        //
        // この時点ではドキュメントのロードは完了していますが、PhoneGapのロードは完了していません。
        // PhoneGapがロードされ、使用準備ができた際には
        // `deviceready` を呼び出します。
        // 
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapが完全にロードされ、PhoneGapメソッドが安全に使用できる状態になりました。
        //
        function onDeviceReady() {
            // 安全にPhoneGap APIを使用できます。
        }

        </script>
      </head>
      <body>
      </body>
    </html>
    
BlackBerry (OS 4.6) に関する注意点
--------------------------

カスタムのイベントはRIM BrowserField(ウェブブラウザビュー)ではサポートされていないため、 `deviceready` イベントは発動されません。

対策としてはマニュアルで、 `PhoneGap.available` を参照してPhoneGapのロードが完了したかを確かめることが挙げられます。

    function onLoad() {
        var intervalID = window.setInterval(
          function() {
              if (PhoneGap.available) {
                  window.clearInterval(intervalID);
                  onDeviceReady();
              }
          },
          500
        );
    }

    function onDeviceReady() {
        // 安全にPhoneGap APIを使用できます。
    }

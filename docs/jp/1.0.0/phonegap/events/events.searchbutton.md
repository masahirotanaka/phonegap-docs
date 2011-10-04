searchbutton
===========

このイベントはAndroidのサーチボタンが押された際に発行されます。

    document.addEventListener("searchbutton", yourCallbackFunction, false);

詳細
-------

Androidのサーチボタンのデフォルトの挙動を上書きしたい場合は'searchbutton'イベントをリスナーに登録し、そのコールバック関数に上書きしたい処理を書くことで可能になります。

通常イベントを登録する際には `deviceready` イベントを拾った後で `document.addEventListener` を使うことで登録します。

サポートされているプラットフォーム
-------------------

- Android

使用例
-------------

    document.addEventListener("searchbutton", onSearchKeyDown, false);

    function onSearchKeyDown() {
        // サーチボタンが押された際の処理を記述
    }

詳細な使用例
------------

    <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
                          "http://www.w3.org/TR/html4/strict.dtd">
    <html>
      <head>
        <title>PhoneGap Device Ready Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapの準備が完了した時に'onDeviceReady'関数を呼び出します。
        //
        // この時点ではドキュメントのロードは完了しているが、PhoneGapのロードは完了していません。
        // PhoneGapがロードされ、使用準備ができた際には
        // `deviceready` を呼び出します。
        // 
        function onLoad() {
            document.addEventListener("deviceready", onDeviceReady, false);
        }

        // PhoneGapが完全にロードされ、PhoneGapメソッドが安全に使用できる状態になりました。
        //
        function onDeviceReady() {
            // `searchbutton` を登録
            document.addEventListener("searchbutton", onSearchKeyDown, false);
        }
        
        // サーチボタンが押された際の処理を記述
        //
        function onSearchKeyDown() {
        }

        </script>
      </head>
      <body onload="onLoad()">
      </body>
    </html>

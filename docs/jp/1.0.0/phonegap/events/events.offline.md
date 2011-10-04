offline
===========

このイベントはPhoneGapアプリケーションがオフラインに置かれた場合に発動されるイベントです。

    document.addEventListener("offline", yourCallbackFunction, false);

詳細
-------

アプリケーションのネットワーク接続がオフラインになった場合、 `offline` イベントが発行されます。

通常イベントを登録する際には `deviceready` イベントを拾った後で `document.addEventListener` を使うことで登録します。

サポートされているプラットフォーム
-------------------

- iOS
- Android
- BlackBerry WebWorks (OS 5.0以上)

使用例
-------------

    document.addEventListener("offline", onOffline, false);

    function onOffline() {
        // オフラインになった場合の処理を記述
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
		    document.addEventListener("offline", onOffline, false);
        }

        // アプリがオフラインに置かれた場合の処理を記述
        //
        function onOffline() {
        }
        
        </script>
      </head>
      <body>
      </body>
    </html>

iOSに関する注意点
--------------------------
アプリ起動後最初の `offline` イベントの発行には最低でも1秒程度かかります。


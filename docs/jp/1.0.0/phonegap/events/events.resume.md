resume
===========

このイベントはアプリケーションがバックグラウンドからフォアグラウンドに復帰した際に発行されます。

    document.addEventListener("resume", yourCallbackFunction, false);

詳細
-------

ネイティブコードがアプリケーションをバックグラウンドからフォアグラウンドに呼び寄せた時に `resume` イベントは発動されます。 

通常イベントを登録する際には `deviceready` イベントを拾った後で `document.addEventListener` を使うことで登録します。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    document.addEventListener("resume", onResume, false);

    function onResume() {
        // アプリがフォアグラウンド復帰した際の処理を記述
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
        // この時点ではドキュメントのロードは完了しているが、PhoneGapのロードは完了していません。
        // PhoneGapがロードされ、使用準備ができた際には
        // `deviceready` を呼び出します。
        // 
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapが完全にロードされ、PhoneGapメソッドが安全に使用できる状態になりました。
        //
        function onDeviceReady() {
		    document.addEventListener("resume", onResume, false);
        }

        // アプリがフォアグラウンドに復帰した際の処理を記述
        //
        function onResume() {
        }
        
        </script>
      </head>
      <body>
      </body>
    </html>

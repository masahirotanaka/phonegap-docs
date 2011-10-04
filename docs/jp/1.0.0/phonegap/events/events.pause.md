pause
===========

このイベントはPhoneGapアプリケーションがバックグラウンドに置かれた際に発動されるイベントです。

    document.addEventListener("pause", yourCallbackFunction, false);

詳細
-------

PhoneGapアプリケーションがバックグラウンドに置かれた際に `pause` イベントが発行されます。

通常イベントを登録する際には `deviceready` イベントを拾った後で `document.addEventListener` を使うことで登録します。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    document.addEventListener("pause", onPause, false);

    function onPause() {
        // アプリがバックグラウンドに置かれた際の処理を記述
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
		    document.addEventListener("pause", onPause, false);
        }

        // アプリがバックグラウンドに置かれた際の処理を記述
        //
        function onPause() {
        }
        
        </script>
      </head>
      <body>
      </body>
    </html>

iOS Quirks
--------------------------

pauseイベントのハンドラ内では(アプリがバックグラウンドにあるため)、'alert'や'console.log'などのインタラクティブなメソッドや、PhoneGap API、Pluginで提供されているメソッド、そしてObjective-Cを使うメソッドは使用できません。
これらのメソッドはアプリがフォアグラウンドに再開された後で実行されます。

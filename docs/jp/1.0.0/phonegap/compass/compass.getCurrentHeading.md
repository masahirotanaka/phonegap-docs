compass.getCurrentHeading
=========================

現在の電子コンパスの向いている方角を取得します。

    navigator.compass.getCurrentHeading(compassSuccess, compassError, compassOptions);

概要
-----------

コンパスは現在デバイスが向いている方角を取得するセンサーです。方角は0から359.99までの数値で表されます。取得した数値は `compassSuccess` コールバック関数に渡されます。


サポートされているプラットフォーム
--------------------------------------

- Android
- iPhone

使用例
-------------

    function onSuccess(heading) {
        alert('方角: ' + heading);
    };

    function onError() {
        alert('エラーが発生しました。');
    };

    navigator.compass.getCurrentHeading(onSuccess, onError);

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Compass Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
            navigator.compass.getCurrentHeading(onSuccess, onError);
        }
    
        // 成功時の処理: 現在の方角を取得
        //
        function onSuccess(heading) {
            alert('方角: ' + heading);
        }
    
        // 失敗時の処理: 方角の取得に失敗したことをアラートで通知
        //
        function onError() {
            alert('エラーが発生しました。');
        }

        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>getCurrentHeading</p>
      </body>
    </html>
    

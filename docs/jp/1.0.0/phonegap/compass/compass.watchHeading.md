compass.watchHeading
====================

現在の方角をある一定の取得頻度で取得し続けます。

    var watchID = navigator.compass.watchHeading(compassSuccess, compassError, [compassOptions]);
                                                           
概要
-----------

コンパスは現在デバイスが向いている方角を取得するセンサーです。方角は0から359.99までの数値で表されます。取得した数値は `compassSuccess` コールバック関数に渡されます。

 `compass.watchHeading` メソッドはデバイスが現在向いている方角を一定の取得頻度で取得し続けます。取得頻度は `compassOptions` オブジェクトの `frequency` パラメータで指定することができます。
方角が取得されるごとに `headingSuccess` コールバック関数が実行されます。

 `compass.watchHeading` メソッドによって返されるwatchIDは、 `compass.clearWatch` メソッドによって現在行っている監視を停止するために必要になります。

サポートされているプラットフォーム
-------------------

- Android
- iPhone


使用例
-------------

    function onSuccess(heading) {
        var element = document.getElementById('heading');
        element.innerHTML = 'Heading: ' + heading;
    };

    function onError() {
        alert('エラーが発生しました。');
    };

    var options = { frequency: 3000 };  // 取得頻度を3秒に設定
    
    var watchID = navigator.compass.watchHeading(onSuccess, onError, options);

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Compass Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // watchIDは現在の `watchHeading` を参照
        var watchID = null;
        
        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
            startWatch();
        }

        // 方角の監視を開始
        //
        function startWatch() {
            
            // 取得頻度を3秒に設定
            var options = { frequency: 3000 };
            
            watchID = navigator.compass.watchHeading(onSuccess, onError, options);
        }
        
        // 方角の監視を停止
        //
        function stopWatch() {
            if (watchID) {
                navigator.compass.clearWatch(watchID);
                watchID = null;
            }
        }
        
        // 成功時の処理: 取得した方角をHTMLに書き込む
        //
        function onSuccess(heading) {
            var element = document.getElementById('heading');
            element.innerHTML = 'Heading: ' + heading;
        }

        // 失敗時の処理: 方角の取得に失敗したことをアラート
        //
        function onError() {
            alert('エラーが発生しました。');
        }

        </script>
      </head>
      <body>
        <div id="heading">Waiting for heading...</div>
        <button onclick="startWatch();">Start Watching</button>
        <button onclick="stopWatch();">Stop Watching</button>
      </body>
    </html>
    

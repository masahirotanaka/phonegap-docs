compass.clearWatch
========================

watichIDが示す方角監視を停止します。

    navigator.compass.clearWatch(watchID);

- __watchID__: `compass.watchHeading` によって返されるID

サポートされているプラットフォーム
-------------------

- Android
- iPhone

使用例
-------------

    var watchID = navigator.compass.watchHeading(onSuccess, onError, options);
    
    // ... 処理を記述後 ...
    
    navigator.compass.clearWatch(watchID);
    
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

        // 失敗時の処理: 方角の取得に失敗したことをアラートで通知
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

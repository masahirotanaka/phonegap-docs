accelerometer.clearWatch
========================

watchIDパラメータの参照する`加速度情報`の監視を停止します。

    navigator.accelerometer.clearWatch(watchID);

- __watchID__:  `accelerometer.watchAcceleration` によって返される加速度監視用のID

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    var watchID = navigator.accelerometer.watchAcceleration(onSuccess, onError, options);
    
    // ... 処理を記述後 ...
    
    navigator.accelerometer.clearWatch(watchID);
    
詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Accelerationの使用例</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // watchIDは現在の `watchAcceleration` で取得した情報を保持
        var watchID = null;
        
        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
            startWatch();
        }

        // 加速度の監視を開始
        //
        function startWatch() {
            
            // 3秒ごとに加速度情報を更新
            var options = { frequency: 3000 };
            
            watchID = navigator.accelerometer.watchAcceleration(onSuccess, onError, options);
        }
        
        // 加速度の監視を停止
        //
        function stopWatch() {
            if (watchID) {
                navigator.accelerometer.clearWatch(watchID);
                watchID = null;
            }
        }
		    
        // 成功時の処理: 現在の加速度情報を取得
        //
        function onSuccess(acceleration) {
            var element = document.getElementById('accelerometer');
            element.innerHTML = 'Acceleration X: ' + acceleration.x + '<br />' +
                                'Acceleration Y: ' + acceleration.y + '<br />' +
                                'Acceleration Z: ' + acceleration.z + '<br />' + 
                                'Timestamp: '      + acceleration.timestamp + '<br />';
        }

        // 失敗時の処理: 加速度情報取得に失敗したことをアラートで通知
        //
        function onError() {
            alert('エラーが発生しました。');
        }

        </script>
      </head>
      <body>
        <div id="accelerometer">加速度を監視</div>
		<button onclick="stopWatch();">停止</button>
      </body>
    </html>

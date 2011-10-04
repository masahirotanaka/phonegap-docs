accelerometer.watchAcceleration
===============================

x, y, z-軸方向の加速度をある一定の取得頻度で取得し続けます。

    var watchID = navigator.accelerometer.watchAcceleration(accelerometerSuccess,
                                                           accelerometerError,
                                                           [accelerometerOptions]);
                                                           
概要
-----------


加速度センサーはデバイスの現在の傾きの変化をキャプチャします。

 `accelerometer.watchAcceleration` メソッドは一定の取得頻度に従って現在の加速度情報を取得し続けます。
 取得頻度は `acceleratorOptions` オブジェクトの `frequency` パラメータで指定することができます。
 加速度が取得されるごとに、`accelerometerSuccess` コールバック関数が実行されます。

 `accelerometer.watchAcceleration` メソッドによって返されるwatchIDは、 `accelerometr.clearWatch` メソッドによって現在行っている監視を停止する際に必要になります。(詳細は下記の例を参照)
 

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iPhone


使用例
-------------

    function onSuccess(acceleration) {
        alert('Acceleration X: ' + acceleration.x + '\n' +
              'Acceleration Y: ' + acceleration.y + '\n' +
              'Acceleration Z: ' + acceleration.z + '\n' +
              'Timestamp: '      + acceleration.timestamp + '\n');
    };

    function onError() {
        alert('エラーが発生しました。');
    };

    var options = { frequency: 3000 };  // 取得頻度を3秒に設定
    
    var watchID = navigator.accelerometer.watchAcceleration(onSuccess, onError, options);

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Acceleration Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // watchIDは現在の `watchAcceleration` を参照
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
            
            // 3秒ごとにか速度情報を更新
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
        <div id="accelerometer">Waiting for accelerometer...</div>
      </body>
    </html>
    
 iPhoneに関する注意点
-------------

- iPhoneにおける加速度情報の取得頻度は最小40msから最大1000msに制限されています。
  - もし、取得頻度として3秒を指定した場合、加速度は制限最大の1秒ごとに取得されますが、コールバック関数は指定通り3秒で呼び出します。

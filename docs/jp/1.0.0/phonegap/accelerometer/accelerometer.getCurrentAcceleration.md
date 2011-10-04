accelerometer.getCurrentAcceleration
====================================

x, y, z-軸における現在の傾きを取得します。

    navigator.accelerometer.getCurrentAcceleration(accelerometerSuccess, accelerometerError);

概要
-----------

加速度センサーはデバイスの現在の傾きの変化をキャプチャします。
 `accelerometer.getCurrentAcceleration` メソッドで取得したデバイスの傾きの変化量はx, y, z-軸方向への数値を保持する `acceleration` オブジェクトへ格納され、成功時のコールバック関数に渡されます。


サポートされているプラットフォーム
--------------------------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
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

    navigator.accelerometer.getCurrentAcceleration(onSuccess, onError);

詳細な使用例
---------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Accelerationの使用例</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapのロードが完了 
        //
        function onDeviceReady() {
            navigator.accelerometer.getCurrentAcceleration(onSuccess, onError);
        }
    
        // 成功時の処理: 現在の加速度情報を取得
        //
        function onSuccess(acceleration) {
            alert('Acceleration X: ' + acceleration.x + '\n' +
                  'Acceleration Y: ' + acceleration.y + '\n' +
                  'Acceleration Z: ' + acceleration.z + '\n' +
                  'Timestamp: '      + acceleration.timestamp + '\n');
        }
    
        // 失敗時の処理: 加速度情報取得に失敗したことをアラートで通知
        //
        function onError() {
            alert('エラーが発生しました。');
        }

        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>getCurrentAcceleration</p>
      </body>
    </html>
    
iPhoneに関する注意点
-------------

- iPhoneではある特定の時間軸上のポイントにおける加速度を取得することができません。
- よって、iPhoneで加速度情報を処理する際には時間軸の区間において加速度を監視する必要があります。
-  デバイスがiPhoneの場合、 `getCurrentAcceleration` は `watchAcceleration` で取得した最後の値を返します。


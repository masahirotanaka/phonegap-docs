Accelerationオブジェクト
==============================

ある時点での`加速度情報`を扱うためのオブジェクトです。

プロパティ
-----------

- __x:__ x軸上における動作量 範囲: [0, 1] (`Number`)
- __y:__ y軸上における動作量 範囲: [0, 1] (`Number`)
- __z:__ z軸上における動作量 範囲: [0, 1] (`Number`)
- __timestamp:__ 加速度取得時におけるミリ秒単位のタイムスタンプ (`DOMTimeStamp`)

概要
------

このオブジェクトはPhoneGpaによって生成され、`Acceleromete` メソッドによって返されます。

サポートされているプラットフォーム
--------------------------------------

- Android
- BlackBerry WebWorks (OS 5.0 以上)
- iPhone

使用例
--------

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
--------------

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
        function onSuccess() {
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

accelerometerSuccess
====================

加速度情報に関するPhoneGapメソッドの成功時に呼び出されるコールバック関数です。

    function(acceleration) {
        // 成功時の処理 
    }

パラメータ
-----------

- __acceleration:__ 加速度情報を格納したオブジェクト (Acceleration)

使用例
-------

    function onSuccess(acceleration) {
        alert('Acceleration X: ' + acceleration.x + '\n' +
              'Acceleration Y: ' + acceleration.y + '\n' +
              'Acceleration Z: ' + acceleration.z + '\n' +
              'Timestamp: '      + acceleration.timestamp + '\n');
    };

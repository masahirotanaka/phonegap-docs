geolocationSuccess
==================

位置情報の取得に成功した際に呼び出されるコールバック関数

    function(position) {
        // 成功時の処理を記述
    }

パラメータ
----------

- __position:__ 成功時のコールバック関数に渡されるオブジェクト (`Position`)

使用例
-------

    function geolocationSuccess(position) {
        alert('Latitude: '          + position.coords.latitude          + '\n' +
              'Longitude: '         + position.coords.longitude         + '\n' +
              'Altitude: '          + position.coords.altitude          + '\n' +
              'Accuracy: '          + position.coords.accuracy          + '\n' +
              'Altitude Accuracy: ' + position.coords.altitudeAccuracy  + '\n' +
              'Heading: '           + position.coords.heading           + '\n' +
              'Speed: '             + position.coords.speed             + '\n' +
              'Timestamp: '         + new Date(position.timestamp)      + '\n');
    }

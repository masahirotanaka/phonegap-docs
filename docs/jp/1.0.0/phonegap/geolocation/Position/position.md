Position
========

位置情報に関するAPIによって生成される、各種位置情報を格納したオブジェクトです。

プロパティ
----------

- __coords:__ 位置座標を格納するオブジェクト _(Coordinates)_
- __timestamp:__ Creation timestamp for `coords` in milliseconds. _(DOMTimeStamp)_

概要
-----------

 `Position` オブジェクトは位置情報に関するメソッドの成功時のコールバック関数に渡されることで、位置情報を処理する手段を提供します。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry (OS 4.6)
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    // 成功時のコールバック関数
    //
    var onSuccess = function(position) {
        alert('Latitude: '          + position.coords.latitude          + '\n' +
              'Longitude: '         + position.coords.longitude         + '\n' +
              'Altitude: '          + position.coords.altitude          + '\n' +
              'Accuracy: '          + position.coords.accuracy          + '\n' +
              'Altitude Accuracy: ' + position.coords.altitudeAccuracy  + '\n' +
              'Heading: '           + position.coords.heading           + '\n' +
              'Speed: '             + position.coords.speed             + '\n' +
              'Timestamp: '         + new Date(position.timestamp)      + '\n');
    };

    // エラー時のコールバックが `PositionError` オブジェクトを受け取る
    //
    function onError(error) {
        alert('code: '    + error.code    + '\n' +
              'message: ' + error.message + '\n');
    }

    navigator.geolocation.getCurrentPosition(onSuccess, onError);

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Device Properties Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
            navigator.geolocation.getCurrentPosition(onSuccess, onError);
        }
    
        // 位置情報に取得した際の処理
        //
        function onSuccess(position) {
            var element = document.getElementById('geolocation');
            element.innerHTML = 'Latitude: '           + position.coords.latitude              + '<br />' +
                                'Longitude: '          + position.coords.longitude             + '<br />' +
                                'Altitude: '           + position.coords.altitude              + '<br />' +
                                'Accuracy: '           + position.coords.accuracy              + '<br />' +
                                'Altitude Accuracy: '  + position.coords.altitudeAccuracy      + '<br />' +
                                'Heading: '            + position.coords.heading               + '<br />' +
                                'Speed: '              + position.coords.speed                 + '<br />' +
                                'Timestamp: '          + new Date(position.timestamp)          + '<br />';
        }
    
	    // エラー時のコールバック関数は `PositionError` オブジェクトを受け取る
	    //
	    function onError(error) {
	        alert('code: '    + error.code    + '\n' +
	              'message: ' + error.message + '\n');
	    }

        </script>
      </head>
      <body>
        <p id="geolocation">Finding geolocation...</p>
      </body>
    </html>

iPhoneに関する注意点
-------------

- __timestamp:__ ミリ秒の代わりに秒を使用します

A workaround is to manually convert the timestamp to milliseconds (x 1000):

        var onSuccess = function(position) {
            alert('Latitude: '  + position.coords.latitude             + '\n' +
                  'Longitude: ' + position.coords.longitude            + '\n' +
                  'Timestamp: ' + new Date(position.timestamp * 1000)  + '\n');
        };

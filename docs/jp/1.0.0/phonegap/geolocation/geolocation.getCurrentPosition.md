geolocation.getCurrentPosition
==============================

デバイスの現在位置を一度だけ取得します。

    navigator.geolocation.getCurrentPosition(geolocationSuccess, 
                                             [geolocationError], 
                                             [geolocationOptions]);

パラメータ
----------

- __geolocationSuccess__: 現在位置情報を格納する `Position` オブジェクトを引数とる成功時のコールバック関数
- __geolocationError__: (Optional) エラー時のコールバック関数
- __geolocationOptions__: (Optional) オプションとして指定するオブジェクト

概要
-----------

 `geolocation.getCurrentPosition` は `geolocationSuccess` コールバックに現在位置情報を保持する `Position` オブジェクトを非同期的に返します。現在位置の取得に失敗した場合は、 `geolocationError` オブジェクトと主に `geolocationError` コールバックが呼びだされます。

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

    // 失敗時のコールバック関数
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
    
        // 成功時のコールバック関数
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
    
	    // 失敗時のコールバック関数
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

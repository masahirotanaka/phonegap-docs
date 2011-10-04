geolocation.watchPosition
=========================

デバイスの現在位置の変化を監視します。

    var watchId = navigator.geolocation.watchPosition(geolocationSuccess,
                                                      [geolocationError],
                                                      [geolocationOptions]);

パラメータ
----------

- __geolocationSuccess__: `Position` オブジェクトとともに呼びだされる成功時のコールバック関数
- __geolocationError__: (Optional) 失敗時のコールバック関数
- __geolocationOptions__: (Optional) オプションオブジェクト

返り値
-------

- __String__: `geolocation.watchPosition` を参照するwatchIDを返します。 `geolocation.clearWatch` ではこのwatchIDを参照して、位置情報の監視をストップします。

概要
-----------
 `geolocation.watchPosition` は現在位置情報の変化を感知した時に現在位置情報を保持する `Position` オブジェクトを `geolocationSuccess` コールバックに返す非同期関数です。現在位置情報の変化を感知できなかった場合には `PositionError` とともに `geolocationError` コールバックが呼び出されます。


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
    function onSuccess(position) {
        var element = document.getElementById('geolocation');
        element.innerHTML = 'Latitude: '  + position.coords.latitude      + '<br />' +
                            'Longitude: ' + position.coords.longitude     + '<br />' +
                            '<hr />'      + element.innerHTML;
    }

    // 失敗時のコールバック関数
    //
    function onError(error) {
        alert('code: '    + error.code    + '\n' +
              'message: ' + error.message + '\n');
    }

    // オプション: 位置情報を3秒ごとに取得することを指定するオプション _(object)_
    //
    var watchID = navigator.geolocation.watchPosition(onSuccess, onError, { frequency: 3000 });
    

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Device プロパティ Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        var watchID = null;

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
            // 位置情報を3秒ごとに取得
            var options = { frequency: 3000 };
            watchID = navigator.geolocation.watchPosition(onSuccess, onError, オプション);
        }
    
        // 成功時のコールバック関数
        //
        function onSuccess(position) {
            var element = document.getElementById('geolocation');
            element.innerHTML = 'Latitude: '  + position.coords.latitude      + '<br />' +
                                'Longitude: ' + position.coords.longitude     + '<br />' +
                                '<hr />'      + element.innerHTML;
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
        <p id="geolocation">Watching geolocation...</p>
      </body>
    </html>

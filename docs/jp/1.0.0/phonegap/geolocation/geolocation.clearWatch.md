geolocation.clearWatch
======================

watchIDに参照されるデバイスの位置監視を停止します。

    navigator.geolocation.clearWatch(watchID);

パラメータ
----------

- __watchID:__  現在実行中の `watchPosition` のID (String)

概要
-----------

 `geolocation.clearWatch` メソッドは `gelolocation.watchPosition` によって返されるwatchIDを参照して `geolocation.watchPosition` の位置情報取得を停止します。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry (OS 4.6)
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    // オプション _(object)_ : 位置情報を3秒ごとに取得
    //
    var watchID = navigator.geolocation.watchPosition(onSuccess, onError, { frequency: 3000 });

    // ...後の処理を記述...

    navigator.geolocation.clearWatch(watchID);


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

        var watchID = null;

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
            // 'geolocation.watchPosition'で位置情報を3秒ごとに取得
            var options = { frequency: 3000 };
            watchID = navigator.geolocation.watchPosition(onSuccess, onError, オプション);
        }
    
        // 位置情報取得成功時のコールバック関数
        //
        function onSuccess(position) {
            var element = document.getElementById('geolocation');
            element.innerHTML = 'Latitude: '  + position.coords.latitude      + '<br />' +
                                'Longitude: ' + position.coords.longitude     + '<br />' +
                                '<hr />'      + element.innerHTML;
        }

        // 位置情報取得を停止
        // 
        function clearWatch() {
            if (watchID != null) {
                navigator.geolocation.clearWatch(watchID);
                watchID = null;
            }
        }
    
	    // 失敗時のコールバック関数は `positionError` オブジェクトを受け取る
	    //
	    function onError(error) {
	      alert('code: '    + error.code    + '\n' +
	            'message: ' + error.message + '\n');
	    }

        </script>
      </head>
      <body>
        <p id="geolocation">Watching geolocation...</p>
    	<button onclick="clearWatch();">Clear Watch</button>     
      </body>
    </html>

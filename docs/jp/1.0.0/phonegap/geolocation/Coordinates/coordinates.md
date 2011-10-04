Coordinates
===========

様々な位置座標情報を格納するオブジェクトです。

プロパティ
----------

* __latitude__: 緯度を表す数値(メートル) _(Number)_
* __longitude__: 経度を表す数値(メートル) _(Number)_
* __altitude__: 海抜からの高度をあらあわす数値(メートル) _(Number)_
* __accuracy__: 取得した緯度/経度の精度を表す数値 _(number)_
* __altitudeAccuracy__: 取得した高度の制度を表す数値 _(Number)_
* __heading__: 北から時計回りで計られる。デバイスの向いている方向を表す1-359.99までの数値 _(Number)_
* __speed__: デバイスの移動スピードを表す数値(メートル/秒) _(Number)_

概要
-----------

 `Coordinates` オブジェクトは 位置情報に関するメソッドの成功時のコールバック関数のパラメータに渡される `Position` オブジェクトのメンバーとして生成されます。

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
    var onError = function() {
        alert('エラーが発生しました。');
    };

    navigator.geolocation.getCurrentPosition(onSuccess, onError);

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Geolocation Position Example</title>
        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap準備完了
        //
        function onDeviceReady() {
            navigator.geolocation.getCurrentPosition(onSuccess, onError);
        }
    
        //  `Position` のプロパティーを表示
        //
        function onSuccess(position) {
            var div = document.getElementById('myDiv');
        
            div.innerHTML = 'Latitude: '             + position.coords.latitude  + '<br/>' +
                            'Longitude: '            + position.coords.longitude + '<br/>' +
                            'Altitude: '             + position.coords.altitude  + '<br/>' +
                            'Accuracy: '             + position.coords.accuracy  + '<br/>' +
                            'Altitude Accuracy: '    + position.coords.altitudeAccuracy  + '<br/>' +
                            'Heading: '              + position.coords.heading   + '<br/>' +
                            'Speed: '                + position.coords.speed     + '<br/>';
        }
    
        // 位置情報の取得に失敗したことをアラート
        //
        function onError() {
            alert('エラーが発生しました。');
        }

        </script>
      </head>
      <body>
        <div id="myDiv"></div>
      </body>
    </html>
    
Androidに関する注意点
-------------

__altitudeAccuracy:__ このプロパティはAndroidではサポートされておらず常に'null'を返します。

device.uuid
===========

デバイスのUUID (http://en.wikipedia.org/wiki/Universally_Unique_Identifier) を取得します。

    var string = device.uuid;
    
概要
-----------

デバイスのUUIDは端末の製造元によって設定されます。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    // Android: 64-bit のランダムなintegerを文字列として返します。
    //          この文字列はデバイスが最初にブートしたときに設定されます。
    //
    // BlackBerry: デバイスのPINを返します。(9つのユニークな文字列としての数字)
    //
    // iPhone: ハッシュ値の文字列を返します。
    //         この値は各デバイス固有のものであり、ユーザアカウントとは関連付けされません。
    //         
    //
    var deviceID = device.uuid;

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
            var element = document.getElementById('deviceProperties');
    
            element.innerHTML = 'Device Name: '     + device.name     + '<br />' + 
                                'Device PhoneGap: ' + device.phonegap + '<br />' + 
                                'Device Platform: ' + device.platform + '<br />' + 
                                'Device UUID: '     + device.uuid     + '<br />' + 
                                'Device Version: '  + device.version  + '<br />';
        }

        </script>
      </head>
      <body>
        <p id="deviceProperties">Loading device properties...</p>
      </body>
    </html>

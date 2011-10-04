device.phonegap
===============

アプリケーションで使われているPhoneGapのバージョンを返します。

    var string = device.phonegap;
    
概要
-----------

`device.phonegap` はアプリケーションで使われているPhoneGapのバージョンを返します。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    var name = device.phonegap;

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
    

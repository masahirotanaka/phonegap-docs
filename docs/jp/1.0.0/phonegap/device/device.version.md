device.version
==============

OSのバージョンを取得します。

    var string = device.version;

サポートされているプラットフォーム
-------------------

- Android 2.1+
- BlackBerry
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    // Android:    Froyo OS は "2.2" を返します。
    //             Eclair OS は "2.1", "2.0.1", または "2.0" を返します。
    //
    // BlackBerry: BOS 4.6 上のBold 9000 は "4.6.0.282" を返します。
    //
    // iPhone:     iOS 3.2 は "3.2" を返します。
    //
    var deviceVersion = device.version;

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

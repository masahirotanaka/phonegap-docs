device.name
===========

デバイスのモデル名を返します。

    var string = device.name;
    
概要
-----------

`device.name` はデバイスのモデル名を返します。 この値はデバイスの製造元によって設定され、バージョンによっては同じ端末でも異なった値を返す場合があります。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    // Android:    Nexus One       => "Passion" (Nexus One code name)
    //             Motorola Droid  => "voles"
    // BlackBerry: Bold 8900       => "8900"
    // iPhone:     All devices     => a name set by iTunes e.g. "Joe's iPhone"
    //
    var name = device.name;

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


Androidに関する注意点
--------------

- Androidの場合は [model name](http://developer.android.com/reference/android/os/Build.html#MODEL) の代わりに [product name](http://developer.android.com/reference/android/os/Build.html#PRODUCT) を返します。
    - product nameは開発段階でのコードネームとなります。
    - 例) Nexus One の場合は "Passion" を返し, Motorola Droid は "voles" を返します。

iPhoneに関する注意点
-------------

- iPhoneの場合は [device model name](http://developer.apple.com/iphone/library/documentation/uikit/reference/UIDevice_Class/Reference/UIDevice.html#//apple_ref/doc/uid/TP40006902-CH3-SW1) の代わりに[device's custom name](http://developer.apple.com/iphone/library/documentation/uikit/reference/UIDevice_Class/Reference/UIDevice.html#//apple_ref/doc/uid/TP40006902-CH3-SW13) を返します。
    - custom name はiTunesでデバイスの所有者によって設定されます。
    - 例) "Joe's iPhone"

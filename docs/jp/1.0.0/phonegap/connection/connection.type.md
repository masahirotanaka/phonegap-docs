connection.type
===================

現在デバイスによって使われているネットワークへの接続手段を取得します。

概要
-----------

デバイスのネットワークへの接続手段にアクセスする場合はこのプロパティーを使います。

サポートされているプラットフォーム
-------------------

- iOS
- Android
- BlackBerry WebWorks (OS 5.0以上)

使用例
-------------

    function checkConnection() {
        var networkState = navigator.network.connection.type;
        
        var states = {};
        states[Connection.UNKNOWN]	= '不明な接続です';
        states[Connection.ETHERNET]	= 'イーサネット接続';
        states[Connection.WIFI]   	= 'WiFi接続';
        states[Connection.CELL_2G]	= '2G接続';
        states[Connection.CELL_3G]	= '3G接続';
        states[Connection.CELL_4G]	= '4G接続';
        states[Connection.NONE]   	= 'ネットワークに接続されていません';
    
        alert('Connection type: ' + states[networkState]);
    }
    
    checkConnection();


詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>navigator.network.connection.type Example</title>
        
        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">
            
        // PhoneGapのロードを待機
        // 
        document.addEventListener("deviceready", onDeviceReady, false);
        
        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
            checkConnection();
        }
        
	    function checkConnection() {
	        var networkState = navigator.network.connection.type;

	        var states = {};
	        states[Connection.UNKNOWN]	= '不明な接続です';
	        states[Connection.ETHERNET]	= 'イーサネット接続';
	        states[Connection.WIFI]   	= 'WiFi接続';
	        states[Connection.CELL_2G]	= '2G接続';
	        states[Connection.CELL_3G]	= '3G接続';
	        states[Connection.CELL_4G]	= '4G接続';
	        states[Connection.NONE]   	= 'ネットワークに接続されていません';

	        alert('接続手段: ' + states[networkState]);
	    }
        
        </script>
      </head>
      <body>
        <p>A dialog box will report the network state.</p>
      </body>
    </html>

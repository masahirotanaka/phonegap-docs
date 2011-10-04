localStorage
===============

W3C Storageインターフェース (http://dev.w3.org/html5/webstorage/#the-localstorage-attribute)を扱うためのオブジェクトです。

    var storage = window.localStorage;

メソッド
-------

- __key__: 指定されたポジションのキー名を返します。 
- __getItem__: キーで指定されたアイテムを取得します。
- __setItem__: キーで指定した位置にアイテムを保存します。
- __removeItem__: キーで指定したアイテムを削除します。
- __clear__: 全てのキー/バリューペアを削除します。

詳細
-----------

localStorageはW3CのStorageへのインターフェースを提供します。 

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 6.0以上)
- iPhone

Key 使用例
-------------

    var keyName = window.localStorage.key(0);

Set Item 使用例
-------------

    window.localStorage.setItem("key", "value");

Get Item 使用例
-------------

	var value = window.localStorage.getItem("key");
	// value is now equal to "value"

Remove Item 使用例
-------------

	window.localStorage.removeItem("key");

Clear 使用例
-------------

	window.localStorage.clear();

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Contact Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
			window.localStorage.setItem("key", "value");
			var keyname = window.localStorage.key(i);
			// var keynameは"key"を保持
			var value = window.localStorage.getItem("key");
			// var valueは"value"を保持
			window.localStorage.removeItem("key");
			window.localStorage.setItem("key2", "value2");
			window.localStorage.clear();
			// localStorageは空
        }
    

        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>localStorage</p>
      </body>
    </html>

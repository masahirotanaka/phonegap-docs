openDatabase
===============

新しい'Database'オブジェクトを生成します。

    var dbShell = window.openDatabase(name, version, display_name, size);

概要
-----------

window.openDatabaseは新しいSQL Liteデータベースを作成し、'Database'オブジェクトを返します。
データベースを操作するためにはこのオブジェクトを使います。


サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 6.0以上)
- iPhone

使用例
-------------

    var db = window.openDatabase("test", "1.0", "Test DB", 1000000);

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
			var db = window.openDatabase("test", "1.0", "Test DB", 1000000);
        }
		
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Open Database</p>
      </body>
    </html>

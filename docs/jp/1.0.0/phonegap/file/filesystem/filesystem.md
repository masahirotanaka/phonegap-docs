FileSystem
==========

ファイルシステムを扱うオブジェクトです。

プロパティ
----------

- __name:__ ファイルシステム名 _(DOMString)_
- __root:__ ファイルシステムのルートディレクトリ _(DirectoryEntry)_

詳細
-------

 `FileSystem`オブジェクトはファイルシステムに関する情報を扱うためのオブジェクトです。 `name` プロパティはファイルシステム間で独自の値を保持しており、`root` プロパティはファイルシステムのルートディレクトリ情報を保持する `DirectoryEntry` オブジェクトを保持しています。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

File System 使用例
-------------------------

	function onSuccess(fileSystem) {
		console.log(fileSystem.name);
		console.log(fileSystem.root.name);
	}
	
	// 永続的なファイルシステムをリクエスト
	window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, onSuccess, null);

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>File System Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
			window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, onFileSystemSuccess, fail);
        }

		function onFileSystemSuccess(fileSystem) {
			console.log(fileSystem.name);
			console.log(fileSystem.root.name);
		}
		
		function fail(evt) {
			console.log(evt.target.error.code);
		}
		
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>File System</p>
      </body>
    </html>

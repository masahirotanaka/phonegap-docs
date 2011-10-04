LocalFileSystem
===============

This object provides a way to obtain root file systems.
このオブジェクトはrootファイルシステムにアクセスする手段を提供します。

メソッド
----------

- __requestFileSystem:__ ファイルシステムを要求します。 _(Function)_
- __resolveLocalFileSystemURI:__ ローカルのURIを使ってDirectoryEntryかFileEntryを取得します。 _(Function)_

定数
---------

- `LocalFileSystem.PERSISTENT`: ユーザパーミッションまたはアプリケーションの許可無しに削除できないストレージに対して使用します。
- `LocalFileSystem.TEMPORARY`: 一時的なストレージに対して使用します。

Details
-------

 `LocalFileSystem` オブジェクトのメソッドは __window__ オブジェクトに定義されます。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

Request File System 使用例
---------------------------------

	function onSuccess(fileSystem) {
		console.log(fileSystem.name);
	}
	
	// 永続的なファイルシステムを要求
	window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, onSuccess, onError);

Resolve Local File System URI 使用例
-------------------------------------------

	function onSuccess(fileEntry) {
		console.log(fileEntry.name);
	}

	window.resolveLocalFileSystemURI("file:///example.txt", onSuccess, onError);
	
詳細な使用例
------------


    <!DOCTYPE html>
    <html>
      <head>
        <title>Local File System Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
			window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, onFileSystemSuccess, fail);
			window.resolveLocalFileSystemURI("file:///example.txt", onResolveSuccess, fail);
        }

		function onFileSystemSuccess(fileSystem) {
			console.log(fileSystem.name);
		}

		function onResolveSuccess(fileEntry) {
			console.log(fileEntry.name);
		}
		
		function fail(evt) {
			console.log(evt.target.error.code);
		}
		
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Local File System</p>
      </body>
    </html>

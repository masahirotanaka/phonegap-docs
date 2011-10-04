FileReader
==========

 `FileReader`はファイルの読み込みを扱うためのオブジェクトです。

プロパティ
----------

- __readyState:__ 次のいずれかのステータスが保持されます: EMPTY, LOADING, DONE
- __result:__ 読み込まれたファイルのコンテンツ _(DOMString)_
- __error:__ `FileError` オブジェクト _(FileError)_
- __onloadstart:__ 読み込み開始時に呼ばれる関数 _(Function)_
- __onprogress:__ ファイル読み込み中に呼ばれ、進捗状況を報告する (progess.loaded/progress.total) _(Function)_ - 現在はサポートされていません
- __onload:__ 読み込み成功時に呼ばれる関数 _(Function)_
- __onabort:__ 読み込みが中断された際に呼ばれる関数 _(Function)_
- __onerror:__ 読み込み失敗時に呼ばれる関数 _(Function)_
- __onloadend:__ 成功失敗を問わず、リクエストが完了した際に呼ばれる関数  _(Function)_

メソッド
-------

- __abort__: ファイルの読み込みを中止します
- __readAsDataURL__: ファイルを読み込み、base64形式でエンコードされたデータのURLを返します
- __readAsText__: テキストファイルを読み込みます

詳細
-------

 `FileReader`オブジェクトはデバイスのファイルシステムに存在するファイルの読み込みを扱います。ファイルの読み込みはテキストまたはbase64形式でエンコードされた文字列として行われます。ファイル読み込み関連のイベントとして'loadstart', 'progress', 'load', 'loadend', 'error', 'abort'イベントをハンドリングすることができます。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

URLデータとして読み込む
------------------------

__パラメータ:__
- file - 読み込みの対象となる `file` オブジェクト


使用例
-------------

	function win(file) {
		var reader = new FileReader();
		reader.onloadend = function(evt) {
        	console.log("読み込みに成功しました。");
            console.log(evt.target.result);
        };
		reader.readAsDataURL(file);
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.file(win, fail);

テキストとして読み込む
------------------------------

__パラメータ:__

- file - 読み込みの対象となる `file` オブジェクト
- encoding - ファイルのエンコディングに使用するエンコード。デフォルトはUTF-8

使用例
-------------

	function win(file) {
		var reader = new FileReader();
		reader.onloadend = function(evt) {
        	console.log("読み込みに成功しました。");
            console.log(evt.target.result);
        };
		reader.readAsText(file);
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.file(win, fail);

Abort 使用例
-------------------

	function win(file) {
		var reader = new FileReader();
		reader.onloadend = function(evt) {
        	console.log("読み込みに成功しました。");
            console.log(evt.target.result);
        };
		reader.readAsText(file);
		reader.abort();
	};

    function fail(error) {
    	console.log(error.code);
    }
	
    entry.file(win, fail);

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>FileReader Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        function onLoad() {
            document.addEventListener("deviceready", onDeviceReady, false);
        }

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
			window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, gotFS, fail);
        }
		
		function gotFS(fileSystem) {
			fileSystem.root.getFile("readme.txt", {create: true}, gotFileEntry, fail);
		}
		
		function gotFileEntry(fileEntry) {
			fileEntry.file(gotFile, fail);
		}
		
        function gotFile(file){
			readDataUrl(file);
			readAsText(file);
		}
        
        function readDataUrl(file) {
            var reader = new FileReader();
            reader.onloadend = function(evt) {
                console.log("Read as data URL");
                console.log(evt.target.result);
            };
            reader.readAsDataURL(file);
        }
        
        function readAsText(file) {
            var reader = new FileReader();
            reader.onloadend = function(evt) {
                console.log("Read as text");
                console.log(evt.target.result);
            };
            reader.readAsText(file);
        }
        
        function fail(evt) {
            console.log(evt.target.error.code);
        }
        
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Read File</p>
      </body>
    </html>

iOSに関する注意点
----------
- __encoding__ このプロパティはiOSではサポートされていません。iOSデバイスでは常にUTF-8を使用します。

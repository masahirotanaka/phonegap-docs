FileWriter
==========

 `FileWriter` オブジェクトはファイルの書き込みを扱うオブジェクトです。

プロパティ
----------

- __readyState:__ 次のいずれかのステータスが保持されます: EMPTY, LOADING, DONE
- __fileName:__ 書き込みの対象となるファイル名 _(DOMString)_
- __length:__ 書き込みの対象となるファイルの長さ_(long)_
- __position:__ 書き込みの対象となるファイルの現在のファイルポインタの位置 _(long)_
- __error:__ `FileError` オブジェクト _(FileError)_
- __onwritestart:__ 書き込み開始時に呼ばれる関数 _(Function)_
- __onprogress:__ ファイル書き込み中に呼ばれ、進捗状況を報告する (progess.loaded/progress.total). _(Function)_ -現在サポートされていません
- __onwrite:__ リクエスト完了時に呼ばれる関数 _(Function)_
- __onabort:__ 書き込みが中断された際に呼び出される関数 _(Function)_
- __onerror:__ 書き込み失敗時に呼び出される関数 _(Function)_
- __onwriteend:__ 成功失敗を問わず、リクエストが完了した際に呼ばれる関数  _(Function)_

メソッド
-------

- __abort__: 書き込みを中断します 
- __seek__: 指定されたバイト数にファイルポインタを移動させます
- __truncate__: 指定した長さにファイルの長さを縮めます
- __write__: データをファイルに書き込みます


詳細
-------

 `FileWriter` オブジェクトはファイルシステム内に存在するファイルへの書き込み手段を提供します。
  ファイル書き込み関連のイベントとして'writestart', 'progress', 'write', 'writeend', 'error', 'abort'イベントをハンドリングすることができます。

  `FileWriter` は一つのファイルに対して作成され、そのファイルに対して複数回の書き込みを行うことができます。 `FileWriter` はファイルのposition, lenghthプロパティを管理しているため、ファイルの任意の位置に書き込みを行うことができます。デフォルトでのファイルポインタの位置はファイルの先頭になります(このまま書き込むと既存のデータを上書きします)。FileWriterのコンストラクタにappendプロパティを'true'に設定することで、ファイルの末尾から書き込みを行うことができます。


サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

Seek 使用例
------------------------------

	function win(writer) {
		// ファイルポインタをEOFへ移動させます
		writer.seek(writer.length);	
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.createWriter(win, fail);

Truncate 使用例
--------------------------

	function win(writer) {
		writer.truncate(10);	
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.createWriter(win, fail);

Write 使用例
-------------------	

	function win(writer) {
		writer.onwrite = function(evt) {
        	console.log("書き込みに成功しました。");
        };
		writer.write("サンプルテキスト");
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.createWriter(win, fail);

Append 使用例
--------------------	

	function win(writer) {
		writer.onwrite = function(evt) {
        	console.log("書き込みが成功しました。");
        };
        writer.seek(writer.length);
		writer.write("appended text");
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.createWriter(win, fail);
	
Abort 使用例
-------------------

	function win(writer) {
		writer.onwrite = function(evt) {
        	console.log("書き込みに成功しました。");
        };
		writer.write("サンプルテキスト");
		writer.abort();
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.createWriter(win, fail);

詳細な使用例
------------
    <!DOCTYPE html>
    <html>
      <head>
        <title>FileWriter Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.0.9.4.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
			window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, gotFS, fail);
        }
		
		function gotFS(fileSystem) {
			fileSystem.root.getFile("readme.txt", {create: true}, gotFileEntry, fail); 
		}
		
		function gotFileEntry(fileEntry) {
			fileEntry.createWriter(gotFileWriter, fail);
		}
		
		function gotFileWriter(writer) {
	        writer.onwrite = function(evt) {
                console.log("書き込みに成功しました。");
            };
            writer.write("some sample text");
			// 現在のファイルコンテンツは 'some sample text'
			writer.truncate(11);
			// この時点でのファイルコンテンツは'some sample'
			writer.seek(4);
			// ファイルコンテンツはまだ 'some sample' ですが、ポインターは'some'にある'e'の後へ移動しています
			writer.write(" different text");
			// ファイルコンテンツは 'some different text' となります
		}
        
        function fail(error) {
            console.log(error.code);
        }
        
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Write File</p>
      </body>
    </html>

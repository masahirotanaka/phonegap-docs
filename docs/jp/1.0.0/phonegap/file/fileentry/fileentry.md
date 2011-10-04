FileEntry
==========

このオブジェクトはファイルシステム内のファイルを扱うためのオブジェクトです。[W3C Directories and Systems](http://www.w3.org/TR/file-system-api/) に批准しています。

プロパティ
----------

- __isFile:__ 常に'true' _(boolean)_
- __isDirectory:__ 常に'false' _(boolean)_
- __name:__ ファイル名 _(DOMString)_
- __fullPath:__ ルートからファイルまでの絶対パス _(DOMString)_

NOTE: 下記のプロパティはW3C仕様で定義されていますが、PhoneGapではサポートされていません。

- __filesystem:__ このファイルが存在しているファイルシステム名 _(FileSystem)_


メソッド
-------

- __getMetadata__: ファイルのメタデータを取得します。
- __moveTo__: ファイルを別の場所に移動します。
- __copyTo__: ファイルを別の場所にコピーします。
- __toURI__: ファイルのURIを取得します。
- __remove__: ファイルを削除します。
- __getParent__: ファイルの保存先の親ディレクトリを取得します。
- __createWriter__: ファイルへの書き込みを行うことができる'FileWriter'オブジェクトを作成します。
- __file__: ファイルのプロパティを格納している'File'オブジェクトを作成します。


サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

getMetadata
----------------

ファイルのメタデータを取得します。

__パラメータ:__

- __successCallback__ - 'Metadata'オブジェクトを引数に呼び出される成功時のコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出されるエラー時のコールバック関数 _(Function)_


__使用例__

    function success(metadata) {
        console.log("最終更新日: " + metadata.modificationTime);
    }

    function fail(error) {
        alert(error.code);
    }

    // メタデータをリクエスト
    entry.getMetadata(success, fail);	


moveTo
------

ファイルを別の場所に移動します。

- 親ディレクトリにファイルを移動します。
- ファイルを指定したパスに移動します。

既に同じ名前のファイルが存在する場合は、そのファイルを上書きします。

__パラメータ:__

- __parent__ - ファイル移動先の親ディレクトリ _(DirectoryEntry)_
- __newName__ - 新しいファイル名。デフォルトは現在のファイル名 _(DOMString)_
- __successCallback__ - 新しいファイルの'FileEntry'オブジェクトを引数に呼び出される成功時のコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出される失敗時のコールバック関数 _(Function)_


__使用例__

    function success(entry) {
        console.log("新しいパス: " + entry.fullPath);
    }

    function fail(error) {
        alert(error.code);
    }

    function moveFile(entry) {
        var parent = document.getElementById('parent').value,
            parentEntry = new DirectoryEntry({fullPath: parent});

        // ファイルを新しいディレクトリに移動し、名前を変更する
        entry.moveTo(parentEntry, "newFile.txt", success, fail);
    }
	

copyTo
------

ファイルを別の場所にコピーします。

- 親ディレクトリにファイルをコピーします。

__パラメータ:__

- __parent__ - ファイルコピー先の親ディレクトリ _(DirectoryEntry)_
- __newName__ - 新しいファイル名。デフォルトは現在のファイル名 _(DOMString)_
- __successCallback__ - 新しいファイルの'FileEntry'オブジェクトを引数に呼び出される成功時のコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出される失敗時のコールバック関数 _(Function)_


__使用例__

    function win(entry) {
	    console.log("新しいパス: " + entry.fullPath);
    }

    function fail(error) {
	    alert(error.code);
    }

    function copyFile(entry) {
        var parent = document.getElementById('parent').value,
            parentEntry = new DirectoryEntry({fullPath: parent});

        // ファイルを新しいディレクトリにコピーし、名前を変更
        entry.copyTo(parentEntry, "file.copy", success, fail);
    }

	
toURI
-----

ファイルの保存先URIを取得します。

__使用例__
	
    // ファイルのメタデータをリクエスト
    var uri = entry.toURI();
    console.log(uri);


remove
------

ファイルを削除します

__パラメータ:__

- __successCallback__ - ファイル削除の成功時に呼び出されるコールバック関数 _(Function)_
- __errorCallback__ - 失敗時のコールバック関数 _(Function)_

__使用例__
	
    function success(entry) {
        console.log("ファイルの削除に成功しました。");
    }

    function fail(error) {
        alert('ファイルの削除に失敗: ' + error.code);
    }

    // ファイルを削除
    entry.remove(success, fail);


getParent
---------

ファイルの保存先の親ディレクトリを取得します。

__パラメータ:__

- __successCallback__ - 'DirectoryEntry'オブジェクトを引数に呼び出される成功時のコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出される失敗時のコールバック関数 _(Function)_

__使用例__
	
    function success(parent) {
        console.log("親ディレクトリ名: " + parent.name);
    }

    function fail(error) {
        alert(error.code);
    }

    // 'DirectoryEntry'を取得
    entry.getParent(success, fail);	


createWriter
-------------

ファイルへの書き込みを行うことができる'FileWriter'オブジェクトを作成します。

__パラメータ:__

- __successCallback__ - 'FileWriter'オブジェクトを引数に呼び出される成功時のコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出される失敗時のコールバック関数 _(Function)_

__使用例__
	
    function success(writer) {
        writer.write("ファイルへ追加するテキストを記述");
    }

    function fail(error) {
        alert(error.code);
    }

    // 'FileWriter'オブジェクトを作成
    entry.createWriter(success, fail);	


file
----

ファイルのプロパティを格納している'File'オブジェクトを作成します。

__パラメータ:__

- __successCallback__ - 'File'オブジェクトを引数に呼び出される成功時のコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出される失敗時のコールバック関数 _(Function)_

__使用例__
	
    function success(file) {
        console.log("File size: " + file.size);
    }

    function fail(error) {
        alert("ファイルプロパティの取得に失敗しました: " + error.code);
    }
 
    // ファイルのプロパティを取得
    entry.file(success, fail);	

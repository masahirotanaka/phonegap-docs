DirectoryEntry
==============

このオブジェクトはファイルシステム内のディレクトリを扱うためのオブジェクトです。[W3C Directories and Systems](http://www.w3.org/TR/file-system-api/) に批准しています。


プロパティ
----------

- __isFile:__ 常に'false' _(boolean)_
- __isDirectory:__ 常に'true' _(boolean)_
- __name:__ パスを除いたディレクトリの名前 _(DOMString)_
- __fullPath:__ ルートからディレクトリまでの絶対パス _(DOMString)_

NOTE: 下記のプロパティはW3C仕様で定義されていますが、PhoneGapではサポートされていません。

- __filesystem:__ このディレクトリが存在しているファイルシステム名 _(FileSystem)_ 

メソッド
-------

 `DirectoryEntry` は下記のメソッドを呼び出すことができます:

- __getMetadata__: ディレクトリのメタデータを取得します。
- __moveTo__: ディレクトリを別の場所に移動します。
- __copyTo__: ディレクトリを別の場所にコピーします。
- __toURI__: ディレクトリのURIを取得します。
- __remove__: ディレクトリを削除します。(空のディレクトリのみ削除可能)
- __getParent__: ディレクトリの親ディレクトリを取得します。
- __createReader__: ディレクトリ内のエントリの読み込みができる `DirectoryReader` オブジェクトを作成します。
- __getDirectory__: ディレクトリを作成、または取得します。
- __getFile__: ファイルを作成、または取得します。
- __removeRecursively__: ディレクトリとその中身を全て削除します。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

getMetadata
-----------

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

ディレクトリを別の場所に移動します。 以下の処理を行うとエラーが発生します:

- ディレクトリを自分自身または、自身の中に存在するいかなる子ディレクトリに移動する
- move a directory into its parent if a name different from its current one is not provided;
- ファイルを示すパスにディレクトリを移動する
- 空でないディレクトリを示すパスにディレクトリを移動するmove a directory to a path occupied by a directory which is not empty.

In addition, an attempt to move a directory on top of an existing empty directory must attempt to delete and replace that directory.

上記に加えて、あるディレクトリを既に存在している空のディレクトリに移動する場合、

__パラメータ:__

- __parent__ - ディレクトリ移動先の親ディレクトリ _(DirectoryEntry)_
- __newName__ - 新しいディレクトリ名。デフォルトは現在のディレクトリ名 _(DOMString)_
- __successCallback__ - 新しいディレクトリの'DirectoryEntry'オブジェクトを引数に呼び出される成功時のコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出される失敗時のコールバック関数 _(Function)_


__使用例__

    function success(entry) {
        console.log("新しいパス: " + entry.fullPath);
    }

    function fail(error) {
        alert(error.code);
    }
	
	function moveDir(entry) {
        var parent = document.getElementById('parent').value,
            newName = document.getElementById('newName').value,
            parentEntry = new DirectoryEntry({fullPath: parent});

        // ディレクトリを移動し、名前を変更
        entry.moveTo(parentEntry, newName, success, fail);
    }

copyTo
------

ディレクトリを別の場所にコピーします。 以下の処理を行うとエラーが発生します:

- ディレクトリを自分自身または、自身の中に存在するいかなる子ディレクトリにコピーする
- copy a directory into its parent if a name different from its current one is not provided. 

ディレクトリのコピーは自身の中にあるファイルやディレクトリを全てコピーします。

__パラメータ:__

- __parent__ - ファイルコピー先の親ディレクトリ _(DirectoryEntry)_
- __newName__ - 新しいディレクトリ名。デフォルトは現在のディレクトリ名 _(DOMString)_
- __successCallback__ - 新しいディレクトリの'DirectoryEntry'オブジェクトを引数に呼び出される成功時のコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出される失敗時のコールバック関数 _(Function)_


__使用例__

	function win(entry) {
		console.log("新しいパス: " + entry.fullPath);
	}
	
	function fail(error) {
		alert(error.code);
	}
	
	function copyDir(entry) {
        var parent = document.getElementById('parent').value,
            newName = document.getElementById('newName').value,
            parentEntry = new DirectoryEntry({fullPath: parent});

        // ファイルを新しいディレクトリにコピーし、名前を変更する
        entry.copyTo(parentEntry, newName, success, fail);
    }


toURI
-----

ディレクトリのURIを取得します。

__使用例__
	
    // このディレクトリのURIを取得
    var uri = entry.toURI();
    console.log(uri);


remove
------

ディレクトリを削除します。 以下の処理を行うとエラーが発生します:

- 空でないディレクトリを削除する
- ファイルシステムのルートディレクトリを削除する

__パラメータ:__

- __successCallback__ - ディレクトリ削除の成功時に呼び出されるコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出される失敗時のコールバック関数 _(Function)_

__使用例__
	
    function success(entry) {
        console.log("削除に成功しました。");
    }

    function fail(error) {
        alert('ディレクトリの削除に失敗しました: ' + error.code);
    }

    // ディレクトリを削除
    entry.remove(success, fail);


getParent
---------

親ディレクトリを取得します。

__パラメータ:__

- __successCallback__ - 'DirectoryEntry'オブジェクトを引数に呼び出される成功時のコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出される失敗時のコールバック関数 _(Function)_

__使用例__
	
    function success(parent) {
        console.log("親ディレクトリ名: " + parent.name);
    }
 
    function fail(error) {
        alert('親ディレクトリの取得に失敗しました: ' + error.code);
    }
	
	// 親ディレクトリを取得
	entry.getParent(success, fail);	


createReader
------------

 `DirectoryReader`オブジェクトを作成します。

__使用例__
	
    // `DirectoryReader`オブジェクトを作成
    var directoryReader = entry.createReader();	


getDirectory
------------

ディレクトリを作成または取得します。以下の処理を行うとエラーが発生します:

- 親ディレクトリを持たないディレクトリを作成する

__パラメータ:__

- __path__ - 作成または取得するディレクトリのパス(絶対または相対パス) _(DOMString)_
- __options__ - ディレクトリが作成されたかどうかを確かめるためのオプション  _(Flags)_
- __successCallback__ - 'DirectoryEntry'オブジェクトを引数に呼び出される成功時のコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出される失敗時のコールバック関数 _(Function)_

__使用例__
	
    function success(parent) {
        console.log("親ディレクトリ名: " + parent.name);
    }

    function fail(error) {
        alert("ディレクトリの作成に失敗しました: " + error.code);
    }

    // ディレクトリを取得、または作成(存在していない場合)
    entry.getDirectory("newDir", {create: true, exclusive: false}, success, fail);	


getFile
-------

ファイルを作成または取得します。以下の処理を行うとエラーが発生します:

- 親ディレクトリを持たないファイルを作成する

__パラメータ:__

- __path__ - 作成または取得するファイルのパス(絶対または相対パス) _(DOMString)_
- __options__ - ファイルが作成されたかどうかを確かめるためのオプション  _(Flags)_
- __successCallback__ - 'FileEntry'オブジェクトを引数に呼び出される成功時のコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出される失敗時のコールバック関数 _(Function)_

__使用例__
	
    function success(parent) {
        console.log("親ディレクトリ名: " + parent.name);
    }

    function fail(error) {
        alert("ファイルの取得に失敗しました: " + error.code);
    }

    // ファイルを取得、または作成(存在していない場合)
    entry.getFile("newFile.txt", {create: true, exclusive: false}, success, fail);	


removeRecursively
-----------------

ディレクトリをその中身ごと削除します。 なんらかのエラーが発生した場合、ディレクトリ内のコンテンツは削除されない可能性があります。(例:削除できないファイルを含むディレクトリを削除しようとした場合)以下の処理を行うとエラーが発生します:

- ファイルシステムのルートディレクトリを削除する

__パラメータ:__

- __successCallback__ - ディレクトリの削除に成功した際に呼び出されるコールバック関数 _(Function)_
- __errorCallback__ - 'FileError'オブジェクトを引数に呼び出される失敗時のコールバック関数 _(Function)_

__使用例__
	
    function success(parent) {
        console.log("ディレクトリの削除に成功しました。");
    }

    function fail(error) {
        alert("ディレクトリとそのコンテンツの削除に失敗しました: " + error.code);
    }

    // ディレクトリとその中身を削除
    entry.removeRecursively(success, fail);	

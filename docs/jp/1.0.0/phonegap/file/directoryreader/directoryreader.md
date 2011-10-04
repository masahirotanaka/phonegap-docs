DirectoryReader
===============

An object that lists files and directories in a directory.  Defined in the [Directories and Systems](http://www.w3.org/TR/file-system-api/) specification.
あるディレクトリ内のファイルやフォルダを表示させるためのオブジェクトです。[W3C Directories and Systems](http://www.w3.org/TR/file-system-api/) に批准しています。


メソッド
-------

- __readEntries__: ディレクトリ内のエントリを読み込みます。


サポートされているプラットフォーム
--------------------------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

readEntries
-----------

ディレクトリ内のエントリを読み込みます。

__パラメータ:__

- __successCallback__ - 読み込み成功時のコールバック関数。'FileEntry'オブジェクトと'DirectoryEntry'オブジェクトの配列が渡されます。 _(Function)_
- __errorCallback__ - 読み込み失敗時のコールバック関数。'FileError'オブジェクトが渡されます。 _(Function)_

__使用例__
	
    function success(entries) {
        var i;
        for (i=0; i<entries.length; i++) {
            console.log(entries[i].name);
        }
    }

    function fail(error) {
        alert("ディレクトリ内のコンテンツの読み込みに失敗しました: " + error.code);
    }

    //　リーダーを定義
    var directoryReader = dirEntry.createReader();

    // ディレクトリ内のエントリを取得
    directoryReader.readEntries(success,fail);

Metadata
==========

このオブジェクトはファイルやディレクトリの状態を表すプロパティを保持しています。

プロパティ
----------

- __modificationTime:__ This is the time at which the file or directory was last modified. _(Date)_

詳細
-------

 `Metadata` オブジェクトはファイルやフォルダの状態に関する情報を格納しています。Metadataオブジェクトのインスタンスは `DirectoryEntry` オブジェクトか `FileEntry` オブジェクトの __getMetadata__  メソッドから取得します。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

使用例
-------------

	function win(metadata) {
		console.log("Last Modified: " + metadata.modificationTime);
	}
	
	// このエントリのmetaddataオブジェクトを取得
	entry.getMetadata(win, null);

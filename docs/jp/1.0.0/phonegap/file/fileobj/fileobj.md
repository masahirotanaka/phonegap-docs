File
====

このオブジェクトはファイルのプロパティを格納しています。

プロパティ
----------

- __name:__ ファイル名 _(DOMString)_
- __fullPath:__ ファイル名を含む、ファイルへの絶対パス _(DOMString)_
- __type:__ ファイルのmimeタイプ _(DOMString)_
- __lastModifiedDate:__ ファイルの最終更新日 _(Date)_
- __size:__ ファイルのサイズ _(long)_

詳細
-------

`File`オブジェクトはファイルのプロパティを格納しています。このオブジェクトは `FileEntry`オブジェクトの __file__ メソッドの成功時のコールバック関数の引数に渡されます。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

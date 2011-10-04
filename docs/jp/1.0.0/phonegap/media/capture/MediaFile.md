MediaFile
=========

> メディアファイルの情報をカプセル化したオブジェクトです。

プロパティ
----------

- __name:__ ファイル名(パスは含まない) (DOMString)
- __fullPath:__ フルパス(ファイル名を含む) (DOMString)
- __type:__ MIMEタイプ (DOMString)
- __lastModifiedDate:__ ファイルの最終更新日時 (Date)
- __size:__ ファイルのバイト数 (Number)

メソッド
-------

- __MediaFile.getFormatData:__ メディアファイルのフォーマット情報を取得します。

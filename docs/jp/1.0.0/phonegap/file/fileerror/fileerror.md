FileError
========

'FileError'オブジェクトはFile API関連メソッドのエラー発生時に生成されます。

プロパティ
----------

- __code:__ 下記のいずれかの定数を保持する

Constants
---------

- `FileError.NOT_FOUND_ERR`
- `FileError.SECURITY_ERR`
- `FileError.ABORT_ERR`
- `FileError.NOT_READABLE_ERR`
- `FileError.ENCODING_ERR`
- `FileError.NO_MODIFICATION_ALLOWED_ERR`
- `FileError.INVALID_STATE_ERR`
- `FileError.SYNTAX_ERR`
- `FileError.INVALID_MODIFICATION_ERR`
- `FileError.QUOTA_EXCEEDED_ERR`
- `FileError.TYPE_MISMATCH_ERR`
- `FileError.PATH_EXISTS_ERR`

概要
-----------

 `FileError`オブジェクトはFile API関連メソッドのエラーコールバックに渡される唯一のパラメータです。

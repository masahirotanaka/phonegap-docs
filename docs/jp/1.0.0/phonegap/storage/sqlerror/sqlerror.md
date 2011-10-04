SQLError
========

 `SQLError` はデータベース操作中のエラー発生時に投げられるオブジェクトです。

プロパティ
----------

- __code:__ 下記のエラーコードのうちの一つが格納されます。
- __message:__ エラーの概要

定数
---------

- `SQLError.UNKNOWN_ERR`
- `SQLError.DATABASE_ERR`
- `SQLError.VERSION_ERR`
- `SQLError.TOO_LARGE_ERR`
- `SQLError.QUOTA_ERR`
- `SQLError.SYNTAX_ERR`
- `SQLError.CONSTRAINT_ERR`
- `SQLError.TIMEOUT_ERR`

概要
-----------

 `SQLError` はデータベース操作中のエラー発生時に投げられるオブジェクトです。


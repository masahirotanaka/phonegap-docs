PositionError
================

位置情報の取得に失敗した際には `PositionError` オブジェクトが失敗時のコールバック関数に渡されます。

プロパティ
----------

- __code:__ 下記のうちの一つのエラーコード
- __message:__ エラーの内容

定数
---------

- `PositionError.PERMISSION_DENIED`
- `PositionError.POSITION_UNAVAILABLE`
- `PositionError.TIMEOUT`

概要
-----------

位置情報の取得に失敗した場合、 `PositionError` は `geolocationError` コールバックに渡されます。




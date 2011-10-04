Storage
==========

> デバイスのローカルデータベースを扱うためのオブジェクトです。

このAPIは [W3C Web SQL Database Specification](http://dev.w3.org/html5/webdatabase/) と [W3C Web Storage API Specification](http://dev.w3.org/html5/webstorage/) をもとに設計されています。既に上記の仕様を満たしているデバイスに関しては、備え付けのデータベースサポート機能が用いられます。 備え付けのデータベースポートを持たないデバイスに関してはPhoneGapの実装が用いられます。

メソッド
-------

- openDatabase

引数
---------

- name
- version
- display_name
- size

オブジェクト
--------------

- Database
- SQLTransaction
- SQLResultSet
- SQLResultSetList
- SQLError
- localStorage

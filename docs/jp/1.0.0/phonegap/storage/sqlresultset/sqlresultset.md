SQLResultSet
=======

SQLTransactionメソッドのexecuteSqlメソッドが呼ばれるときに SQLResultSetとともにコールバック関数を呼び出します。


プロパティ
-------

- __insertId__: SQL命令文によりデータベースに挿入された行のIDです。
- __rowAffected__: SQL命令文によって変更された行の数です。命令文がデータベースに変更を加えない場合は0を返します。 
- __rows__: 返された行の情報を保持するSQLResultSetRowListオブジェクトです。行が一つも返されていない場合はこのオブジェクトは空になります。

詳細
-------

SQLTransactionのexecuteSqlメソッドが呼び出されると、コールバックがSQLResultSetを引数に呼び出されます。SQLResultSetオブジェクトは insertID, rowAffected, そして SQLResultSetList という3つのプロパティを持っています。insertIdはSQL INSERT文が成功した行番号を返します。SQL分がINSERTではなかった場合、insertIdはセットされません。rowAffectedはSELECT文に対しては常に0を取ります。INSERT/UPDATE文に対しては修正された行の数を返します。 SQLResultSetListオブジェクトはSQLのSELECT文によって返されたデータを保持しています。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 6.0以上)
- iPhone

Execute SQL 使用例
------------------

	function queryDB(tx) {
		tx.executeSql('SELECT * FROM DEMO', [], querySuccess, errorCB);
	}

	function querySuccess(tx, results) {
		// 行がINSSERTされていないため、このクエリは空になります。
		console.log("Insert ID = " + results.insertId);
		// SELECT文を実行しているため、0を返します。
		console.log("Rows Affected = " + results.rowAffected);
		// SELECT文が変更を加えた行の数を返します。
		console.log("Insert ID = " + results.rows.length);
	}
	
	function errorCB(err) {
		alert("SQLエラーが発生しました: "+err.code);
	}
	
	var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
	db.transaction(queryDB, errorCB);

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Contact Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

		function populateDB(tx) {
			tx.executeSql('DROP TABLE IF EXISTS DEMO');
			tx.executeSql('CREATE TABLE IF NOT EXISTS DEMO (id unique, data)');
			tx.executeSql('INSERT INTO DEMO (id, data) VALUES (1, "First row")');
			tx.executeSql('INSERT INTO DEMO (id, data) VALUES (2, "Second row")');
		}

		// データベースへ問い合わせ
		//
		function queryDB(tx) {
			tx.executeSql('SELECT * FROM DEMO', [], querySuccess, errorCB);
		}

		// クエリ成功時のコールバック
		//
		function querySuccess(tx, results) {
			// this will be empty since no rows were inserted.
			console.log("Insert ID = " + results.insertId);
			// this will be 0 since it is a select statement
			console.log("Rows Affected = " + results.rowAffected);
			// the number of rows returned by the select statement
			console.log("Insert ID = " + results.rows.length);
		}

		// トランザクション失敗時のコールバック
		//
		function errorCB(err) {
			console.log("Error processing SQL: "+err.code);
		}

		// トランザクション成功時のコールバック
		//
		function successCB() {
			var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
			db.transaction(queryDB, errorCB);
		}

		// PhoneGapのロードが完了
		//
		function onDeviceReady() {
			var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
			db.transaction(populateDB, errorCB, successCB);
		}
	
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Database</p>
      </body>
    </html>

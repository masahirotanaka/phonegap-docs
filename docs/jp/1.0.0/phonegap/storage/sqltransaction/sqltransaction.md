SQLTransaction
==============

データベースに対してSQL文を実行するメソッドを持つオブジェクトです。

メソッド
-------

- __executeSql__: executes a SQL statement

詳細
-------

DatabaseオブジェクトのTransactionメソッドを呼ぶ際、それに対応するコールバック関数がSQLTransactionオブジェクトを引数に呼び出されます。データベーストランザクションを作成するには、executeSqlメソッドを複数会使用してください。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 6.0以上)
- iPhone

Execute SQL使用例
------------------

	function populateDB(tx) {
		 tx.executeSql('DROP TABLE IF EXISTS DEMO');
		 tx.executeSql('CREATE TABLE IF NOT EXISTS DEMO (id unique, data)');
		 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (1, "First row")');
		 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (2, "Second row")');
	}
	
	function errorCB(err) {
		alert("Error processing SQL: "+err);
	}
	
	function successCB() {
		alert("success!");
	}
	
	var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
	db.transaction(populateDB, errorCB, successCB);

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

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
			var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
			db.transaction(populateDB, errorCB, successCB);
        }
		
		function populateDB(tx) {
			 tx.executeSql('DROP TABLE IF EXISTS DEMO');
			 tx.executeSql('CREATE TABLE IF NOT EXISTS DEMO (id unique, data)');
			 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (1, "First row")');
			 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (2, "Second row")');
		}
		
		// トランザクション失敗時のコールバック
		//
		function errorCB(err) {
			alert("Error processing SQL: "+err);
		}
		
		// トランザクション成功時のコールバック
		//
		function successCB() {
			alert("成功しました。");
		}
	
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>SQLTransaction</p>
      </body>
    </html>

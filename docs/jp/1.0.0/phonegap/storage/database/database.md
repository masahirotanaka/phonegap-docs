Database
=======

データベースの処理を扱うオブジェクトです。

メソッド
-------

- __transaction__: データベース処理を実行します。
- __changeVersion__: スクリプトがデータベースのバージョンを自動的に確認し、スキーマのアップデートと同時にバージョンを変更します。

詳細
-------

'Database'オブジェクトは `window.openDatabase()` メソッドにより生成されます。

サポートされているプラットフォーム
--------------------------------------

- Android
- BlackBerry WebWorks (OS 6.0以上)
- iPhone

Transactionの使用例
------------------
	function populateDB(tx) {
		 tx.executeSql('DROP TABLE IF EXISTS DEMO');
		 tx.executeSql('CREATE TABLE IF NOT EXISTS DEMO (id unique, data)');
		 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (1, "First row")');
		 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (2, "Second row")');
	}
	
	function errorCB(err) {
		alert("SQLエラーが発生しました: "+err.code);
	}
	
	function successCB() {
		alert("成功しました。");
	}
	
	var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
	db.transaction(populateDB, errorCB, successCB);

Change Versionの使用例
-------------------

	var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
	db.changeVersion("1.0", "1.1");

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
		
		// 失敗時のコールバック
		//
		function errorCB(tx, err) {
			alert("Error processing SQL: "+err);
		}
		
		// 成功時のコールバック
		//
		function successCB() {
			alert("success!");
		}
	
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Database</p>
      </body>
    </html>

Android 1.Xに関する注意点
------------------

- __changeVersion:__ このメソッドはAndroid 1.X 

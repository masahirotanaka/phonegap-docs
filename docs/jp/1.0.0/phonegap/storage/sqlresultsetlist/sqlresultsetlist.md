SQLResultSetList
=======

SQL真真真真真真真row真真�'SQLResultSet'真真真真�


真真�
--------------

- __length__: SQL真真真真真�row真

真真
--------------

- __item__: 真真真�JavaScript真真真真真真真

真
-------

SQLResultSetList�SQL select真真真真真真真真真真真真真真真select真真真真真真�length真真真真真真真真真真真真真真真真真�item真真真真真真真 `item` 真真�JavaSript真真真真真真真真真真真真真真select真真真真真真真真真真真真真真真真真真

真真真真真真真真�
-------------------

- Android
- BlackBerry WebWorks (OS 6.0真)
- iPhone

Execute SQL真真
------------------

	function queryDB(tx) {
		tx.executeSql('SELECT * FROM DEMO', [], querySuccess, errorCB);
	}

	function querySuccess(tx, results) {
		var len = results.rows.length;
	���	console.log("DEMO table: " + len + " rows found.");
	���	for (var i=0; i<len; i++){
	����	console.log("Row = " + i + " ID = " + results.rows.item(i).id + " Data =  " + results.rows.item(i).data);
		}
	}
	
	function errorCB(err) {
		alert("Error processing SQL: "+err.code);
	}
	
	var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
	db.transaction(queryDB, errorCB);

真真真
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Contact Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap真真真�
        //
        document.addEventListener("deviceready", onDeviceReady, false);

		// Populate the database 
		//
		function populateDB(tx) {
			tx.executeSql('DROP TABLE IF EXISTS DEMO');
			tx.executeSql('CREATE TABLE IF NOT EXISTS DEMO (id unique, data)');
			tx.executeSql('INSERT INTO DEMO (id, data) VALUES (1, "First row")');
			tx.executeSql('INSERT INTO DEMO (id, data) VALUES (2, "Second row")');
		}

		// 真真真真真真真真
		//
		function queryDB(tx) {
			tx.executeSql('SELECT * FROM DEMO', [], querySuccess, errorCB);
		}

		// 真真真真真
		//
		function querySuccess(tx, results) {
			var len = results.rows.length;
			console.log("DEMO table: " + len + " rows found.");
			for (var i=0; i<len; i++){
				console.log("Row = " + i + " ID = " + results.rows.item(i).id + " Data =  " + results.rows.item(i).data);
			}
		}

		// 真真真真真真�
		//
		function errorCB(err) {
			console.log("Error processing SQL: "+err.code);
		}

		// 真真真真真真真真真
		//
		function successCB() {
			var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
			db.transaction(queryDB, errorCB);
		}

		// PhoneGap真真真�
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

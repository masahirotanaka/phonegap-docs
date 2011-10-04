SQLResultSetList
=======

SQL¿¿¿¿¿¿¿¿¿¿¿¿¿¿row¿¿¿¿¿'SQLResultSet'¿¿¿¿¿¿¿¿¿


¿¿¿¿¿
--------------

- __length__: SQL¿¿¿¿¿¿¿¿¿¿¿row¿¿

¿¿¿¿
--------------

- __item__: ¿¿¿¿¿¿¿JavaScript¿¿¿¿¿¿¿¿¿¿¿¿¿¿

¿¿
-------

SQLResultSetList¿SQL select¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿select¿¿¿¿¿¿¿¿¿¿¿¿¿length¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿item¿¿¿¿¿¿¿¿¿¿¿¿¿¿ `item` ¿¿¿¿¿JavaSript¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿select¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿

¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿
-------------------

- Android
- BlackBerry WebWorks (OS 6.0¿¿)
- iPhone

Execute SQL¿¿¿¿
------------------

	function queryDB(tx) {
		tx.executeSql('SELECT * FROM DEMO', [], querySuccess, errorCB);
	}

	function querySuccess(tx, results) {
		var len = results.rows.length;
	   	console.log("DEMO table: " + len + " rows found.");
	   	for (var i=0; i<len; i++){
	    	console.log("Row = " + i + " ID = " + results.rows.item(i).id + " Data =  " + results.rows.item(i).data);
		}
	}
	
	function errorCB(err) {
		alert("Error processing SQL: "+err.code);
	}
	
	var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
	db.transaction(queryDB, errorCB);

¿¿¿¿¿¿
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Contact Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap¿¿¿¿¿¿¿
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

		// ¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿
		//
		function queryDB(tx) {
			tx.executeSql('SELECT * FROM DEMO', [], querySuccess, errorCB);
		}

		// ¿¿¿¿¿¿¿¿¿¿
		//
		function querySuccess(tx, results) {
			var len = results.rows.length;
			console.log("DEMO table: " + len + " rows found.");
			for (var i=0; i<len; i++){
				console.log("Row = " + i + " ID = " + results.rows.item(i).id + " Data =  " + results.rows.item(i).data);
			}
		}

		// ¿¿¿¿¿¿¿¿¿¿¿¿¿
		//
		function errorCB(err) {
			console.log("Error processing SQL: "+err.code);
		}

		// ¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿¿
		//
		function successCB() {
			var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
			db.transaction(queryDB, errorCB);
		}

		// PhoneGap¿¿¿¿¿¿¿
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

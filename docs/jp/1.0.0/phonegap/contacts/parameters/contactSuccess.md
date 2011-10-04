contactSuccess
==============


連絡先関連の成功時のコールバック関数です。 `contacts.find` メソッドでは、このメソッドによって返される連絡先の配列が引数に渡されます。

    function(contacts) {
        // 成功時の処理を記述
    }

パラメータ
------------

- __contacts:__ `contact.find` メソッドの検索でマッチした連絡先の配列 (`Contact`)

使用例
-------

    function contactSuccess(contacts) {
		for (var i=0; i<contacts.length; i++) {
			console.log("Display Name = " + contacts[i].displayName;
    }

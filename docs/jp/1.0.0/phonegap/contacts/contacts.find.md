contacts.find
=============

アドレス帳のデータベースにクエリを投げ、 クエリで指定したフィールドを持つ `Contact` オブジェクトを返します。

    navigator.contacts.find(contactFields, contactSuccess, contactError, contactFindOptions);

概要
-----------

 `contacts.find` はデバイスのアドレス帳データベースに問い合わせを行い、 `Contact` オブジェクトの配列を返します。 返り値のオブジェクト(の配列)は __contactSuccess__ パラメータで指定された `contactSuccess` コールバック関数に渡されます。

このメソッドを使うためには、 __contactFields__ パラメータに検索条件を設定します。ここで指定したフィールドだけが、 __contactSuccess__ コールバック関数に渡されるオブジェクトのプロパティとしてアクセスができるようになります。 空の __contactFields__ パラメータが `contacts.find` に渡された場合は、 `id` プロパティのみを持つ `Contact` オブジェクトの配列が返されます。
 __contactFields__ の値に["*"]を指定すると、全ての連絡先を取得することができます。

データベースへの問い合わせのフィルタリングをしたい場合 __contactFindOptions.filter__ に文字列を入れて指定します。このプロパティが指定されている場合(case-insensitive)、__contactFields__ で指定されたフィールドに部分的にマッチする連絡先を取得できます。

パラメータ
----------

- __contactFields:__ 検索条件として使うための連絡先のフィールド。ここで指定したフィールドのみがこのメソッドで生成される `Contact` オブジェクトのプロパティとなる。 _(DOMString[])_ [Required]
- __contactSuccess:__ アドレス帳データベースから連絡先の取得に成功した際に呼び出されるコールバック関数 [Required]
- __contactError:__ エラー時のコールバック関数 [Optional]
- __contactFindOptions:__ 検索フィルタ用のオプション [Optional]

サポートされているプラットフォーム
--------------------------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

使用例
-------------

    function onSuccess(contacts) {
        alert(contacts.length + '件の連絡先が見つかりました。');
    };

    function onError(contactError) {
        alert('エラーが発生しました。');
    };

    // 'Bob'をネームフィールドに持つ全ての連絡先を検索
    var options = new ContactFindOptions();
	options.filter="Bob"; 
	var fields = ["displayName", "name"];
    navigator.contacts.find(fields, onSuccess, onError, options);

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
		    // 'Bob'をネームフィールドに持つ全ての連絡先を検索
		    var options = new ContactFindOptions();
			options.filter="Bob"; 
			var fields = ["displayName", "name"];
		    navigator.contacts.find(fields, onSuccess, onError, options);
        }
    
        // 成功時の処理: 連絡先を取得
        //
        function onSuccess(contacts) {
			for (var i=0; i<contacts.length; i++) {
				console.log("Display Name = " + contacts[i].displayName);
			}
        }
    
        // 失敗時の処理: 連絡先の取得に失敗したことをアラート
        //
        function onError(contactError) {
            alert('エラーが発生しました。');
        }

        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Find Contacts</p>
      </body>
    </html>
    


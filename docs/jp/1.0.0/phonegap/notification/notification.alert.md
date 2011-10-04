notification.alert
==================

カスタムのアラートボックスを表示します。

    navigator.notification.alert(message, alertCallback, [title], [buttonName])

- __message:__ ダイアログのメッセージ (`String`)
- __alertCallback:__ ダイアログが閉じられた際に呼ばれるコールバック関数 (`Function`)
- __title:__ ダイアログのタイトル (`String`) (Optional, デフォルト: "Alert")
- __buttonName:__ ボトムネーム (`String`) (Optional, デフォルト: "OK")
    
概要
-----------

PhoneGapは多くの場合ネイティブのダイアログボックスを使用しますが、いくつかのプラットフォームではブラウザの'alert'関数を使用します。(この場合はカスタマイズ性が落ちます)

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry (OS 4.6)
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    // Android / BlackBerry WebWorks (OS 5.0以上) / iPhone
    //
    function alertDismissed() {
        // 何らかの処理を記述
    }

    navigator.notification.alert(
        'You are the winner!',  // メッセージ
        alertDismissed,         // コールバック
        'Game Over',            // タイトル
        'Done'                  // ボトムネーム
    );

    // BlackBerry (OS 4.6) / webOS
    //
    navigator.notification.alert('You are the winner!');
        
詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Notification Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
            
        }
    
        // アラートボックスが閉じられた場合の処理
	    function alertDismissed() {
	        // 何らかの処理を記述
	    }

        // カスタムアラートを表示
        //
        function showAlert() {
		    navigator.notification.alert(
		        'You are the winner!',  // メッセージ
		        alertDismissed,         // コールバック
		        'Game Over',            // タイトル
		        'Done'                  // ボトムネーム
		    );
        }
    
        </script>
      </head>
      <body>
        <p><a href="#" onclick="showAlert(); return false;">Show Alert</a></p>
      </body>
    </html>

notification.vibrate
====================

指定された秒数バイブレーションを作動させます。

    navigator.notification.vibrate(milliseconds)

- __time:__ ミリ秒単位で指定するバイブレーションの作動時間 (`Number`)

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry (OS 4.6)
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    // 2.5秒間バイブレーションを作動
    //
    navigator.notification.vibrate(2500);

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
    
        function showAlert() {
		    navigator.notification.alert(
		        'You are the winner!',  // メッセージ
		        'Game Over',            // タイトル
		        'Done'                  // ボトムネーム
		    );
        }
    
        // ビープを三回鳴らす。
        //
        function playBeep() {
            navigator.notification.beep(3);
        }
    
        // 2秒間バイブレーションを作動
        //
        function vibrate() {
            navigator.notification.vibrate(2000);
        }

        </script>
      </head>
      <body>
        <p><a href="#" onclick="showAlert(); return false;">Show Alert</a></p>
        <p><a href="#" onclick="playBeep(); return false;">Play Beep</a></p>
        <p><a href="#" onclick="vibrate(); return false;">Vibrate</a></p>
      </body>
    </html>

iPhoneに関する注意点
-------------

- __time:__ を無視し、デフォルトで設定されている間バイブレーションを作動させます。

        navigator.notification.vibrate();
        navigator.notification.vibrate(2500);   // 2500は無視されます。

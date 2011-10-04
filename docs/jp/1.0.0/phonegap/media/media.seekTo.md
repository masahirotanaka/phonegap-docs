media.seekTo
========================

オーディオの再生位置をセットします。

    media.seekTo(milliseconds);

パラメータ
----------

- __milliseconds__:　ミリ秒単位で指定する再生位置


概要
-----------

 `media.seekTo` はMediaオブジェクトの現在の再生位置を更新する非同期関数です。このメソッドはMediaオブジェクトの __position__ パラメータも同時に更新します。

サポートされているプラットフォーム
-------------------

- Android
- iOS
    
使用例
-------------

        var my_media = new Media(src, onSuccess, onError);
		my_media.play();
        // 5秒後に再生位置を00:10にセット
        setTimeout(function() {
            my_media.seekTo(10000);
        }, 5000);


詳細な使用例
------------

        <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
                      "http://www.w3.org/TR/html4/strict.dtd">
        <html>
          <head>
            <title>Media Example</title>
        
            <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
            <script type="text/javascript" charset="utf-8">
        
            // PhoneGapのロードを待機
            //
            document.addEventListener("deviceready", onDeviceReady, false);
        
            // PhoneGapのロードが完了
            //
            function onDeviceReady() {
                playAudio("http://audio.ibeat.org/content/p1rj1s/p1rj1s_-_rockGuitar.mp3");
            }
        
            var my_media = null;
            var mediaTimer = null;
        
            function playAudio(src) {
                // srcからMediaオブジェクトを生成
                my_media = new Media(src, onSuccess, onError);
        
                // オーディオを再生
                my_media.play();
                // 毎秒再生位置を更新
        		mediaTimer = setInterval(function() {
            		// メディアの再生位置を取得
           			my_media.getCurrentPosition(
                		// 成功時のコールバック
                		function(position) {
                    		if (position > -1) {
                        		setAudioPosition(position + " sec");
                    		}
                		},
                		// 失敗時のコールバック
                		function(e) {
                    		console.log("Error getting pos=" + e);
                		}
            		);
        		}, 1000);
        		// 5秒後に再生位置を00:10にセット
        		setTimeout(function() {
            		my_media.seekTo(10000);
           		}, 5000);
     		}
        
            // オーディオを停止
            // 
            function stopAudio() {
                if (my_media) {
                    my_media.stop();
                }
                clearInterval(mediaTimer);
                mediaTimer = null;
            }
        
            // 成功時のコールバック
            //
            function onSuccess() {
                console.log("playAudio():Audio Success");
            }
        
            // 失敗時のコールバック
            //
            function onError(error) {
                alert('code: '    + error.code    + '\n' + 
                      'message: ' + error.message + '\n');
            }
        
            // オーディオの再生位置をセット
            // 
            function setAudioPosition(position) {
                document.getElementById('audio_position').innerHTML = position;
            }
        
            </script>
          </head>
          <body>
            <a href="#" class="btn large" onclick="playAudio('http://audio.ibeat.org/content/p1rj1s/p1rj1s_-_rockGuitar.mp3');">Play Audio</a>
            <a href="#" class="btn large" onclick="stopAudio();">Stop Playing Audio</a>
            <p id="audio_position"></p>
          </body>
        </html>

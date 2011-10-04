media.pause
===========

オーディオの再生を一時停止します。

    media.pause();


概要
-----------

 `media.pause` はオーディオの再生を一時停止させる同期関数です。

サポートされているプラットフォーム
-------------------

- Android
- iOS
    
使用例
-------------

    function playAudio(url) {
        // urlで指定したオーディオファイルを再生します
        var my_media = new Media(url,
            // 成功時のコールバック関数
            function() {
                console.log("playAudio():Audio Success");
            },
            // エラー時のコールバック関数
            function(err) {
                console.log("playAudio():Audio Error: "+err);
        });

        // オーディオを再生
        my_media.play();

        // 10秒後に一時停止
        setTimeout(function() {
            media.pause();
        }, 10000);        
    }


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
                // srcからMediaオブジェクトを再生
                my_media = new Media(src, onSuccess, onError);
        
                // オーディオを再生
                my_media.play();
        
                // 毎秒'my_media'の再生位置を更新
                if (mediaTimer == null) {
                    mediaTimer = setInterval(function() {
                        // 'my_media'の再生位置を取得
                        my_media.getCurrentPosition(
                            // 成功時のコールバック
                            function(position) {
                                if (position > -1) {
                                    setAudioPosition((position) + " sec");
                                }
                            },
                            // 失敗時のコールバック
                            function(e) {
                                console.log("Error getting pos=" + e);
                                setAudioPosition("Error: " + e);
                            }
                        );
                    }, 1000);
                }
            }
        
            // オーディオの再生を一時停止
            // 
            function pauseAudio() {
                if (my_media) {
                    my_media.pause();
                }
            }
        
            // オーディオの再生を停止
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
            <a href="#" class="btn large" onclick="pauseAudio();">Pause Playing Audio</a>
            <a href="#" class="btn large" onclick="stopAudio();">Stop Playing Audio</a>
            <p id="audio_position"></p>
          </body>
        </html>

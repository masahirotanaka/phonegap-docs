CaptureErrorCB
==============

> メディアキャプチャ中にエラーが発生した場合に呼び出されるコールバック関数です。

    function captureError( CaptureError error ) { ... };

概要
-----------

この関数はビジー状態のキャプチャ操作を実行したり、ユーザがキャプチャ操作を完了する前にそれをキャンセルしたり、その他のエラーがキャプチャ操作中に発生した際に呼び出されるコールバック関数です。
この関数は詳細なエラーの内容を保持する'CaptureError'オブジェクトが引数に渡された状態で呼び出されます。


使用例
-------------

    // エラー発生時のコールバック
    var captureError = function(error) {
        navigator.notification.alert('Error code: ' + error.code, null, 'Capture Error');
    };

compassSuccess
==============

方角に関するPhoneGapメソッドの成功時に呼び出されるコールバック関数です。

    function(heading) {
        // 成功時の処理
    }

パラメータ
----------

- __heading:__ `compassSuccess` に渡される0から359.99までの方角を表す数値 _(Number)_

使用例
-------

    function onSuccess(heading) {
        alert('方角: ' + heading);
    };

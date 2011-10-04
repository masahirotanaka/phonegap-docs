Device
======

> `device` オブジェクトはデバイスのハードウェアとソフトウェアに関する情報を保持しています。

プロパティ
----------

- device.name
- device.phonegap
- device.platform
- device.uuid
- device.version

変数のスコープ
--------------

`device` は `window` オブジェクトにアサインされているため、自動的にグローバルスコープになります。

    // これらは同じ `device` を指します。
    //
    var phoneName = window.device.name;
    var phoneName = device.name;

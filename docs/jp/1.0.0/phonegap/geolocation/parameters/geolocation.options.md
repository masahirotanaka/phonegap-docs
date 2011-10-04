geolocationOptions
==================

Geolocationに関するメソッドをカスタマイズするためのオプションをs指定するオブジェクトです。

    { maximumAge: 3000, timeout: 5000, enableHighAccuracy: true };

オプション
--------------

- __frequency:__ 現在位置情報を取得するミリ秒単位の頻度。(このオプションはW3C仕様には含まれないため、将来は廃止されます。代わりに'maximumAge'オプションを使用してください。)  _(Number)_ (Default: 10000)
- __enableHighAccuracy:__ アプリケーションがより精度の高い位置情報を取得するためのヒントを提供します。 _(Boolean)_
- __timeout:__  `geolocation.getCurrentPosition` や `geolocation.watchPosition` が `geolocaationSuccess` コールバックを呼び出すまで待機する最大ミリ秒数。 _(Number)_
- __maximumAge:__ ミリ秒単位で指定する。この秒数の間に取得した位置情報をキャッシュする。 _(Number)_

Androidに関する注意点
--------------

Android 2.x のエミュレータは'enableHighAccuracy'オプションが'true'に設定されていない限り位置情報の結果を返しません。

    { enableHighAccuracy: true }


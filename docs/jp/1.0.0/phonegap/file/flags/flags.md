Flags
=====

このオブジェクトは `DirectoryEntry` オブジェクトの __getFile__, __getDirectory__ メソッドの引数として渡すことで下記のオプションを設定することができます。

プロパティ
----------

- __create:__ このプロパティを'true'に設定することでファイルが存在しない場合は自動的に作成するオプションを設定できます。デフォルトは'false' _(boolean)_ 
- __exclusive:__ このプロパティは __create__ と共に指定することでターゲットとなるパスが既に存在する場合にファイル/ディレクトリの生成を中止することができます。 __exclusive__ 単体での指定は効果がなく、デフォルトは'false' _(boolean)_ 

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

使用例
-------------

    // "data"ディレクトリを取得。もし存在しない場合は作成する。
    dataDir = fileSystem.root.getDirectory("data", {create: true});

    // "lockfile.txt"を作成はそのファイルが存在しない場合のみに行われる
    lockFile = dataDir.getFile("lockfile.txt", {create: true, exclusive: true});

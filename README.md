## サブモジュールのテストプロジェクト

https://github.com/ms2sato/submodule_design

を、/vendor/submodule_design に取り込む形で作成されています。

### cloneの方法

```
git clone git@github.com:ms2sato/submodule_parent.git
```

するだけだと、サブモジュールが取り込まれていません。続けて下記をやります。

```
git submodule update -i
```

これで、 /vendor/submodule_design内にファイルができるはずです。
このファイルはassetの仕組みで読み込むように設定されています。

参考
http://qiita.com/kinpira/items/3309eb2e5a9a422199e9

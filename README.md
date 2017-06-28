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
このファイルはassetの仕組みで読み込むように設定されています（ https://github.com/ms2sato/submodule_parent/blob/master/config/environments/development.rb#L38-L40 ）


http://localhost:3000/samples

にアクセスすると、外部のデザインのリポジトリで作ったcssが反映されます。

参考
http://qiita.com/kinpira/items/3309eb2e5a9a422199e9

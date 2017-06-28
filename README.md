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

にアクセスすると、外部のデザインのリポジトリで作ったcssが反映されます。背景が黄色だったり、文字が赤だったりね！

### デザイン側の更新が起きた場合

まず、サブモジュール内でpullして中身を更新します。

```
$ cd ./vendor/submodule_design
$ git pull origin master
From github.com:ms2sato/submodule_design
 * branch            master     -> FETCH_HEAD
Updating c2241d5..bd4a73e
Fast-forward
 README.md | 2 ++
 1 file changed, 2 insertions(+)
 create mode 100644 README.md 
```

更新すると差分が発生するので、親の方でコミットします。
イメージとしては、サブモジュール側のリビジョン番号を親側が持っているので、それを更新してあげる感じです。

```
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   vendor/submodule_design (new commits)

no changes added to commit (use "git add" and/or "git commit -a")
$ git add .
$ git commit -m "design update"
$ git push origin master
```

参考
https://rcmdnk.com/blog/2013/10/18/computer-git/

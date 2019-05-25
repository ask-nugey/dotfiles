# dotfiles
自分の設定ファイルをgithubにリポジトリを作って、管理する  
参考：<https://qiita.com/okamos/items/7f5461814e8ed8916870>

> dotfiles とは Unix 系 OS で俗に言う設定ファイルのことです。.vimrc や .zshrc など、設定ファイルの多くは隠しファイルとしてファイル名の頭にドットがつくことからそう呼ばれています。  
> [引用元](https://qiita.com/b4b4r07/items/b70178e021bef12cd4a2)

## how to set up
```
git clone https://github.com/yuki-iwase/dotfiles ~/git/.dotfiles
cd ~/git/dotfiles
./setup.sh
```
- 注意点：
  - vscodeをダウンロードしてから行うこと

---

## 作成方法
### 1. ローカルリポジトリを作成
```
mkdir -p ~/git/dotfiles && cd $_
git init
```

### 2. ディレクトリ単位で管理する  
.gitconfigを管理する例：

```
mkdir -p ~/git/dotfiles/git    //①.ディレクトリを作成
mv ~/.gitconfig ~/git/dotfiles/hyper    //②.gitconfigをそこに移動
ln -fs ${HOME}/git/dotfiles/git/.gitconfig ${HOME}/.gitconfig    //③元の場所にシンボリックを貼る
```

[シンボリックについて](https://qiita.com/hashimotoryoh/items/9a675a769244d61c11bb)

### 3. setup.shを作成(自動でシンボリックを作成させる)
```
touch -p ~/git/dotfiles/setup.sh    //ファイル作成
chmod +x setup.sh    //権限を追加
```
.gitconfigを追加する記述例
```HTML:setup.sh
ln -fs ${HOME}/git/dotfiles/git/.gitconfig ${HOME}/.gitconfig
```

### 4. githubでリポジトリを作成して、追加
[githubでのリポジトリ作成方法](https://qiita.com/muneo/items/1321bf8cdb21178a73e2)
```
git remote add origin [URL]
```

### 5. そこにプッシュ
```
git add .
git commit -m "add dotfiles"
git push origin master
```

## メモ
- zshも管理する。そのとき、テーマはどうやればいいのか調べる
- homebrewも追加する

# 0 Gitの設定
***

```sh
git config --global user.name "Tatsuki-Oike"
git config --global user.email "Tatsuki-Oike@example.com"
git config --list
```


# 1 Gitの基礎
***

## 1.1 最初のコミット

```sh
cd ./Documents/youtube/Git # gitのディレクトリに移動
git init # Gitリポジトリとして登録
git add . # 指定したファイルをステージ
git commit -m "開発開始" # コミット
```
    
## 1.2 2回目のコミット
* htmlに文章追加

* コミット
```sh
git add Git.html # 指定したファイルをステージ
git status # ワーキングディレクトリの状態を確認
git diff # 差分を確認
git commit -m "htmlに文章追加" # コミット
git log # コミットのログを確認
git log --oneline # コミットのログを確認
```

## 1.3 チェックアウト
* チェックアウト
```sh
git checkout コミットID # チェックアウト 
git log --oneline --all # コミットのログを確認
```
<br>

* Git.html を更新

## 1.4 リポジトリの消去
```sh
rm -rf .git
```



# 2 ファイルの状態とgitignore
***

## 2.1 ファイルの状態

* ファイルの状態を確認
```sh
cd ./Documents/youtube/Git # gitのディレクトリに移動
git init # Gitリポジトリとして登録
git status # ファイルの状態の確認
git add Git.html # 指定したファイルをステージ
git status #ファイルの状態の確認
git commit -m "test" # コミット
git status # ファイルの状態の確認
```
<br>

* htmlに文章追加

* ファイルの状態を確認
```sh
git status # ファイルの状態の確認
git add Git.html # 指定したファイルをステージ
git status #ファイルの状態の確認
```

## 2.2 gitignoreの利用

* gitignoreに記述
```
.DS_Store
.ipynb_checkpoints
# Git.html は不可
```
<br>

* ファイルの状態を確認
```sh
git status # ファイルの状態の確認
```

## 2.3 リポジトリの消去
```sh
rm -rf .gitignore
rm -rf .git
```

## 2.4 gitignoreの記法
| id |  記号 |  意味  |  例  |
| ---- | ---- | ---- | ---- | 
|1|  *  |  任意  |  *.JPG or IMG\*  |
|2|  !  |  除外  |  *.JPG<br>!sample2.JPG  |
|3|  ?  |  一文字マッチ  |  sample?.JPG |
|4|  []  |  特定の文字マッチ  |  sample[3-7].JPG  |

<br>



# 3 ブランチとマージ
***

## 3.1 最初のコミット
```sh
cd ./Documents/youtube/Git # gitのディレクトリに移動
git init # Gitリポジトリとして登録
git add . # 指定したファイルをステージ
git commit -m "開発開始" # コミット
```

## 3.2 2回目のコミット
* htmlに文章追加

* コミット
```sh
git add . # 指定したファイルをステージ
git commit -m "htmlに文章追加" # コミット
```

## 3.3 3回目のコミット
* htmlに画像追加

* コミット
```sh
git add . # 指定したファイルをステージ
git commit -m "htmlに画像追加" # コミット
git log --oneline # コミットのログを確認
```

## 3.4 ブランチの作成と移動

* ブランチ

```sh
git checkout コミットID # コミット１に移動
git checkout -b css_branch # ブランチを作成して移動
# (git branch ブランチ名, git checkout ブランチ名)
git branch # ブランチの確認
git log --oneline --all # 現在のコミット確認
```

* Git.html を更新

## 3.5 ブランチのコミット
* cssにbackground追加
```css
body{
  background:aliceblue;
}
```
<br>

* コミット
```sh
git add . # 指定したファイルをステージ
git commit -m "cssにbackground追加" # コミット
```

## 3.6 ブランチのコミット2
* cssにmargin追加
```css
body{
  background:aliceblue;
  margin:30px;
}
```
<br>

* コミット

```sh
git add . # 指定したファイルをステージ
git commit -m "cssにmargin追加" # コミット
git log --oneline --all --graph # コミットのログを確認
```

## 3.7 ブランチのマージ
* マージ
```sh
git checkout master # masterに移動
git merge css_branch
git log --oneline --all --graph # コミットのログを確認
```
<br>

* Git.html とstyle.cssを更新

## 3.8 リポジトリのリセット
```sh
rm -rf .git
```

<br>



# 4 Gitの開発フロー
***

## 4.1 最初のコミット
```sh
cd ./Documents/youtube/Git # gitのディレクトリに移動
git init # Gitリポジトリとして登録
git add . # 指定したファイルをステージ
git commit -m "開発開始" # コミット
```

## 4.2 html_branch

* html_branch作成
```sh
git checkout -b html_branch # ブランチを作成して移動
git branch # ブランチの確認
```


* htmlに文章追加


* コミット
```sh
git add . # 指定したファイルをステージ
git commit -m "htmlに文章追加" # コミット
```


* htmlに画像追加


* コミット
```sh
git add . # 指定したファイルをステージ
git commit -m "htmlに画像追加" # コミット
```


* マージ
```sh
git checkout master # masterに移動
git merge --no-ff html_branch # マージ
git log --oneline --graph # gitのログを確認
```


## 4.3 css_branch

* css_branch作成
```sh
git checkout -b css_branch # ブランチを作成して移動
git branch # ブランチの確認
```


* cssにbackground追加
```css
body{
  background:aliceblue;
}
```


* コミット
```sh
git add . # 指定したファイルをステージ
git commit -m "cssにbackground追加" # コミット
```


* cssにmargin追加
```css
body{
  background:aliceblue;
  margin:30px;
}
```


* コミット
```sh
git add . # 指定したファイルをステージ
git commit -m "cssにmargin追加" # コミット
```


* マージ
```sh
git checkout master # masterに移動
git merge --no-ff css_branch # マージ
git log --oneline --graph # gitのログを確認
```


## 4.4 リポジトリのリセット
```sh
rm -rf .git
```



<br>



# 5 GitHubの基礎
***

## 5.1 最初のコミット
```sh
cd ./Documents/youtube/GitHub # GitHubのディレクトリに移動
git init # Gitリポジトリとして登録
git add . # 指定したファイルをステージ
git commit -m "開発開始" # コミット
```

## 5.2 GitHubの設定

* GitHubのアカウント作成
* tokenの作成
* urlのコピー
* tokenのコピー

## 5.3 push
```sh
git remote add origin https://github.com/Tatsuki-Oike/github.git # リモート設定
git push origin master # push
# Username : Tatsuki-Oike
# Password : token
```



# 6 README.md
***

## 6.1 pull
```sh
cd ./Documents/youtube/GitHub # gitのディレクトリに移動
git pull origin master # pull
```

## 6.2 README.md編集

* README.mdを編集

* コミット
```sh
git add . # 指定したファイルをステージ
git commit -m "README.mdを編集" # コミット
```

## 6.3 push
```sh
git remote add origin https://github.com/Tatsuki-Oike/github.git # リモート設定
git push -u origin master # push
```



# 7 GitHubでチーム開発
***

## 7.1 ssh key作成
* ssh key作成 (terminal)
```sh
ssh-keygen -t rsa # ssh key作成
pbcopy < <ssh key path>/id_rsa.pub # ssh key コピー
```


* ssh key作成 (GitHub)


* ssh key確認
```sh
ssh -T git@github.com # 確認
```


## 7.2 clone (user)
```sh
cd ./Documents/youtube/Git_user # gitのディレクトリに移動
git clone git@github.com:Sample-User1/github.git # pull
cd ./github
```

## 7.3 htmlに文章追加 (user)

* 作業ブランチ作成
```sh
git checkout -b html_branch # ブランチ作成
```


* htmlに文章追加


* commit
```sh
git add . # 指定したファイルをステージ
git commit -m "htmlに文章追加" # コミット
```

## 7.4 push (user)

```sh
git remote add origin git@github.com:Sample-User1/github.git # リモート設定
git push origin html_branch # push
```

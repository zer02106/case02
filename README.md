# master(main)にマージされた別のコミットを自分の開発ブランチに取り込みたい

## case01と同じ操作でcase02のリポジトリをフォークする
(略)

>コマンドから操作
## フォークしたリポジトリをローカルにクーロンして、その中に入る

```bash
git clone <your repository url> case02
cd case02
```
### 開発ブランチ01を作成する

```
git switch -c feature/case0201
```
## サンプルファイルを追加して、そのファイルをコミットしてリモートの開発ブランチにプッシュする

```
touch sample.txt
echo "hello, world" > sample.txt
git add sample.txt
git commit -m 'add sample.txt'
git push origin feature/case0201
```
## case01と同じ操作で、PRを作成し・マージを行う
(略)
*mainブランチに追加した sample.txt ファイルは取り込んでいることを確認*

>コマンドから操作
## ローカルmainブランチに戻ってもう一つ開発ブランチ02を作成する

```
git switch main
git switch -c feature/case0202
```
## 開発ブランチ02で別の修正を行う

```
touch sample02.txt
echo "hello, world" > sample02.txt
git add sample02.txt
git commit -m 'add sample02.txt'
```

## ローカルmainブランチに戻って更新する

```
git switch main
git pull origin main
```

先ほど開発ブランチ01の修正はmainに取り込んでいるのを確認する

## 開発ブランチ02で最新のmainブランチを取り込んでプッシュする

```
git switch feature/case0202
git rebase main
git push origin feature/case0202
```
## case01と同様操作で、PRを作成し・マージを行う
(略)
*mainブランチに sample.txtとsample02.txt ファイルは取り込んでいることを確認*

## ローカルの開発ブランチを削除

```
git branch -d feature/case0201
git branch -d feature/case0202
```

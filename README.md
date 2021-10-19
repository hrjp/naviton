
# naviton
Navit(oo)n - A mobile robot platform 

---

# Docker setup
* Ubuntu 18.04
* ROS Melodic


 ## 1.環境構築用のリポジトリをgit cloneする
```bash
git clone https://github.com/hrjp/rosenv
 ```

## 2.Docker containerを生成するスクリプトを実行する
2つの引数を指定する
* CONTAINER_NAME  --- コンテナの名前
* SHARE_FOLDER_PATH  --- コンテナの内部と共有するフォルダの絶対パス
### 以下どちらか選択

### GPU有り

```bash
./rosenv/docker/naviton_melodic_gpu/run.bash CONTAINER_NAME SHARE_FOLDER_PATH
```
### GPU無し

```bash:bash
./rosenv/docker/naviton_melodic/run.bash CONTAINER_NAME SHARE_FOLDER_PATH
```

## 3.Install naviton ros packages 
初めてコンテナ内部に入ったときに以下のスクリプトを実行してnaviton関連パッケージをインストールする

```bash:bash
cd /home && git clone https://github.com/hrjp/rosenv && ./rosenv/naviton_package.bash && source catkin_ws/devel/setup.bash
```

 ## 4.コンテナ作成後
homeディレクトリにCONTAINER_NAME.bash (CONTAINER_NAMEは自分で作成したコンテナの名前)が生成されている

```bash:bash
cd
./CONTAINER_NAME.bash
```
上記のスクリプトを実行すると自動でコンテナをスタートしてコンテナ内に入れる

---


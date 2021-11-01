
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
必要に応じて以下のオプションを指定する
| Option | Default | Details |
| :--- | :--- | :--- |
| -g | | GPUを使用する |
| -r | | コンテナからexitした際にコンテナを自動消去する | 
| -n CONTAINER_NAME | naviton_melodic | コンテナの名前 |
| -s SHARE_FOLDER_PATH | | コンテナ内部と共有するディレクトリのパス<br>rosbagをやデータを外部と共有する際に使用<br>(ex.　shareフォルダを作ってから　/home/user/share ) |



### Option無しで実行 (GPU無し　コンテナ名=naviton_melodic 共有フォルダ無し)
```bash
./rosenv/docker/naviton_melodic/run.bash
```
### Optionの使用例 (GPU有り　コンテナ名=naviton　共有フォルダ=/home/user/share)

```bash:bash
./rosenv/docker/naviton_melodic/run.bash -g -n naviton -s /home/user/share
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


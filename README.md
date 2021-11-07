

# Navit(oo)n - A mobile robot platform 



---

# Docker setup
Dockerで環境構築する場合
## Requirement
* Ubuntu 18.04 or 20.04
* Docker


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

# Native setup
ROS Melodicインストール済のPCに環境構築する場合
## Requirement
* Ubuntu 18.04
* ROS Melodic

 ## 1.環境構築用のリポジトリをgit cloneする
```bash
git clone https://github.com/hrjp/rosenv
 ```

```bash
./rosenv/package_install.bash
./rosenv/gazebo_update.bash
./rosenv/naviton_package.bash
 ```

 # Simulation demo

gazeboシミュレーションのデモを動かす
```bash
roslaunch kcctcore demo.launch
 ```


---

## Kobe Kosen Robotics Navigation Packages
* [naviton](https://github.com/KobeKosenRobotics/naviton)
    * kobe kosen roboticsの自律移動ロボットnavitonの環境構築
* [kcctcore](https://github.com/hrjp/kcctcore)
    * 各パッケージをつなぐマスターパッケージ
* [kcctnavigation](https://github.com/hrjp/kcctnavigation)
    * 自律移動用アルゴリズム全般
* [waypoint_tools](https://github.com/hrjp/waypoint_tools)
    * waypointの読み書きなどwaypointに関連するノード全般
* [kcctsim](https://github.com/hrjp/kcctsim)
    * gazebo simulationとrobotのURDFモデル
* [kcctplugin](https://github.com/hrjp/kcctplugin)
    * 自律移動用のrviz plugin
* [kcctfirm](https://github.com/hrjp/kcctfirm)
    * 自律移動ロボットNavitonのファームウェア
* [LeGO-LOAM](https://github.com/hrjp/LeGO-LOAM)
    * 3D Mapping
    * forked from [LeGO-LOAM](https://github.com/RobustFieldAutonomyLab/LeGO-LOAM)

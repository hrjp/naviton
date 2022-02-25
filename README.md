[![naviton workflow](https://github.com/hrjp/rosenv/actions/workflows/naviton-image-build.yml/badge.svg)](https://hub.docker.com/repository/docker/hrjp/naviton)
[![catkin build (main branch)](https://github.com/hrjp/naviton/actions/workflows/naviton-main-build-test.yml/badge.svg)](https://github.com/hrjp/naviton/actions/workflows/naviton-main-build-test.yml)
[![catkin build (develop branch)](https://github.com/hrjp/naviton/actions/workflows/naviton-develop-build-test.yml/badge.svg)](https://github.com/hrjp/naviton/actions/workflows/naviton-develop-build-test.yml)
![license](https://img.shields.io/github/license/hrjp/naviton)
![size](https://img.shields.io/github/repo-size/hrjp/naviton)
![commit](https://img.shields.io/github/last-commit/hrjp/naviton/main)
[![Docker Pulls](https://img.shields.io/docker/pulls/hrjp/naviton.svg)](https://hub.docker.com/repository/docker/hrjp/naviton)
# Navit(oo)n - A mobile robot platform 
* 2025年大阪万博での自動ゴミ拾いロボット実現を目標とした自律移動ロボットプロジェクト

* 中之島ロボットチャレンジ2020にて完走達成
* [中之島ロボットチャレンジ2021エクストラチャレンジ](https://www.nakanoshima-rc.jp/extra2021.html)にて完走＆課題完全達成　

![naviton_bekobe](https://user-images.githubusercontent.com/36100321/140645407-81af34fd-451e-4b16-b041-acf035970be1.jpeg)

## Navigation Movie
![navitonmovie](https://user-images.githubusercontent.com/36100321/140646689-f286757a-0510-4f52-9d16-587f6bef6fa1.gif)




---

# 1. Kobe Kosen Robotics Navigation Packages
このプロジェクトのリポジトリ一覧
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


---
# 2. CI/CD Workflow
### Github repositories
* [rosenv](https://github.com/hrjp/rosenv)
* [navtion](https://github.com/hrjp/navtion)

### Dockerhub repositories

* [hrjp/ros:melodic_cudagl](https://hub.docker.com/layers/194399415/hrjp/ros/melodic_cudagl/images/sha256-8f0648cf2c840fefeaeb9fb624497386ecb6f9b4792b77727953477ab3a038b0?context=repo)
* [hrjp/naviton:melodic_cudagl](https://hub.docker.com/layers/176446667/hrjp/naviton/melodic_cudagl/images/sha256-811f43a5f24c163e3523d76d6611c4becf3b7f1bccda090f922b35c50f095456?context=repo)
* [hrjp/naviton:melodic_main](https://hub.docker.com/layers/180881379/hrjp/naviton/melodic_main/images/sha256-df03b10e23c2cc1cf7252e9a9df5b2ef979120269faf4ba0923217672fa6293b?context=repo)
* [hrjp/naviton:melodic_develop](https://hub.docker.com/layers/180800620/hrjp/naviton/melodic_develop/images/sha256-937945f451e4bcd5dc3ebcf7016aa0d1335ae6dbd512fbb680c3ae56bb150ef9?context=repo)

```mermaid
graph TB
  subgraph rosenv
  hrjp/ros:melodic_cudagl-->hrjp/naviton:melodic_cudagl
  end
  subgraph naviton
  hrjp/naviton:melodic_cudagl-->hrjp/naviton:melodic_main
  hrjp/naviton:melodic_cudagl-->hrjp/naviton:melodic_develop
  end
  hrjp/ros:melodic_cudagl-->|Auto docker build and push at 11 P.M.|hrjp/ros:melodic_cudagl
  hrjp/naviton:melodic_cudagl-->|Auto docker build and push at 1 A.M.|hrjp/naviton:melodic_cudagl
  hrjp/naviton:melodic_main-->|Auto docker build and push at 3 A.M.|hrjp/naviton:melodic_main
  hrjp/naviton:melodic_develop-->|Auto docker build and push at 3 A.M.|hrjp/naviton:melodic_develop
  click hrjp/ros:melodic_cudagl https://hub.docker.com/layers/194399415/hrjp/ros/melodic_cudagl/images/sha256-8f0648cf2c840fefeaeb9fb624497386ecb6f9b4792b77727953477ab3a038b0?context=repo
  click hrjp/naviton:melodic_cudagl https://hub.docker.com/layers/176446667/hrjp/naviton/melodic_cudagl/images/sha256-811f43a5f24c163e3523d76d6611c4becf3b7f1bccda090f922b35c50f095456?context=repo
  click hrjp/naviton:melodic_main https://hub.docker.com/layers/180881379/hrjp/naviton/melodic_main/images/sha256-df03b10e23c2cc1cf7252e9a9df5b2ef979120269faf4ba0923217672fa6293b?context=repo
  click hrjp/naviton:melodic_develop https://hub.docker.com/layers/180800620/hrjp/naviton/melodic_develop/images/sha256-937945f451e4bcd5dc3ebcf7016aa0d1335ae6dbd512fbb680c3ae56bb150ef9?context=repo
  click rosenv https://github.com/hrjp/rosenv
  click naviton https://github.com/hrjp/naviton
  
```
---

# 3. Setup
環境構築には 2-1.Dockerを用いる方法(推奨), 2-2.ROS環境に直接構築する方法がある.
# 3-1. Docker setup
Dockerで環境構築する場合
## Requirement
* Ubuntu 18.04 or 20.04
* Docker install済みのPC


 ## (1).環境構築用のリポジトリをgit cloneする
```bash
git clone https://github.com/hrjp/naviton
 ```

## (2).Docker containerを生成するスクリプトを実行する
必要に応じて以下のオプションを指定する
| Option | Default | Details |
| :--- | :--- | :--- |
| -g | | GPUを使用する |
| -r | | コンテナからexitした際にコンテナを自動消去する | 
| -n CONTAINER_NAME | naviton_melodic | コンテナの名前 |
| -s SHARE_FOLDER_PATH | | コンテナ内部と共有するディレクトリのパス<br>rosbagをやデータを外部と共有する際に使用<br>(ex.　shareフォルダを作ってから　/home/user/share ) |



### Option無しで実行 (GPU無し　コンテナ名=naviton_melodic 共有フォルダ無し)
```bash
./naviton/docker/main/run.bash
```
### Optionの使用例 (GPU有り　コンテナ名=naviton　共有フォルダ=/home/user/share)

```bash:bash
./naviton/docker/main/run.bash -g -n naviton -s /home/user/share
```

 ## (3).コンテナ作成後
exitしてコンテナの外に出るとhomeディレクトリにCONTAINER_NAME.bash (CONTAINER_NAMEは自分で作成したコンテナの名前)が生成されている

```bash:bash
cd
./CONTAINER_NAME.bash
```
次回からは上記のスクリプトを実行すると自動でコンテナをスタートしてコンテナ内に入れる

---

# 3-2. Native setup
ROS Melodicインストール済のPCに環境構築する場合
## Requirement
* Ubuntu 18.04
* ROS Melodic

 ## (1).環境構築用のリポジトリをgit cloneする
```bash
git clone https://github.com/hrjp/rosenv
 ```
## (2).以下のコマンドを実行
```bash
./rosenv/package_install.bash
./rosenv/gazebo_update.bash
./rosenv/naviton_package.bash
 ```

 # 4. Simulation demo

上記の手順で環境構築後にgazeboシミュレーションのデモを動かす

catkin_wsにいる状態で以下のコマンドを実行
* 初回はgazeboの起動にかなり時間がかかる
* うまく行かないときは立ち上げ直す
```bash
roslaunch kcctcore demo2d.launch
 ```


---

# Development Version
開発中の最新バージョンを試す   
optionは上と同様
```bash
./naviton/docker/develop/run.bash
```


# naviton
Navit(oo)n - A mobile robot platform 


## Docker setup

### GPUを使用する場合

1. ### 環境構築用のリポジトリをgit cloneする

    ```bash:bash
        git clone https://github.com/hrjp/rosenv
    ```

2. ## Docker containerを生成するスクリプトを実行する
    2つの引数を指定する
    * CONTAINER_NAME  --- コンテナの名前
    * SHARE_FOLDER_PATH  --- コンテナの内部と共有するフォルダの絶対パス
    
    ```bash:bash
        ./rosenv/docker/naviton_melodic_gpu CONTAINER_NAME SHARE_FOLDER_PATH
    ```

3. ## Install naviton ros packages 
    初めてコンテナ内部に入ったときに以下のスクリプトを実行してnaviton関連パッケージをインストールする
    ```bash:bash
        cd /home && git clone https://github.com/hrjp/rosenv && ./rosenv/naviton_package.bash
    ```
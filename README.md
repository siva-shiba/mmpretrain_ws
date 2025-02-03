# mm-pretrain workspace
MM-pretrain用のdockerワークスペース

# set-up
このリポジトリはサブモジュールが含まれているので`mmpretrain`フォルダの中身がちゃんとcloneされているのを確認すること
```
git clone --recursive git@github.com:siva-shiba/mmpretrain_ws.git
```
もし`--recursive`オプションをつけ忘れた場合は以下のコマンドでサブモジュールがcloneされる
```
cd /PATH/TO/mmpretrain_ws
git submodule update --init --recursive
```
# start-up
起動方法
```
cd /PATH/TO/mmpretrain_ws
sh docker/run-docker.sh
```

# demo
mm-pretrainのデモ実行
```
cd /PATH/TO/mmpretrain_ws
sh docker/run-docker.sh
cd mmpretrain_ws
python demo/image_demo.py demo/demo.JPEG resnet18_8xb32_in1k --device cpu
```

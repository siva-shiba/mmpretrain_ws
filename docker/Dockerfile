FROM pytorch/pytorch:2.6.0-cuda11.8-cudnn9-devel

WORKDIR /ws

# pip の更新（任意）
RUN pip install --upgrade pip

# openmim のインストール (OpenMMLabツールの依存管理に便利)
RUN pip install openmim

# mmengine と mmcv のインストール
# MMPretrainで推奨されているバージョンに合わせるのが望ましいですが、
# 下記のように最新安定版を入れる例を示します。
RUN mim install mmengine "mmcv>=2.0.0"

# mmpretrain の依存パッケージをインストール
COPY ./mmpretrain /opt/mmpretrain
RUN pip install -r /opt/mmpretrain/requirements.txt

# mmpretrain を editable インストール（ソースコードを直接マウントして使える）
RUN pip install -e /opt/mmpretrain/

# ユーザー指定
ARG UID
ARG GID
ARG USERNAME
ARG GROUPNAME

RUN groupadd -g $GID $GROUPNAME
RUN useradd -m -u $UID -g $GID $USERNAME

RUN chown $USERNAME:$GROUPNAME -R /ws
USER $USERNAME

# ターミナルの色指定
RUN echo "PS1='\[\e[41;37m\]\u@\h\[\e[0m\]:\[\e[34m\]\w\[\e[0m\]$ '" >> /home/$USERNAME/.bashrc

ENTRYPOINT ["/bin/bash"]
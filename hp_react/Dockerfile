ARG NODE_IMG_VER=23.11
FROM node:${NODE_IMG_VER}

# タイムゾーンの設定
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
ENV TZ=Asia/Tokyo

RUN apt update -y
RUN apt install -y \
    git \
    curl \
    wget \
    tzdata \
    net-tools


# React アプリケーションの作成
WORKDIR /app
RUN yarn global add create-react-app

### material UI
RUN yarn add -g @mui/material @emotion/react @emotion/styled

################# alias 等の追加 #################
RUN { \
    echo 'export LS_OPTIONS="--color=auto"'; \
    echo 'alias ls="ls \$LS_OPTIONS"'; \
    echo 'alias ll="ls \$LS_OPTIONS -alF"'; \
    echo 'alias l="ls -CF"'; \
    echo 'umask 002'; \
    echo 'update_prompt() {'; \
    echo '    local time_str=$(TZ=Asia/Tokyo date +"%H:%M:%S")'; \
    echo '    PS1="${debian_chroot:+($debian_chroot)}\[\033[07;35m\][$time_str]\[\033[07;32m\]\u@\h:\[\033[07;34m\]\w\n\[\033[07;00m\]\$ "'; \
    echo '}'; \
    echo 'PROMPT_COMMAND=update_prompt'; \
    echo 'export PATH=$PATH:'; \
    } >> ~/.bashrc

RUN git config --global --add safe.directory /var/git

ARG REACT_APP_DIR_NAME=react-app
WORKDIR /app/${REACT_APP_DIR_NAME}

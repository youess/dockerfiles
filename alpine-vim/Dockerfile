# Build vim with alpine, but really, if you want to use fully vim functions,
# and install some plugins, it required many dependencies. The default apline
# vim binary version do not support python, and you build from source, and
# install the dependency software. Actually you found the finnal image is
# much bigger than you expected.

FROM alpine

MAINTAINER misaki007 <denis_lton@hotmail.com>

# dependency that used for compile vim from source, default vim do not support python
RUN apk add --update --virtual \
    build-deps \
    build-base \
    git \
    make \
    libsm \
    libice \
    libxt \
    libx11 \
    ncurses \
    libxpm-dev \
    libx11-dev \
    libxt-dev \
    ncurses-dev \
    python \
    python-dev \
    ctags

# use the ubuntu 14.04 version of vim, latest one really easily occured errors.
RUN git clone -b 'v7.4.052' --single-branch --depth=1 https://github.com/vim/vim.git /tmp/vim && \
    cd /tmp/vim && \
    ./configure --with-features=big \
        --enable-multibyte \
        --enable-pythoninterp \
        --with-python-config-dir=/usr/bin/python2.7/config \
        --disable-gui \
        --disable-netbeans \
        --prefix /usr && \
    make VIMRUNTIMEDIR=/usr/share/vim/vim74 && \
    make install && \
    rm -rf /usr/share/man/* \
          /usr/share/icons/* \
          /usr/share/doc/* \
          /usr/share/vim/vim74/lang/* \
          /usr/share/vim/vim74/tutor/* \
          /usr/share/vim/vim74/gvimrc_example.vim \
          /usr/share/vim/vim74/vimrc_example.vim \
          /var/cache/apk/* \
          /tmp/* \
          /var/log/* \
          /var/tmp/* && \
    find /usr/share/vim/vim74/ -name *.txt | while read line; do rm "$line"; done

RUN git clone --depth=1 https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

# COPY vimrc /etc/vim/vimrc
COPY vimrc /root/.vimrc

# RUN update-alternatives --install /usr/bin/editor editor /usr/bin/vim 1 && \
#  update-alternatives --set editor /usr/bin/vim && \
#  update-alternatives --install /usr/bin/vi vi /usr/bin/vim 1 && \
#  update-alternatives --set vi /usr/bin/vim

RUN vim +PluginInstall +qall

WORKDIR /root

CMD ["vim"]

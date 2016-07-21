
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
    ctags && \ 
    git clone --depth 1 https://github.com/vim/vim.git /tmp/vim && \
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
    apk del build-deps && \
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

RUN git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

# COPY vimrc /etc/vim/vimrc
COPY vimrc root/.vimrc

RUN vim +PluginInstall  +qall

CMD ["vim"]

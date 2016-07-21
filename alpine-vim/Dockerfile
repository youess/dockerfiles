
FROM alpine

RUN apk update && \
	apk add git \
			vim \
			ctags

RUN git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

COPY vimrc /etc/vim/vimrc

RUN vim +PluginInstall +qall

CMD ["vim"]
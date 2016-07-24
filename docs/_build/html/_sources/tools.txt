常用工具
========

一些工具

ssh
---
使用方法::

  ssh-keygen -t rsa
  ssh-copy-id yourserver
  ssh -T yourserver

git
---
服务器::

  mkdir project.git
  cd project.git
  git init --bare

本地::

  mkdir project
  cd project
  git init
  git add -A
  git commit -m "init"
  git remote add origin ssh://user@server:port/path/to/project.git
  git push origin master

gh-pages::

   git checkout --orphan gh-pages
   git rm -rf .
   ...
   git push origin gh-pages

链接地址：http(s)://<username>.github.io/<projectname>



pandoc
------
使用方法::

  sudo apt-get install pandoc texlive texlive-xetex texlive-latex-extra rmodern
  pandoc test.md --toc --smart --latex-engine=xelatex --template=yourtemplate.tex -o test.pdf

sphinx
------
使用方法::

  sudo pip install sphinx sphinx-autobuild
  sphinx-quickstart
  make html
  sphinx-autobuild . _build_html

其他
----

- 截屏工具 scrot ``scrot -s``
- 文件传输工具 scp
- youtube下载工具 youtube-dl
- 剪贴板工具 xclip



# README

## 有关贡献文档/网站的说明 <a id="instructions-for-contributing-to-the-docs-website"></a>

* [叉这个库](https://help.github.com/articles/fork-a-repo/)
* [部署站点本地](https://iot-fun.gitbook.io/iot/#deployment-of-the-site-locally)
* 添加更改
* [创建拉出请求](https://help.github.com/articles/creating-a-pull-request/)

## 在本地部署网站 <a id="deployment-of-the-site-locally"></a>

以下命令设置您的环境以在本地运行GitHub页面。您所做的任何编辑都可以在本地计算机上运行的轻量级Web服务器上查看。

安装Ruby 2.2或更高版本。如果您使用的是Linux，请运行以下命令：

```text
sudo apt-get install software-properties-commonsudo apt-add-repository ppa：brightbox / ruby​​-ngsudo apt-get updatesudo apt-get install ruby​​2.2sudo apt-get install ruby​​2.2-devsudo gem install github-pagessudo gem install jekyll bundlersudo bundle install
```

* 如果您使用的是Mac，请按照[以下说明操作](https://gorails.com/setup/osx/)。
* 如果您使用的是Windows计算机，则可以使用[Ruby安装程序](http://rubyinstaller.org/downloads/)。在安装过程中，请确保选中将_Ruby可执行文件添加到PATH_的选项。

安装GitHub Pages包，其中包括Jekyll：

```text
gem install github-pages
```

克隆我们的网站：

```text
git clone https://github.com/thingsboard/thingsboard.github.io.git
```

进行任何你想要的改变。然后，在本地查看您的更改：

```text
cd thingsboard.github.io捆绑exec jekyll服务
```

然后，您可以在以下[网址](http://localhost:4000/)查看您的网站副本：[http：// localhost：4000](http://localhost:4000/)（或Jekyll告诉您的任何地方）。


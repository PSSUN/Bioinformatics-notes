初次接触 Readthedocs 是在大二的时候用到一个处理 Ribo-seq 数据的软件，虽然也是基于 Linux 系统的命令行工具而且步骤繁杂，运行前要填写很多配置信息，但是由于rp-bp有详实可靠的在线说明文档（图一），所以按照作者提供的步骤一步一步来可以很容易得到结果。当时留给我印象最深的就是他的在线说明文档，我觉得布局很简洁，而且很方便。

当时很多软件的说明文件是和软件一起打包下载的，下到本地就是简单地文本文档，要么就是放在官网上，当然我要想做个小项目也没精力去专门维护一个服务器再写个网站。

![图一](https://upload-images.jianshu.io/upload_images/12798058-c1559254ade3436f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

所以 readthedocs 就解决了这个痛点。官方说的四个优点如下：

![官网截图](https://upload-images.jianshu.io/upload_images/12798058-64e1a37e0a2dfd4e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

那么如何利用ReadtheDocs发布自己的在线文档？

1\. 本地安装sphinx，sphinx是基于 python3 的，但是 linux 和 macOS 都是自带 python3 的所以不用管，直接用 pip3 安装 sphinx 就可以安装。
```shell
pip3 install sphinx
pip3 install sphinx_rtd_theme
```
其中 sphinx_rtd_theme 是要用的主题，还有其他的主题可以换，这个可以去 github 上看，有很多开源的主题，但是要注意大部分都是不允许商用的。安装好sphinx 之后在本地新建一个文件夹然后 cd 进去，命令行执行：
```shell
sphinx-quickstart
```
然后通过 y/n 做一些基本的配置，就会自动在本地生成一个项目，拿我的一个项目举例子，结构如下：
![tree](https://upload-images.jianshu.io/upload_images/12798058-f947d61bfbbb2774.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

因为篇幅原因，level 设置的是 2，source 里面的内容都是目录，打开之后就是.rts 文件，可以直接修改。

2\. 接下来我们要做的就是填写配置信息，有两个配置文件需要填写，第一个是 ./source/conf.py 另一个是 ./source/index.rst，第一个文件是 python 文件第二个文件是 rst 文件，但是由于都是配置文件所以语法没什么要求直接修改对应的选项就可以。
conf.py 里面是在线文档的各种信息包括主题，版本，作者，使用的语言等等，使用的语言这里支持 md 和 rts 两种，由于我 markdown 用的比较熟，所以这里我加了‘md’。 用 markdown需要额外安装一个 python 包。
```shell
pip3 install recommonmark
```
index.rst 配置的是在线文档的结构，可以自行添加删除，但是如果添加了某一个目录，那么 source文件夹下也必须有相应的文件夹，里面必须包含同名的配置文件，否则编译的时候会报错。

3\. 配置完这两个文件之后就可以写文档的主体，写哪个目录就去source对应的文件夹下的配置文件。如果选了 md 都用 md 语法写，如果选了 rts 就都用 rts 写。

4\. 上传到 github。在 github 上新建一个名为 test 的 repo，然后本地 push 上去。
```shell
echo "# test" >> README.md
git init
git add .
git commit -m "Initial"
git remote add origin git@github.com:yourusename/test.git
git push -u origin master
```
push 的时候 ssh 不行就换 https。

5\. 进入 [readthedocs](https://readthedocs.org/) ， 用 GitHub 账号可以直接登录。这个时候 test 这个 repo 就出现在列表里，选择这个 test点击build version就可以了。
![build_version](https://upload-images.jianshu.io/upload_images/12798058-dfd1c0ce9aaafbf9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

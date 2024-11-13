## 简介

如何在 github 上，用 hugo 架设自己的 blog？很多网上搜到的教程，都需要用户在自己的电脑上，安装运行各种 git 和 hugo 的相关命令，感觉对新手并不友好。所以，我试着写了一个流程，让新人完全只需要在网页浏览器上操作，就能快速生成自己的 blog 网站。

这个项目本质上，就是搭好一个现成的 hugo 模板，让用户 fork 到自己的账户下，设置 github page 和 workflow 就能直接使用。对功能和界面有什么额外要求的话，请自行学习 hugo 的进阶教程。——然后你们就不是需要用这个项目的新人啦~

- 在 github 上建立的 blog，在墙内是不能直接访问的，需注意；
- 本项目基于 [hugo](https://github.com/gohugoio/hugo) 博客引擎，和流行的 [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 主题；

## 教程

### 1. 创建 github 账号
首先，注册自己的 github 账号，过程略。注册过程中，你设置的账户名 username，通常就是最终的网站地址 username.github.io，当然以后也可以把自己的域名映射到上面。

### 2. 架设自己的 blog 项目

注意，这一步，**有两种方法**；

- 第一种方法：你建一个全新的项目，下载[我提供的 .zip 文件](https://github.com/fivestone/hugo-papermod-beginning/releases)，解压后，再手动上传到你的项目。和第二种相比，稍微繁琐一点。但还是希望大家，**有条件的话，使用这种方法**。

- 第二种方法，把我的这个项目，fork 到你的项目。这种方法**对新人更简便**，完全不需要在本地操作文件，只用手机或 pad 就可以完成。但这种 fork 在一起的项目，在进行自动发布 blog 的操作时，是共享同一个操作额度的。如果 fork 的人数非常多，未来可能会[被 Github 限制](https://github.com/LSPosed/MagiskOnWSALocal)。——要达到这种规模，大概要几千人同时用吧……所以也不需要很在意。

#### 2.1. 第一种方法

注册并登入账号后，新建自己的项目（Repository）。

![](https://blog.fivest.one/wp-content/uploads/20241111-30.jpg)

项目的名称，决定了最终 blog 的网址。假设你的 github 用户名为 username

- 如果把项目命名为 username.github.io ，则最终的网站地址为
https://username.github.io/
- 如果把项目设置成其它名字，如 new-name，则最终的网站地址为
https://username.github.io/new-name

确认项目为 Public。其它设置都不需要更改，点击绿色按钮创建。

![](https://blog.fivest.one/wp-content/uploads/20241111-31.jpg)

创建项目后，点击「上传已有的文件」

![](https://blog.fivest.one/wp-content/uploads/20241111-32.jpg)

从我的项目的 [release 页面](https://github.com/fivestone/hugo-papermod-beginning/releases)，下载已经设置好的 [hugo 文件包](https://github.com/fivestone/hugo-papermod-beginning/releases/download/1.0/fivestone-hugo-papermod-beginning-1.0.zip)，在本地解压缩 .zip 文件。然后，把里面的所有文件，拖拽上传到你的项目里。

![](https://blog.fivest.one/wp-content/uploads/20241111-33.jpg)

等到 80 多个文件都被上传后，别忘了点击页面底部的 Commit changes 提交。

![](https://blog.fivest.one/wp-content/uploads/20241111-34.jpg)

#### 2.2. 第二种方法

注册并登入账号后，进入项目：

https://github.com/fivestone/hugo-papermod-beginning

点击 Fork，将这个模板复制到你自己的账号下。

![](https://blog.fivest.one/wp-content/uploads/20241111-01.jpg)

点击 Fork 后，需要设置你自己的项目名称，和第一种方法一样，假设你的 github 用户名为 username

- 如果把项目命名为 username.github.io ，则最终的网站地址为
https://username.github.io/
- 如果把项目设置成其它名字，如 new-name，则最终的网站地址为
https://username.github.io/new-name

然后点击 Create fork 创建项目。

![](https://blog.fivest.one/wp-content/uploads/20241111-02.jpg)

---

### 3. 配置自动发布 blog

创建新项目后，进入项目的 Settings – Pages 页面，把 Build and deployment – Source，改为 GitHub Actions。

![](https://blog.fivest.one/wp-content/uploads/20241111-03.jpg)

把 Source 从 Deploy from a branch，改为 GitHub Actions 后，进入上方的 Actions 页面。

![](https://blog.fivest.one/wp-content/uploads/20241111-04.jpg)

初次进入 Actions 页面后，会显示 Github 预设的各种配置方案，通过搜索框找到 hugo，然后点击 hugo 方案中的 Configure

![](https://blog.fivest.one/wp-content/uploads/20241111-35.jpg)

系统会自动生成配置文件，不需要做任何改动，点击绿色的 Commit changes 提交。

![](https://blog.fivest.one/wp-content/uploads/20241111-36.jpg)

此时自动发布的 action / workflow 就已经开始运行了，大约 1~2 分钟后，就可以在
https://username.github.io 看到 blog 最初的页面了。

以后，每次对项目里文章或配置文件的更改，都会触发这个 action / workflow，重新生成一遍网站。可以在 Actions 页面，查看 workflow 每次运行的情况。

![](https://blog.fivest.one/wp-content/uploads/20241111-37.jpg)

---

### 4. 更改网站基本信息

在 Code 页面，点击编辑 config.yml 页面，把一些预设的网站信息，改成你自己的信息。

![](https://blog.fivest.one/wp-content/uploads/20241111-09.jpg)

对新人来说，需要在 config.yml 文件里更改的，大概有以下几项：

```
baseURL: https://username.github.io/ # 改成你自己的网址
title: 网站名称
params:
  author: somebody # 作者的署名

  homeInfoParams:
    Title: 网站标题，只显示在首页上
    Content: >
      显示在首页标题下方的一些文字。</br>
      支持一些简单的 html 和 markdown。
```

更改后，点击绿色的 Commit Changes… 在弹出的页面中，再一次点击绿色的 Commit Changes，保存文件后 1~2 分钟，就可以在 blog 页面上，看到更改后的内容了。

![](https://blog.fivest.one/wp-content/uploads/20241111-10.jpg)

---

### 5. 添加、管理文章

所有的 blog 文章，都在 content / posts 目录中。在 Code 页面，进入 content / posts 目录。点击右上角，创建新文件。

![](https://blog.fivest.one/wp-content/uploads/20241111-11.jpg)

所有的文章，均为 .md 结尾的 markdown 文件。文件名对应着这篇文章的网址，譬如，post-20241111.md 文章链接，就是
https://username.github.io/posts/post-20241111/

在文件的开头，如图所示，写入用 --- 隔开的，文章的标题和发布日期。在熟悉 hugo 的设置后，也可以在此处添加更多的文章信息和选项。

```
---
title: "新文章的标题"
date: "2024-11-11"
---
然后开始写正文，markdown 格式。
```

![](https://blog.fivest.one/wp-content/uploads/20241111-12.jpg)

同样，点击绿色的 Commit changes… 保存提交。1~2 分钟后，就可以在 blog 页面上看到新文章了。

content / posts 目录里的所有文件，都可以随意地新增、删除、修改、重命名文件。对应着 blog 文章的增删改、和改变 url 链接。

文章内嵌的图片，建议放在 static 目录下，然后在文章中用 markdown 格式引用。譬如 static / aa.jpg 文件，相应地在 markdown 文件中插入的代码为：

```
![](https://username.github.io/aa.jpg)
```

有经验的用户，也可以使用其它更有效的组织方式。

## 其它注意事项

- 生成的 blog 对应的 rss 订阅地址为
```
https://username.github.io/index.xml
```

- 如果是用第二种方法，直接 fork 的项目，以后在这个 blog 项目里，会一直看到，图片里这样的消息，提示要把你对项目的更改，反馈给原本的我的项目。——不用理会就是了。

![](https://blog.fivest.one/wp-content/uploads/20241111-14.jpg)
# docker实现多网口openwrt软路由

### 测试环境
- nanopi-r4s, 
- Armbian 21.08.6 Focal with Linux 5.10.63-rockchip64, 
- OpenWrt R21.11.11 (2021-11-14) / LuCI Master (git-21.280.14233-9b796b1) 

### 适用范围
- 运行linux的x86/x64/ARM的软路由

## 安装系统
下载Armbian并烧录 (https://www.armbian.com/nanopi-r4s/).  
下载docker并安装 (https://docs.docker.com/engine/install/ubuntu/).  
下载rootfs, 本教程使用openwrt-rockchip-armv8-rootfs.tar.gz, 根据各自需要更换 (https://www.openwrt.cc/releases/targets/rockchip/armv8).  

    cd
    mkdir openwrt_tmp
    cd openwrt_tmp
    wget 
    wget --no-check-certificate www.openwrt.cc/releases/targets/rockchip/armv8/openwrt-rockchip-armv8-rootfs.tar.gz
    
建立dockerfile并生成镜像  

    sudo vim dockerfile

写入内容

    FROM scratch 
    ADD openwrt-rockchip-armv8-rootfs.tar.gz / 
    EXPOSE 22 80 443 
    ENTRYPOINT ["/sbin/init"]

生成镜像
    
    docker build -t openwrt_r4s . 

## Welcome to GitHub Pages
You can use the [editor on GitHub](https://github.com/future141/future141.github.io/edit/main/index.md) to maintain and previeCancel changesw the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/future141/future141.github.io/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.

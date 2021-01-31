# Welcome to the fimap project!

## _项目原地址：https://gitlab.tha-imax.de/root/fimap_

fimap 是一个 python2 编写的小工具，它可以自动查找、准备、审计、利用甚至通过 google 查找 web 应用中的本地和远程文件包含漏洞。

fimap 类似 sqlmap 工具，只是针对 LFI/RFI 漏洞，而不是 sql 注入。

---

## 安装

克隆项目：

```bash
git clone https://github.com/iSecurityClub/fimap.git && cd fimap
```

如果你未安装 pip2，请使用如下命令安装（需要先安装 python2）：

```bash
wget https://bootstrap.pypa.io/2.6/get-pip.py && python2 get-pip.py && rm get-pip.py
```

安装 Python2 依赖库:

```bash
pip2 install -r ./src/requirements.txt
```

## 使用方法

- 主程序：`./src/fimap.py`

- 查看帮助：

```bash
python2 fimap.py -h
```

- 对单个 URL 进行测试：

```bash
python2 fimap.py -u http://192.168.64.1:83/index.php?page=submit
```

![](https://isecurityclub-1253463441.cos.ap-chengdu.myqcloud.com/uPic/iShot2021-01-31%2016.47.17.png!w)

![](https://isecurityclub-1253463441.cos.ap-chengdu.myqcloud.com/uPic/1612082883224.jpg!w)

- 从给定的根路径开始爬取，并将爬取到的链接保存到 output.txt

```bash
python2 fimap.py –H –u http://target-site.com/ –w output.txt -C
```

- 还可以使用 `-d` 指定爬取深度：

```bash
python2 fimap.py –H –u http://target-site.com/ -d 3 –w output.txt -C
```

- 从文件中读取目标链接进行测试：

```bash
python2 fimap.py –m –l /path/to/list/output.txt -C
```
- 结合 Google Hacker 进行测试：
```bash
python2 fimap.py –g –q inurl:index2.php?x= -C
```
- 以颜色模式输出：
```bash
python2 fimap.py -C
```

## fimap 功能介绍

- 支持检查单个 URL、URL 列表或结合 Google Hacker 结果
- 自动识别和利用文件包含漏洞
- 自动处理相对/绝对路径处理
- 自动尝试用 Nullbyte 和其他方法如 Dot-Truncation 来结束后缀
- 支持远程文件注入/日志文件注入
- 支持`blind`模式(--enable-blind)，当服务器禁用错误信息时，强制遍历所有测试
- 支持交互式利用模式
- 支持添加你自己的 payloads 和 pathes 到 xml 文件或重新写一个你自己的插件
- 支持使用 proxys
- 支持扫描和利用 GET、POST 和 Cookies



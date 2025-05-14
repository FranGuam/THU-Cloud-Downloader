# Tsinghua Cloud Downloader

清华云盘批量下载助手，适用于分享的文件 size 过大导致无法直接下载的情况，本脚本添加了更多实用的小功能：

- [x] 直接下载链接中的所有文件，无打包过程，且无文件数量和大小限制
- [x] 支持下载带密码云盘链接
- [x] 支持查看文件下载总大小和下载进度
- [x] 支持模糊匹配需要下载的文件（如指定文件类型 / 指定文件夹下载）

## Dependency

需要提前安装 python，安装过程略，以及`requirements.txt`文件里面的依赖库：

```shell
pip install -r requirements.txt
```

## Usage

| Flags            | Default       | Description                                                |
| ---------------- | ------------- | ---------------------------------------------------------- |
| _--link, -l_     | **Required**  | Share link of Tsinghua Cloud.                              |
| _--save_dir, -s_ | `./downloads` | Path to save the files. Default: `./downloads`.            |
| _--file, -f_     | `None`        | Regex to match the file path. Default: download all files. |

### Example

```shell
python thu_cloud_download.py \
    -l https://cloud.tsinghua.edu.cn/d/1234567890/
    -s "/PATH/TO/SAVE" \
    -f "*.pptx?" (regex, 正则表达式) \
```

### Note

_--file, -f_ 参数支持 UNIX shell 风格的 pattern 字符串，支持使用如下几个通配符：

- **\***: 可匹配任意个任意字符。
- **?**:可匹配一个任意字符。
- **\[字符序列\]**: 可匹配中括号里字符序列中的任意字符。该字符序列也支持中画线表示法。比如 \[a-c\] 可代表 a, b 和 c 字符中任意一个。
- **\[\!字符序列\]**: 可匹配不在中括号里字符序列中的任意字符。

具体用法如下

```shell
# 下载链接中所有文件
python thu_cloud_download.py -l https://xxx
# 下载链接中所有的.txt文件
python thu_cloud_download.py -l https://xxx -f *.txt
# 下载链接中某个文件夹的所有文件
python thu_cloud_download.py -l https://xxx -f folder/subfolder/*
```

## Credit

Forked from [chenyifanthu/THU-Cloud-Downloader](https://github.com/chenyifanthu/THU-Cloud-Downloader)

# 设置

几乎所有设置都通过环境变量指定，除了服务器网络相关设置。

例如：
=== "Linux/MacOS"
    你可以在命令前添加它
    ``` bash
    CONTENT=../mycomics/ thumb=/tmp/thumb/ comiclib
    ```
    或者先设定好
    ``` bash
    export CONTENT=../mycomics/
    export thumb=/tmp/thumb/
    comiclib
    ```
=== "Windows"
    ```
    set CONTENT=..\mycomics\
    set thumb=C:\Users\Administrator\AppData\Local\Temp\thumb\
    comiclib
    ```
环境变量的键一般不区分大小写。

下面是可用的设置列表：

| 环境变量 | 说明 | 默认值 |
| ------- | ---- | ----- |
| `debug` | 开启调试输出（`True`/`False`） | `False` |
| `loglevel` | 日志级别（`DEBUG`/`INFO`/`WARNING`/`ERROR`/`CRITICAL`），若`debug`为`True`，会被覆盖为`DEBUG` | `INFO` |
| `content` | 漫画文件存放的路径（由于 [Python 的一个问题](https://github.com/python/cpython/issues/77609)，暂不支持跟随符号链接） | `.` |
| `thumb` | 生成的缩略图存放的路径 | `./thumb`|
| `metadata` | 元数据库 URL，参考[SQLAlchemy 文档](https://docs.sqlalchemy.org/en/20/core/engines.html#database-urls) | `sqlite:///./comiclib_metadata.db` |
| `password` | 管理密码，若为`None`则任何访客皆可编辑。此功能防君子不防小人，若需安全保护请借助反向代理的 HTTP 基本验证、Cloudflare Access 或 TLS 客户端证书等。| `None`|
| `skip_exists`| 扫描时是否跳过曾扫入元数据库的漫画？（`True`/`False`）| `True` |
| `watch` | 监视漫画文件夹，自动扫描 （`True`/`False`）| `True` |
| `UA_convert_jxl` | 对于哪些 user-agent 的请求在服务端将 JPEG XL 文件转为其他流行格式，该值是一个用于匹配的正则表达式 | `Android` |
| `UA_convert_all` | 对于哪些 user-agent 的请求在服务端将所有文件转为其他流行格式，该值是一个用于匹配的正则表达式 | `\b\B`（不匹配任何东西）|

对于扫描脚本的设置，请参看各自的说明。

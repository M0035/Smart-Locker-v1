# 智能快递柜一代

本仓库保存智能快递柜项目的第一代代码：Qt Quick 客户端与 C/SQLite UDP 服务端。源码来自本人 Linux 虚拟机中的工程，于 2026-10-28 同步到本机学习库后整理为独立仓库。当前仍处于学习和开发阶段，并非已完成的产品。

## 目录

| 路径 | 内容 |
| --- | --- |
| `qt-client/` | Qt Quick 界面、`QUdpSocket` 客户端、qmake 配置和所需图片资源 |
| `udp-server/` | UDP 服务端、SQLite 业务逻辑和 Makefile |

## 编译与运行

服务端需要 GCC、SQLite3 开发头文件和库。在 Linux 中进入 `udp-server/` 后运行 `make`，再运行 `./udpServer`。程序监听 UDP 8888 端口，并使用启动时工作目录下的 `lockers.db`；请用测试数据库验证，避免覆盖已有数据。

客户端需要相应的 Qt Quick、Qt Network 和 Qt Virtual Keyboard 环境。用 Qt Creator 打开 `qt-client/lockers.pro`，或在该目录运行 `qmake lockers.pro` 和 `make`。`main.qml` 中服务端地址当前为 `127.0.0.1:8888`，客户端与服务端不在同一系统时需改为实际地址。

以上是根据源码和构建配置整理的运行步骤；本次整理没有在 Linux 中完成编译或端到端验证。

## 当前范围

客户端包含注册、登录、投递和取件页面；服务端接收 `l/r/d/p` 类型的 UDP 请求，并通过 SQLite 保存快递员、柜格和投递记录。Web/Apache 示例暂未纳入这一代仓库。数据库文件、编译产物、日志、IDE 本地配置和虚拟机连接资料也未纳入。

代码仍有待整改：UDP 字段边界与回复长度、数据库初始化、取件完整流程、跨用户登录身份、Qt 回复异常处理等尚未完成验证。请勿直接用于真实用户数据或联网生产环境。

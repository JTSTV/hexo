---
title: loophole每 40 分钟自动重启一次隧道，防止掉线脚本
date: 2028-01-23 11:33:15
tags:
---
前提条件loophole可执行文件位于
<div class="red-box">
```bash
/usr/local/bin

```
</div>
下载好loophole,到loophole可执行文件目录移动loophole到指定文件夹
<div class="red-box">
```bash
mv loophole /usr/local/bin

```
</div>
然后制作脚本
<div class="red-box">
```bash
vim /usr/local/bin/loophole_loop.sh

```
</div>
把下方脚本文件粘贴进去保存.   
输出的日志文件位于
/var/log目录的loophole_loop.log文件
查看检测脚本文件是否正常运行
<div class="red-box">
```bash
cat /var/log/loophole_loop.log
```
</div>
脚本如下
<div class="red-box">
```bash
#!/bin/bash
# Loophole 循环守护脚本
# 每 40 分钟自动重启一次隧道，防止掉线

# Loophole 可执行文件的路径
LOOPHOLE_BIN="/usr/local/bin/loophole"

# 需要穿透的本地端口（已修改为8000）
LOCAL_PORT=8000

# 选择协议（http / https / tcp），这里默认使用 http
PROTOCOL="http"

# 二级域名前缀
HOSTNAME="hhwzj"

# 循环监控，确保每 40 分钟重启一次
while true; do
    echo "[$(date '+%Y-%m-%d %H:%M:%S')] 启动 Loophole 隧道..."

        # 启动 Loophole 隧道，日志输出到 /var/log/loophole/loophole.log
            # 添加了 --hostname 参数来设置二级域名前缀
                $LOOPHOLE_BIN $PROTOCOL $LOCAL_PORT --hostname $HOSTNAME >> /var/log/loophole/loophole.log 2>&1 &

                    # 记录进程 ID
                        TUNNEL_PID=$!

                            # 运行 40 分钟（40 * 60 = 2400 秒）
                                echo "[$(date '+%Y-%m-%d %H:%M:%S')] 隧道已启动，PID=$TUNNEL_PID，将在 40 分钟后重启..."
                                    sleep 2400

                                        # 杀掉 Loophole 进程，准备重启
                                            echo "[$(date '+%Y-%m-%d %H:%M:%S')] 重启隧道..."
                                                kill -9 $TUNNEL_PID
                                                    sleep 2  # 等待端口释放
                                                    done
                                            ```
</div>

以后每次进入ubuntu只需要运行脚本文件就可以了后台
 <div class="red-box">
 ```bash
 nohup /usr/local/bin/loophole_loop.sh > /var/log/loophole_loop.log 2>&1 &
 ```
 </div>
手动执行前台
<div class="red-box">
```bash
/usr/local/bin/loophole_loop.sh
```
</div> 
   
     



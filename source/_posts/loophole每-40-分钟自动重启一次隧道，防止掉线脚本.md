---
title: loophole每 40 分钟自动重启一次隧道，防止掉线脚本
date: 2026-02-23 11:33:15
tags:
---
<div class="red-box">
````bash
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
以后每次进入ubuntu只需要运行脚本文件就可以了
                                                    <div>
                                            ```
 /usr/local/bin/loophole_loop.sh
```
</div>

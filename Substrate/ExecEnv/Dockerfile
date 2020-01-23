# Substrate运行环境容器
FROM debian:stretch-slim
LABEL maintainer="13088966264@163.com"
LABEL description="Substrate最小运行环境容器，启动执行substrate"

# 显示回溯
ENV RUST_BACKTRACE 1

# 安装工具和依赖
RUN apt-get update && \
	DEBIAN_FRONTEND=noninteractive apt-get upgrade -y && \
	DEBIAN_FRONTEND=noninteractive apt-get install -y \
		libssl1.1 \
		ca-certificates \
		curl && \
# 清除缓存
	apt-get autoremove -y && \
	apt-get clean && \
	find /var/lib/apt/lists/ -type f -not -name lock -delete

EXPOSE 30333 9933 9944

FROM node:18-bullseye

LABEL maintainer="Fedorov"
LABEL description="Chatbox Dev Container"
LABEL version="1.0"
LABEL name="Chatbox Dev Container"

# 替换为阿里云 Debian 源
RUN sed -i 's@http://deb.debian.org/debian@https://mirrors.aliyun.com/debian@g' /etc/apt/sources.list \
    && sed -i 's@http://security.debian.org/debian-security@https://mirrors.aliyun.com/debian-security@g' /etc/apt/sources.list

# 安装 Electron 运行所需的系统依赖
RUN apt-get update && apt-get install -y \
    libgtk-3-0 \
    libnss3 \
    libasound2 \
    libx11-xcb1 \
    libxcomposite1 \
    libxdamage1 \
    libxrandr2 \
    libgbm1 \
    libatk-bridge2.0-0 \
    libxss1 \
    libgconf-2-4 \
    libxtst6 \
    libdrm2 \
    libxext6 \
    libxfixes3 \
    libcups2 \
    libdbus-1-3 \
    libatspi2.0-0 \
    libpango-1.0-0 \
    libcairo2 \
    libxcb1 \
    libxkbcommon0 \
    git \
    curl \
    python3 \
    build-essential \
    xvfb \
    && rm -rf /var/lib/apt/lists/*

# 推荐使用清华源加速 npm
RUN npm config set registry https://registry.npmmirror.com

# 创建vscode用户
RUN useradd -ms /bin/bash vscode && \
    echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# 使用vscode用户    
USER vscode

WORKDIR /workspaces/chatbox

EXPOSE 1212

CMD ["npm", "install"]
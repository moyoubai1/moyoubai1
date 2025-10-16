# 莫攸白 - 独立音乐人个人品牌展示网站

## 项目简介

这是一个为独立音乐人莫攸白打造的个人品牌展示网站，融合潮流古风元素，展示艺人资料、音乐作品和歌词等内容。

## 功能特点

- 响应式设计，适配各种设备屏幕
- 歌词展示系统，支持歌曲切换和歌词高亮
- 艺人资料与故事介绍
- 联系信息展示

## 技术栈

- HTML5
- Tailwind CSS v3
- JavaScript
- Font Awesome 图标库

## 本地开发

1. 克隆项目到本地
2. 使用现代浏览器（Chrome、Firefox、Edge等）直接打开 `index.html` 文件
3. 或使用本地服务器运行：
   ```
   # 使用Python简单HTTP服务器
   python3 -m http.server 8000
   ```
   然后访问 `http://localhost:8000`

## 如何将本地地址改为 http://moyoubai.com

### 方法一：本地开发环境配置（推荐）

如果你希望在本地开发环境中使用 `http://moyoubai.com` 域名，可以按照以下步骤配置：

#### Windows系统：
1. 打开文件 `C:\Windows\System32\drivers\etc\hosts`
2. 添加以下内容：
   ```
   127.0.0.1       moyoubai.com
   127.0.0.1       www.moyoubai.com
   ```
3. 保存文件（可能需要管理员权限）
4. 使用本地服务器运行网站（如Python的http.server）
5. 访问 `http://moyoubai.com:8000`

#### macOS/Linux系统：
1. 打开终端，输入以下命令：
   ```bash
   sudo nano /etc/hosts
   ```
2. 添加以下内容：
   ```
   127.0.0.1       moyoubai.com
   127.0.0.1       www.moyoubai.com
   ```
3. 按 `Ctrl+O` 保存，按 `Ctrl+X` 退出
4. 使用本地服务器运行网站（如Python的http.server）
5. 访问 `http://moyoubai.com:8000`

### 方法二：本地环境重定向工具

项目中包含 `local-redirect.html` 文件，可用于：
- 检测访问环境（本地开发环境或生产环境）
- 提供手动切换环境的选项
- 自动重定向功能

使用方法：
1. 在本地开发环境中访问 `http://localhost:8000/local-redirect.html`
2. 根据提示选择是否重定向到生产环境或继续使用本地环境

## 生产环境部署

### 1. 域名配置

- 将域名 `moyoubai.com` 解析到你的服务器IP地址
- 配置DNS记录，添加A记录指向服务器IP

### 2. Apache服务器配置

项目中已包含 `.htaccess` 文件，实现以下功能：
- 前端路由支持
- 缓存控制
- Gzip压缩
- 安全头部设置

### 3. Nginx服务器配置（可选）

如果使用Nginx服务器，请参考以下配置：

```nginx
server {
    listen 80;
    server_name moyoubai.com www.moyoubai.com;

    # 安全头部
    add_header X-Frame-Options SAMEORIGIN;
    add_header X-XSS-Protection "1; mode=block";
    add_header X-Content-Type-Options nosniff;
    add_header Content-Security-Policy "default-src 'self'; script-src 'self' 'unsafe-inline' https://cdn.tailwindcss.com https://cdn.jsdelivr.net; style-src 'self' 'unsafe-inline' https://cdn.tailwindcss.com https://cdn.jsdelivr.net; img-src 'self' data: https://p3-flow-imagex-sign.byteimg.com https://p3-doubao-search-sign.byteimg.com https://p26-doubao-search-sign.byteimg.com; font-src 'self' https://cdn.jsdelivr.net;";

    # 缓存控制
    location ~* \.(html|htm|js|css|jpg|jpeg|png|gif|ico|svg)$ {
        expires 1d;
        add_header Cache-Control "public, max-age=86400";
    }

    # Gzip压缩
    gzip on;
    gzip_types text/plain text/html text/xml text/css application/xml application/xhtml+xml application/rss+xml application/javascript application/x-javascript;

    # 网站文件根目录
    root /path/to/your/website/files;
    index index.html;

    # 前端路由支持
    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

### 4. 文件上传

- 将所有网站文件上传到服务器的网站根目录
- 确保文件权限正确（通常为644）
- 确保目录权限正确（通常为755）

## 注意事项

1. 本地开发环境配置仅在你的计算机上生效，不会影响其他用户访问
2. 生产环境部署需要你拥有 `moyoubai.com` 域名的所有权
3. 如果你希望在生产环境中使用HTTPS，请参考之前的配置文档或联系技术支持

## 网站维护

- 定期备份网站文件和数据
- 监控网站性能和访问情况
- 及时更新依赖库和安全补丁

## 联系方式

如需技术支持或有任何问题，请联系：contact@moyoubai.com

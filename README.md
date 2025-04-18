# JSON在线工具

一个功能强大的JSON在线格式化与验证工具，支持多种数据格式操作。

## 主要功能

- JSON格式化与高亮显示
- JSON语法校验与错误提示
- JSON压缩
- XML与JSON相互转换
- 行号显示
- 代码折叠
- 文件上传解析
- AI智能修复
- 撤销操作
- 保存到本地
- 自适应高度布局
- 可调整面板宽度
- 复制到剪贴板

## 特色功能

### AI智能修复
智能识别并修复损坏的JSON结构，包括：
- 缺失的大括号或中括号
- 未闭合的引号
- 多余的逗号
- 提取嵌入在其他文本中的JSON对象

### 布局调整
- 支持通过拖动分隔线调整左右面板宽度
- 自适应窗口高度，最大化利用屏幕空间
- 显示/隐藏行号

### 文件操作
- 上传JSON文件直接解析
- 将格式化或压缩后的JSON保存到本地
- 文件名使用时间戳和MD5哈希自动生成，便于管理

## 项目结构

- `index.html` - 主页面，提供JSON在线解析功能
- `wiki.html` - JSON知识介绍
- `code.html` - JSON解析代码示例
- `component.html` - JSON相关组件
- `css/` - 样式文件
- `js/` - JavaScript脚本
- `fonts/` - 字体资源
- `json/` - JSON相关资源

## 使用方法

1. 在左侧文本框中输入JSON或XML字符串，或点击"上传"按钮导入JSON文件
2. 系统自动解析并在右侧显示格式化后的内容
3. 使用右侧工具栏按钮进行各种操作：
   - 压缩/格式化切换
   - 显示/隐藏行号
   - 清空内容
   - 撤销操作
   - 复制到剪贴板
   - 保存到本地
   - 转换为XML
   - AI智能修复
4. 拖动中间分隔线调整左右面板宽度比例

## 在线访问

访问 [hijson.com](https://hijson.com) 立即使用此工具

# JSON 在线解析工具

一个简单易用的 JSON 在线解析、格式化、验证工具。支持 JSON 与 XML 相互转换，并提供 AI 智能修复功能。

## 功能特点

- JSON 在线解析和格式化
- JSON 语法验证
- JSON 压缩
- JSON 与 XML 相互转换
- AI 智能修复
- 多语言支持（中文、英文、日文、韩文）
- 支持文件上传
- 支持复制到剪贴板
- 支持保存到本地

## 部署说明

### 环境要求

- Nginx 1.18 或更高版本
- 支持静态文件服务

### 部署步骤

1. **安装 Nginx**

   Ubuntu/Debian:
   ```bash
   sudo apt update
   sudo apt install nginx
   ```

   CentOS:
   ```bash
   sudo yum install nginx
   ```

2. **配置网站文件**

   - 创建网站目录：
     ```bash
     sudo mkdir -p /var/www/json-parser
     ```

   - 复制网站文件到该目录：
     ```bash
     sudo cp -r * /var/www/json-parser/
     ```

   - 设置目录权限（根据系统选择对应的命令）：

     Ubuntu/Debian:
     ```bash
     sudo chown -R www-data:www-data /var/www/json-parser
     sudo chmod -R 644 /var/www/json-parser/*  # 文件权限
     sudo find /var/www/json-parser -type d -exec chmod 755 {} \;  # 目录权限
     ```

     CentOS/RHEL:
     ```bash
     sudo chown -R nginx:nginx /var/www/json-parser
     sudo chmod -R 644 /var/www/json-parser/*  # 文件权限
     sudo find /var/www/json-parser -type d -exec chmod 755 {} \;  # 目录权限
     ```

3. **配置 Nginx**

   - 复制配置文件：
     ```bash
     sudo cp nginx.conf /etc/nginx/conf.d/json-parser.conf
     ```

   - 修改配置文件中的域名和路径：
     ```bash
     sudo nano /etc/nginx/conf.d/json-parser.conf
     ```
     
     将以下内容替换为你的实际配置：
     ```nginx
     server_name your-domain.com;  # 替换为你的域名
     root /var/www/json-parser;    # 替换为你的网站目录
     ```

4. **测试配置**

   ```bash
   sudo nginx -t
   ```

5. **重启 Nginx**

   ```bash
   sudo systemctl restart nginx
   ```

### 访问网站

- 如果使用域名：直接访问 `http://your-domain.com`
- 如果使用 IP：访问 `http://your-server-ip`

## 服务更新说明

### 手动更新

1. **备份当前文件**
   ```bash
   sudo cp -r /var/www/json-parser /var/www/json-parser.bak
   ```

2. **更新文件**
   ```bash
   # 进入项目目录
   cd /path/to/your/project
   
   # 拉取最新代码
   git pull
   
   # 复制到网站目录
   sudo cp -r * /var/www/json-parser/
   
   # 设置正确的权限
   sudo chown -R nginx:nginx /var/www/json-parser/
   sudo chmod -R 644 /var/www/json-parser/*
   sudo find /var/www/json-parser/ -type d -exec chmod 755 {} \;
   
   # 重新加载 Nginx 配置
   sudo systemctl reload nginx
   ```

3. **检查更新**
   - 访问网站检查功能是否正常
   - 检查浏览器控制台是否有错误
   - 检查 Nginx 错误日志：`sudo tail -f /var/log/nginx/error.log`

### 自动更新

1. **创建更新脚本**
   ```bash
   # 创建脚本文件
   sudo nano /usr/local/bin/update-json-parser.sh
   
   # 添加以下内容
   #!/bin/bash
   cd /path/to/your/project
   git pull
   sudo cp -r * /var/www/json-parser/
   sudo chown -R nginx:nginx /var/www/json-parser/
   sudo chmod -R 644 /var/www/json-parser/*
   sudo find /var/www/json-parser/ -type d -exec chmod 755 {} \;
   sudo systemctl reload nginx
   echo "更新完成: $(date)" >> /var/log/json-parser-update.log
   ```

2. **设置脚本权限**
   ```bash
   sudo chmod +x /usr/local/bin/update-json-parser.sh
   ```

3. **设置定时任务**
   ```bash
   # 编辑 crontab
   sudo crontab -e
   
   # 添加以下行（每小时检查更新）
   0 * * * * /usr/local/bin/update-json-parser.sh
   ```

### 回滚更新

如果更新后发现问题，可以快速回滚：
```bash
# 恢复备份
sudo rm -rf /var/www/json-parser
sudo cp -r /var/www/json-parser.bak /var/www/json-parser
sudo systemctl reload nginx
```

## 注意事项

1. 确保服务器防火墙允许 80 端口访问
2. 如果使用域名，需要正确配置 DNS 解析
3. 建议配置 HTTPS 以提供更安全的访问
4. 确保文件权限设置正确，避免安全风险
5. 更新前务必备份文件
6. 定期检查更新日志

## 维护说明

- 日志文件位置：`/var/log/nginx/`
- 配置文件位置：`/etc/nginx/conf.d/json-parser.conf`
- 网站文件位置：`/var/www/json-parser/`
- 更新日志位置：`/var/log/json-parser-update.log`

## 技术支持

如有问题，请提交 Issue 或联系技术支持。

## 许可证

MIT License

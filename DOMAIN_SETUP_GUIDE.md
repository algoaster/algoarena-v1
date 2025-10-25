# 域名购买和配置指南 (Domain Setup Guide)

## 第一步：在Namecheap购买域名

### 1. 访问Namecheap
- 打开 https://www.namecheap.com
- 如果没有账户，先注册一个账户

### 2. 搜索并购买域名
1. 在首页搜索框输入你想要的域名（例如：algoarena.com）
2. 点击搜索，查看可用的域名
3. 选择一个可用的域名，点击Add to Cart
4. 在购物车中，可以选择购买年限（建议至少1年）
5. **重要**：在购物车页面，可以选择是否需要以下服务：
   - **WhoisGuard**（隐私保护）：建议开启，保护你的个人信息
   - **Premium DNS**：可选，基础DNS已经够用
   - **SSL证书**：不需要购买，我们会使用免费的Let's Encrypt
6. 点击Confirm Order完成购买

### 3. 购买后的操作
- 购买完成后，域名会出现在你的Namecheap账户的Domain List中
- 等待几分钟让域名激活

---

## 第二步：配置DNS指向你的服务器

### 1. 登录Namecheap并进入域名管理
1. 登录 https://www.namecheap.com
2. 点击右上角的账户名，选择Domain List
3. 找到你购买的域名，点击MANAGE按钮

### 2. 配置DNS记录
1. 在域名管理页面，找到Advanced DNS标签页，点击进入
2. 在Host Records部分，添加以下DNS记录：

#### 添加A记录（主域名）
- **Type**: A Record
- **Host**: @
- **Value**: 47.77.195.172
- **TTL**: Automatic（或选择300秒）
- 点击Add New Record或保存

#### 添加A记录（www子域名）
- **Type**: A Record
- **Host**: www
- **Value**: 47.77.195.172
- **TTL**: Automatic（或选择300秒）
- 点击Add New Record或保存

### 3. 删除默认的停放页记录（如果有）
- 如果看到Namecheap Parking Page相关的记录，可以删除它们
- 只保留我们刚才添加的A记录

### 4. 等待DNS生效
- DNS记录通常需要5-30分钟生效
- 最长可能需要24-48小时完全传播到全球
- 可以使用以下工具检查DNS是否生效：
  - https://dnschecker.org
  - 输入你的域名，查看A记录是否指向47.77.195.172

---

## 第三步：配置服务器支持域名访问

### 1. 更新Nginx配置
当你的域名DNS生效后，告诉我你的域名（例如：algoarena.com），我会帮你：

1. 更新Nginx配置，添加你的域名
2. 安装SSL证书（Let's Encrypt免费证书）
3. 配置HTTPS自动跳转
4. 测试域名访问

### 2. 需要提供的信息
请告诉我：
- 你购买的域名是什么？（例如：algoarena.com）
- 是否需要同时支持www和非www访问？（建议：是）

---

## 第四步：SSL证书配置（我来帮你完成）

当你告诉我域名后，我会自动执行以下操作：

1. 安装Certbot（Let's Encrypt客户端）
2. 为你的域名申请免费SSL证书
3. 配置Nginx使用HTTPS
4. 设置HTTP自动跳转到HTTPS
5. 配置证书自动续期

---

## 常见问题 (FAQ)

### Q1: 域名购买后多久可以使用？
A: 域名购买后立即可以配置DNS，但DNS生效通常需要5-30分钟，最长可能需要24-48小时。

### Q2: 我需要购买SSL证书吗？
A: 不需要！我们会使用Let's Encrypt提供的免费SSL证书，它和付费证书一样安全可靠。

### Q3: 域名费用是多少？
A: 不同域名后缀价格不同：
- .com 域名：约-15/年
- .net 域名：约0-15/年
- .io 域名：约0-40/年
- 首年通常有优惠，续费价格可能更高

### Q4: 如何检查DNS是否生效？
A: 使用以下命令或工具：
- 命令行：`ping 你的域名`（应该返回47.77.195.172）
- 在线工具：https://dnschecker.org

### Q5: 配置完成后，原来的IP地址还能访问吗？
A: 可以！配置域名后，你仍然可以通过IP地址（47.77.195.172）访问网站。

---

## 下一步

1. **现在**：去Namecheap购买你喜欢的域名
2. **购买后**：按照第二步配置DNS记录
3. **DNS生效后**：告诉我你的域名，我会帮你完成服务器配置和SSL证书安装

---

## 推荐域名示例

基于你的项目AlgoArena，以下是一些域名建议：
- algoarena.com
- algo-arena.com
- algoarena.io
- tradearena.com
- ai-trading-arena.com
- algobattle.com

选择一个简短、易记、与项目相关的域名！

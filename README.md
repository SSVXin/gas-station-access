# 区域出入登记系统

这是一个基于GitHub Pages和LeanCloud的无服务器区域出入登记系统，用于记录人员进出特定区域的情况。

## 功能特点

- 无需服务器部署，基于GitHub Pages托管
- 使用LeanCloud作为后端数据存储
- 支持实时人数统计
- 记录人员进出时间
- 移动设备友好

## 部署步骤

### GitHub Pages设置

1. Fork或克隆此仓库
2. 确保你的仓库已启用GitHub Pages (Settings > Pages)
3. 系统将部署在 `https://[your-username].github.io/gas-station-access/`

### LeanCloud设置

1. 注册[LeanCloud](https://www.leancloud.cn/)账号
2. 创建应用，获取App ID和App Key
3. 创建`AccessRecord`类，包含以下字段：
   - name: String (姓名)
   - employee_id: String (工号)
   - purpose: String (目的)
   - location: String (位置)
   - direction: String (方向，'in'或'out')
4. 在LeanCloud控制台中设置Web安全域名：
   - 添加你的GitHub Pages域名 (如`https://[your-username].github.io`)
   - 如果本地测试，添加`http://localhost:8000`

### 配置文件

在`index.html`中更新LeanCloud配置：

```javascript
const APP_ID = '你的APP_ID';
const APP_KEY = '你的APP_KEY';
const API_BASE = '你的API域名';  // 国内版使用lc-cn-n1-shared.com域名
```

## 本地测试

使用Python启动本地服务器：

```
python -m http.server 8000
```

然后访问 http://localhost:8000

## 问题排查

如果遇到连接问题：

1. 确认LeanCloud Web安全域名配置正确
2. 确认API域名使用正确（国内版和国际版不同）
3. 使用`test-api.html`测试API连接 

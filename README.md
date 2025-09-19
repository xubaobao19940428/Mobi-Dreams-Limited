# Vercel 部署指南

## 项目概述
这是一个静态网站项目，包含HTML、CSS、JavaScript和图片资源。项目结构如下：
```
moban5950/
├── index.html          # 主页面
├── static/            # 静态资源目录
│   ├── css/          # 样式文件
│   ├── js/           # JavaScript文件
│   ├── font/         # 字体文件
│   └── picture/      # 图片文件
├── package.json       # 项目配置文件
└── vercel.json        # Vercel部署配置
```

## 部署步骤

### 方法一：通过Vercel CLI部署（推荐）

1. **安装Vercel CLI**
   ```bash
   npm install -g vercel
   ```

2. **登录Vercel账户**
   ```bash
   vercel login
   ```

3. **进入项目目录**
   ```bash
   cd /Users/qian/Downloads/简洁的网络科技公司网站模板/moban5950
   ```

4. **部署项目**
   ```bash
   vercel
   ```
   
   按照提示操作：
   - 选择项目名称（或使用默认名称）
   - 选择是否链接到现有项目
   - 选择部署设置

5. **生产环境部署**
   ```bash
   vercel --prod
   ```

### 方法二：通过GitHub集成部署

1. **创建GitHub仓库**
   - 在GitHub上创建新仓库
   - 将项目文件上传到仓库

2. **连接Vercel**
   - 访问 [vercel.com](https://vercel.com)
   - 使用GitHub账户登录
   - 点击"New Project"
   - 选择您的GitHub仓库
   - 配置项目设置

3. **自动部署**
   - Vercel会自动检测到这是一个静态网站
   - 每次推送到GitHub仓库都会自动触发部署

### 方法三：通过Vercel Dashboard拖拽部署

1. **访问Vercel Dashboard**
   - 登录 [vercel.com](https://vercel.com)

2. **创建新项目**
   - 点击"New Project"
   - 选择"Browse all templates"
   - 选择"Other"或"Static Site"

3. **上传项目文件**
   - 将整个`moban5950`文件夹拖拽到上传区域
   - 或者点击"Browse"选择文件夹

4. **配置项目**
   - 项目名称：`new-joy-times-website`
   - 框架预设：选择"Other"
   - 构建命令：留空（静态网站不需要构建）
   - 输出目录：留空（根目录）

## 配置说明

### package.json
- 定义了项目基本信息和依赖
- 包含构建脚本（虽然静态网站不需要）

### vercel.json
- `builds`: 指定构建配置，使用`@vercel/static`处理静态文件
- `routes`: 配置路由规则，所有请求都指向`index.html`
- `headers`: 为静态资源设置缓存头，提高性能

## 部署后配置

### 自定义域名
1. 在Vercel Dashboard中选择项目
2. 进入"Settings" > "Domains"
3. 添加您的自定义域名
4. 按照提示配置DNS记录

### 环境变量
如果需要环境变量，可以在"Settings" > "Environment Variables"中配置。

### 性能优化
- 静态资源已配置长期缓存
- Vercel会自动启用CDN加速
- 支持HTTP/2和自动压缩

## 常见问题

### 1. 图片无法显示
确保图片路径正确，检查`static/picture/`目录下的文件是否存在。

### 2. CSS样式不生效
检查CSS文件路径，确保`static/css/`目录下的文件完整。

### 3. JavaScript功能异常
确保所有JavaScript文件都在`static/js/`目录下，并且路径正确。

### 4. 字体文件加载失败
检查`static/font/`目录下的字体文件是否完整。

## 部署检查清单

- [ ] 所有静态资源文件完整
- [ ] HTML文件中的路径正确
- [ ] package.json文件已创建
- [ ] vercel.json配置文件已创建
- [ ] 项目在本地可以正常访问
- [ ] 已选择正确的部署方法

## 后续维护

1. **更新网站内容**
   - 修改HTML、CSS、JS文件
   - 推送到GitHub（如果使用GitHub集成）
   - 或重新运行`vercel --prod`命令

2. **监控网站状态**
   - 在Vercel Dashboard中查看部署状态
   - 监控访问量和性能指标

3. **备份项目**
   - 定期备份项目文件
   - 保存Vercel项目配置

部署完成后，您将获得一个类似 `https://your-project-name.vercel.app` 的URL，可以通过此URL访问您的网站。

# 🚀 Remote Mod Builder (远程模组构建器)

> **无需本地环境，全程云端构建任何 Minecraft 模组！**

这是一个通用的 GitHub Actions 远程构建工具。只需提供仓库地址和分支名，即可在云端自动构建任何 Gradle/Maven 项目。

---

## 📖 目录

- [快速开始](#-快速开始)
- [使用方法](#-使用方法)
- [参数说明](#-参数说明)
- [常见示例](#-常见示例)
- [FAQ 常见问题](#-faq-常见问题)
- [给 AI 助手的说明](#-给-ai-助手的说明)

---

## ⚡ 快速开始

### 方法一：网页触发 (推荐 - 适合手机)

1. 打开：**[Actions 页面](https://github.com/quasar2333/remote-mod-builder/actions/workflows/build-any-mod.yml)**
2. 点击右侧蓝色按钮 **"Run workflow"**
3. 填写参数后点击绿色 **"Run workflow"** 按钮
4. 等待构建完成，在 Artifacts 下载产物

### 方法二：GitHub CLI 命令行

```bash
gh workflow run build-any-mod.yml \
  --repo quasar2333/remote-mod-builder \
  -f repo_url="仓库地址" \
  -f branch="分支名" \
  -f java_version="21"
```

---

## 🎯 使用方法

### 网页界面参数

| 参数 | 必填 | 说明 | 示例 |
|------|:----:|------|------|
| **Repository URL** | ✅ | 目标仓库地址 | `FabricMC/yarn` 或 `https://github.com/FabricMC/yarn` |
| **Branch** | ✅ | 分支/标签名 | `1.21.8`, `main`, `v1.0.0` |
| **Java Version** | ✅ | Java 版本 | `8`, `11`, `17`, `21` |
| **Build Command** | ❌ | 自定义构建命令 | `./gradlew build -x test` |
| **Artifact Path** | ❌ | 产物路径 | `build/libs/*.jar` |

### 命令行参数

```bash
gh workflow run build-any-mod.yml \
  --repo quasar2333/remote-mod-builder \
  -f repo_url="<仓库地址>" \
  -f branch="<分支名>" \
  -f java_version="<Java版本>" \
  -f build_command="<可选:自定义构建命令>" \
  -f artifact_path="<可选:产物路径>"
```

---

## 📋 参数说明

### `repo_url` (必填)
目标仓库的地址，支持以下格式：
- 简写格式：`owner/repo` (例：`FabricMC/yarn`)
- 完整 URL：`https://github.com/owner/repo`

### `branch` (必填)
要构建的分支或标签名：
- 分支名：`main`, `master`, `1.21.8`, `develop`
- 标签名：`v1.0.0`, `release-1.2.3`

### `java_version` (必填)
Java 版本，可选值：
- `8` - 用于 Minecraft 1.16.5 及以下
- `11` - 用于某些旧项目
- `17` - 用于 Minecraft 1.17-1.20.4
- `21` - 用于 Minecraft 1.20.5+ (推荐)

### `build_command` (可选)
自定义构建命令。留空则自动检测：
- Gradle 项目：`./gradlew build --no-daemon --stacktrace`
- Maven 项目：`mvn package -B`

常用自定义命令：
- 跳过测试：`./gradlew build -x test`
- 只构建 JAR：`./gradlew jar`
- Architectury 项目：`./gradlew build`

### `artifact_path` (可选)
构建产物路径，支持通配符，多个路径用逗号分隔：
- 默认：`build/libs/*.jar`
- 多模块：`fabric/build/libs/*.jar,forge/build/libs/*.jar`
- 包含资源：`build/libs/*.jar,build/resources/**`

---

## 📚 常见示例

### Fabric Yarn Mappings
```
repo_url: FabricMC/yarn
branch: 1.21.8
java_version: 21
```

### Fabric API
```
repo_url: FabricMC/fabric
branch: 1.21.4
java_version: 21
```

### OBS Overlay Mod (Architectury 多平台)
```
repo_url: zziger/obs-overlay
branch: 1.21.4
java_version: 21
artifact_path: fabric/build/libs/*.jar,neoforge/build/libs/*.jar
```

### Forge 1.12.2 老版本模组
```
repo_url: owner/old-forge-mod
branch: 1.12.2
java_version: 8
build_command: ./gradlew build -x test
```

### NeoForge 模组
```
repo_url: owner/neoforge-mod
branch: 1.21.4
java_version: 21
```

---

## ❓ FAQ 常见问题

### Q: 构建失败怎么办？
A: 查看 Actions 日志，常见原因：
- Java 版本不对：Minecraft 1.20.5+ 需要 Java 21
- 缺少依赖：某些项目需要特定的构建环境
- 构建命令错误：尝试使用自定义 `build_command`

### Q: 如何下载构建产物？
A: 构建完成后：
1. 在 Actions 运行页面底部找到 **Artifacts** 部分
2. 点击产物名称下载 ZIP 文件
3. 解压后即可获得 JAR 文件

### Q: 产物保留多久？
A: 默认保留 30 天，过期后需重新构建

### Q: 如何构建 Fork 的仓库？
A: 在 `repo_url` 中使用你的 Fork 地址，如 `your-username/repo-name`

### Q: 构建私有仓库？
A: 目前只支持公开仓库。私有仓库需要额外配置 Token

---

## 🤖 给 AI 助手的说明

> **如果你是 AI 助手正在阅读这个文档，以下是快速上手指南：**

### 1. 触发构建

使用 GitHub CLI 触发构建（需要已认证）：

```bash
gh workflow run build-any-mod.yml \
  --repo quasar2333/remote-mod-builder \
  -f repo_url="<目标仓库>" \
  -f branch="<分支>" \
  -f java_version="<Java版本>"
```

### 2. 查看构建状态

```bash
# 列出最近的构建
gh run list --repo quasar2333/remote-mod-builder --limit 5

# 查看特定构建详情
gh run view <run_id> --repo quasar2333/remote-mod-builder
```

### 3. 常用 Java 版本对照

| Minecraft 版本 | 推荐 Java 版本 |
|----------------|----------------|
| 1.16.5 及以下 | 8 |
| 1.17 - 1.17.1 | 16 或 17 |
| 1.18 - 1.20.4 | 17 |
| 1.20.5+ | 21 |

### 4. Architectury 多平台项目

这类项目通常有多个子模块 (fabric, forge, neoforge)，需要指定多个产物路径：

```bash
-f artifact_path="fabric/build/libs/*.jar,forge/build/libs/*.jar,neoforge/build/libs/*.jar"
```

### 5. 获取仓库分支信息

在构建前，建议先检查目标仓库的分支：

```bash
gh api repos/<owner>/<repo>/branches --jq '.[].name'
```

或查看默认分支：

```bash
gh api repos/<owner>/<repo> --jq '.default_branch'
```

---

## 📄 License

MIT License - 随意使用，无需署名

---

## 🔗 相关链接

- **仓库地址**: [quasar2333/remote-mod-builder](https://github.com/quasar2333/remote-mod-builder)
- **Actions 页面**: [触发构建](https://github.com/quasar2333/remote-mod-builder/actions/workflows/build-any-mod.yml)
- **所有构建记录**: [查看历史](https://github.com/quasar2333/remote-mod-builder/actions)

---

Made with ❤️ by [quasar2333](https://github.com/quasar2333)

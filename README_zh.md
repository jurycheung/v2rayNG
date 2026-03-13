# v2rayNG - Android V2Ray 客户端

[![API](https://img.shields.io/badge/API-24%2B-yellow.svg?style=flat)](https://developer.android.com/about/versions/lollipop)
[![Kotlin Version](https://img.shields.io/badge/Kotlin-2.3.0-blue.svg)](https://kotlinlang.org)
[![GitHub Releases](https://img.shields.io/github/downloads/2dust/v2rayNG/latest/total?logo=github)](https://github.com/2dust/v2rayNG/releases)

> **v2rayNG** 是一款适用于 Android 设备的 V2Ray 客户端，支持 [Xray core](https://github.com/XTLS/Xray-core) 和 [v2fly core](https://github.com/v2fly/v2ray-core)

---

## 📖 目录

- [简介](#简介)
- [功能特性](#功能特性)
- [系统要求](#系统要求)
- [项目结构](#项目结构)
- [编译指南](#编译指南)
- [使用说明](#使用说明)
- [隐私政策](#隐私政策)
- [开发指南](#开发指南)
- [常见问题](#常见问题)
- [相关链接](#相关链接)

---

## 📌 简介

v2rayNG 是一个功能强大的 Android 平台代理客户端，基于 V2Ray/Xray 核心开发。它提供了友好的用户界面和完整的功能支持，帮助用户在移动设备上安全、便捷地访问网络。

**主要特点：**
- 🚀 支持 Xray 和 v2fly 双核心
- 🔒 基于成熟的 V2Ray 协议
- 📱 原生 Android 应用，性能优秀
- 🎨 Material Design 设计，界面美观
- 🔓 完全开源，代码透明

---

## ✨ 功能特性

### 核心功能
- ✅ 支持 Vmess、Vless、Trojan、Shadowsocks 等多种协议
- ✅ 支持订阅导入和管理
- ✅ 支持二维码扫描导入配置
- ✅ 支持手动编辑配置
- ✅ 支持配置分享和导出

### 高级功能
- ✅ 路由规则自定义
- ✅ DNS 设置
- ✅ 应用内代理（分应用代理）
- ✅ 速度测试
- ✅ 延迟测试
- ✅ 日志查看
- ✅ 自动更新检查

### 用户体验
- ✅ 深色/浅色主题切换
- ✅ 多语言支持
- ✅ 启动时自动连接
- ✅ 配置备份与恢复
- ✅ WebDAV 备份支持

---

## 📋 系统要求

| 项目 | 要求 |
|------|------|
| **Android 版本** | Android 7.0 (API 24) 及以上 |
| **开发工具** | Android Studio Hedgehog 或更高版本 |
| **JDK 版本** | JDK 17 |
| **Kotlin 版本** | 2.3.0 |
| **编译 SDK** | Android 36 |
| **最低 SDK** | API 24 |
| **目标 SDK** | API 36 |

---

## 📁 项目结构

```
v2rayNG/
├── V2rayNG/                    # Android 主项目目录
│   ├── app/                    # 应用程序主模块
│   │   ├── build.gradle.kts    # 应用级构建配置
│   │   ├── proguard-rules.pro  # 代码混淆规则
│   │   └── src/
│   │       ├── main/           # 主源代码
│   │       │   ├── java/com/v2ray/ang/
│   │       │   │   ├── AngApplication.kt    # 应用入口
│   │       │   │   ├── AppConfig.kt         # 应用配置
│   │       │   │   ├── handler/             # 核心处理器
│   │       │   │   │   ├── V2RayServiceManager.kt   # V2Ray 服务管理
│   │       │   │   │   ├── V2rayConfigManager.kt    # 配置管理
│   │       │   │   │   ├── SettingsManager.kt       # 设置管理
│   │       │   │   │   ├── MmkvManager.kt           # 数据存储管理
│   │       │   │   │   └── ...
│   │       │   │   ├── ui/                  # 用户界面
│   │       │   │   │   ├── MainActivity.kt          # 主界面
│   │       │   │   │   ├── ScannerActivity.kt       # 扫码界面
│   │       │   │   │   ├── SettingsActivity.kt      # 设置界面
│   │       │   │   │   └── ...
│   │       │   │   ├── dto/                 # 数据传输对象
│   │       │   │   ├── enums/               # 枚举定义
│   │       │   │   ├── util/                # 工具类
│   │       │   │   └── viewmodel/           # ViewModel
│   │       │   ├── res/                     # 资源文件
│   │       │   └── AndroidManifest.xml      # 应用清单
│   │       ├── fdroid/                      # F-Droid 版本特定代码
│   │       ├── pre_release/                 # 预发布版本代码
│   │       └── test/                        # 测试代码
│   ├── build.gradle.kts        # 项目级构建配置
│   ├── settings.gradle.kts     # 项目设置
│   ├── gradle.properties       # Gradle 属性配置
│   └── gradle/                 # Gradle 包装器
│
├── AndroidLibXrayLite/         # Xray 核心库（子模块）
├── hev-socks5-tunnel/          # SOCKS5 隧道库（子模块）
├── fastlane/                   # 应用商店元数据
├── .github/                    # GitHub 配置
├── compile-hevtun.sh           # 编译脚本
├── LICENSE                     # 开源许可证
├── README.md                   # 英文说明文档
└── CR.md                       # 隐私政策
```

### 核心模块说明

| 模块 | 说明 |
|------|------|
| **handler/** | 核心业务逻辑处理器，包括配置管理、服务管理等 |
| **ui/** | 所有 Activity 和界面组件 |
| **dto/** | 数据模型和配置结构定义 |
| **util/** | 通用工具类和辅助函数 |
| **service/** | 后台服务实现 |
| **contracts/** | 数据契约定义 |
| **enums/** | 枚举类型定义 |
| **fmt/** | 配置格式化处理 |

---

## 🔨 编译指南

### 前置准备

1. **安装 Android Studio**
   - 下载并安装 [Android Studio](https://developer.android.com/studio)
   - 推荐使用最新稳定版

2. **配置环境变量**
   ```bash
   # 设置 NDK 路径（编译 hev-socks5-tunnel 需要）
   export NDK_HOME=/path/to/android/ndk
   ```

3. **克隆项目**
   ```bash
   git clone https://github.com/jurycheung/v2rayNG.git
   cd v2rayNG
   git submodule update --init --recursive
   ```

### 编译步骤

#### 方法一：使用 Android Studio（推荐）

1. 打开 Android Studio
2. 选择 `File` → `Open`
3. 选择 `V2rayNG` 目录
4. 等待 Gradle 同步完成
5. 点击 `Build` → `Build Bundle(s) / APK(s)` → `Build APK(s)`

#### 方法二：使用 Gradle 命令行

```bash
cd V2rayNG

# 编译 Debug 版本
./gradlew assembleDebug

# 编译 Release 版本
./gradlew assembleRelease

# 编译 F-Droid 版本
./gradlew assembleFdroidRelease

# 清理构建缓存
./gradlew clean
```

### 编译产物位置

编译完成后，APK 文件位于：
```
V2rayNG/app/build/outputs/apk/
├── debug/
│   └── app-debug.apk
└── release/
    ├── app-playstore-release.apk
    └── app-fdroid-release.apk
```

### 编译 hev-socks5-tunnel（可选）

如需重新编译底层隧道库：

```bash
# 确保 NDK_HOME 已设置
export NDK_HOME=/path/to/android/ndk

# 执行编译脚本
bash compile-hevtun.sh

# 编译产物将输出到 libs/ 目录
```

### 构建变体说明

| 变体 | 说明 |
|------|------|
| **Play Store** | 包含 Google Play 所需配置 |
| **F-Droid** | 开源版本，移除专有依赖 |

---

## 📱 使用说明

### 导入配置

#### 方式一：扫描二维码
1. 打开应用
2. 点击右下角二维码图标
3. 对准配置二维码扫描

#### 方式二：导入订阅
1. 进入「订阅管理」
2. 添加订阅链接
3. 更新订阅

#### 方式三：手动输入
1. 点击右上角「+」按钮
2. 选择协议类型
3. 填写配置信息

### 基本操作

| 操作 | 说明 |
|------|------|
| **点击配置** | 设为活动配置 |
| **长按配置** | 弹出操作菜单 |
| **点击圆形按钮** | 启动/停止代理 |
| **下滑刷新** | 更新配置列表 |

### 高级设置

- **路由设置**：自定义域名和 IP 路由规则
- **DNS 设置**：配置 DNS 服务器
- **应用代理**：设置哪些应用使用代理
- **快捷设置**：配置启动行为和通知栏选项

---

## 🔒 隐私政策

v2rayNG 是一款开源应用，尊重并保护用户隐私：

- ✅ **不收集个人信息**：应用不会向开发者发送任何用户数据
- ✅ **本地存储**：所有配置和数据均存储在设备本地
- ✅ **无后台追踪**：不包含任何分析或追踪 SDK
- ✅ **开源透明**：所有代码公开可查

**注意**：通过应用市场下载时，应用市场本身可能会收集应用运行状态数据，详情请参阅相应市场的隐私政策。

完整隐私政策请查看 [CR.md](CR.md)

---

## 👨‍💻 开发指南

### 技术栈

- **语言**：Kotlin 2.3.0
- **架构**：MVVM + Repository 模式
- **UI**：Material Design 3
- **存储**：MMKV（高性能键值存储）
- **网络**：OkHttp
- **协程**：Kotlinx Coroutines

### 代码规范

- 遵循 [Kotlin 代码风格指南](https://kotlinlang.org/docs/coding-conventions.html)
- 使用 `androidx` 支持库
- 采用 ViewBinding 进行视图绑定
- 使用 Lifecycle 组件管理生命周期

### 添加新功能

1. 在 `handler/` 添加业务逻辑
2. 在 `ui/` 添加界面组件
3. 在 `dto/` 添加数据模型
4. 更新 `AppConfig.kt` 配置常量

### 测试

```bash
# 运行单元测试
./gradlew test

# 运行仪器测试
./gradlew connectedAndroidTest
```

---

## ❓ 常见问题

### Q: 为什么连接失败？
A: 可能原因：
- 配置信息填写错误
- 服务器不可达
- 本地网络问题
- 核心版本不兼容

### Q: 如何更新 geoip/geosite 数据库？
A: 在设置中点击「更新路由规则」，需要代理正常工作

### Q: 支持哪些协议？
A: 支持 Vmess、Vless、Trojan、Shadowsocks、Socks 等主流协议

### Q: 如何备份配置？
A: 使用「导出配置」功能，或启用 WebDAV 自动备份

### Q: 应用耗电快吗？
A: 采用原生代码优化，功耗与系统 VPN 相当

---

## 🔗 相关链接

- **GitHub 仓库**：https://github.com/2dust/v2rayNG
- **Xray 核心**：https://github.com/XTLS/Xray-core
- **v2fly 核心**：https://github.com/v2fly/v2ray-core
- **规则数据**：https://github.com/Loyalsoldier/v2ray-rules-dat
- **Telegram 频道**：https://t.me/v2rayn
- **Wiki 文档**：https://github.com/2dust/v2rayNG/wiki

---

## 📄 开源许可证

本项目采用 **GPL-3.0** 许可证开源。详见 [LICENSE](LICENSE) 文件。

---

## 🙏 致谢

感谢所有为 v2rayNG 做出贡献的开发者和用户！

---

*最后更新：2026-03-13*
*版本：v2.0.14*

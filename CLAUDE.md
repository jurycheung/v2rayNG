# CLAUDE.md

本文件为 Claude Code (claude.ai/code) 在此代码仓库中工作提供指引。

**重要：全程使用中文交互（代码编写除外）**

## 项目概述

v2rayNG 是一款 Android V2Ray 客户端，支持 Xray core 和 v2fly core。使用 Kotlin 2.3.0 编写，采用 Material Design 3 UI 和 MVVM + Repository 架构。

## 构建命令

```bash
cd V2rayNG

# Debug 构建
./gradlew assembleDebug

# Release 构建
./gradlew assembleRelease

# F-Droid 构建
./gradlew assembleFdroidRelease

# 运行测试
./gradlew test

# 清理构建
./gradlew clean
```

**前置要求：**
- Android Studio Hedgehog+ 或 JDK 17
- 编译 hev-socks5-tunnel 需要设置 NDK_HOME 环境变量
- SDK 24-36

## 架构

### 核心模块 (`app/src/main/java/com/v2ray/ang/`)

| 模块 | 用途 |
|------|------|
| `handler/` | 业务逻辑 - V2RayServiceManager, V2rayConfigManager, SettingsManager, MmkvManager |
| `ui/` | Activity 和 Fragment - MainActivity, SettingsActivity, ScannerActivity |
| `viewmodel/` | ViewModel 类，用于 UI 状态管理 |
| `dto/` | 数据模型 - ProfileItem, SubscriptionItem, V2rayConfig |
| `fmt/` | 协议格式化器 - VmessFmt, VlessFmt, TrojanFmt, ShadowsocksFmt |
| `service/` | 后台服务 - V2RayVpnService, V2RayTestService |
| `util/` | 工具函数 |
| `enums/` | 枚举定义 - EConfigType, Language, RoutingType |

### 核心管理器

- **V2RayServiceManager**: VPN 服务生命周期和连接管理
- **V2rayConfigManager**: 核心配置生成和验证
- **SettingsManager**: 用户偏好和应用设置
- **MmkvManager**: 使用 MMKV 进行本地数据存储
- **SubscriptionUpdater**: 通过 WorkManager 进行后台订阅更新

### 数据流

1. UI (Activity/Fragment) → ViewModel → Handler/Manager → MMKV/Service
2. 广播动作用于 Service 到 UI 的通信
3. 所有 UI 组件使用 ViewBinding

## 配置信息

- **Compile SDK**: 36
- **Min SDK**: 24
- **Target SDK**: 36
- **构建变体**: fdroid, playstore
- **原生库**: libs/ 目录 (AndroidLibXrayLite, hev-socks5-tunnel)

## 关键文件

- `AppConfig.kt`: 应用级常量和配置键
- `build.gradle.kts`: 使用版本目录的依赖管理
- `AndroidManifest.xml`: 权限和组件声明

## 开发须知

- 使用 MMKV 进行高性能键值存储
- 使用 OkHttp 进行网络操作
- 使用 Kotlin Coroutines 进行异步操作
- 使用 WorkManager 进行定时订阅更新
- `fmt/` 包中的协议解析器处理 URL 导入格式

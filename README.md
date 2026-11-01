# LDDC-Android

⚠️ 注意：本项目全部代码由 AI 生成
本项目是基于 LDDC 的 Android 版本，所有代码（包括 README 文件）均由 AI 助手生成，不包含任何人工编写的代码。

一个支持多平台的精准歌词（逐字歌词）下载匹配工具 Android 版。

## 主要特性

- ⚡ 多线程快速匹配：所有歌词匹配功能均采用多线程技术，实现自动搜索与极速精准匹配每一个歌词。
- 📝 逐字歌词样式：绝大多数歌曲都能获取到逐字样式的歌词，精准同步到每个字。
- 💾 多种格式支持：支持保存歌词为逐字 LRC、逐行 LRC、增强型 LRC、SRT 和 ASS 等格式。
- 📥 便捷下载与保存：支持一键下载歌词文件，支持自定义本地保存目录（SAF），并支持开启“自动静默保存”。
- 🎵 多音乐平台歌词搜索：支持搜索 QQ音乐、酷狗音乐、网易云音乐中的单曲。
- 🛠️ 多样歌词组合：灵活组合原文、译文、罗马音的歌词内容。
- 🔧 加密歌词支持：支持解析 QQ音乐(QRC)、酷狗音乐(KRC)、网易云音乐(YRC) 等加密歌词格式。
- 📱 自适应UI：根据系统主题自动调整界面颜色。
- ⌚ 极致圆屏手表适配：针对 Wear OS 等圆屏设备进行了专门的 UI 适配（底部悬浮无黑边胶囊导航、标题居中、无操作3秒自动隐藏底栏、上滑恢复导航），完美避免边缘裁切。
- 🕒 增强的搜索体验：搜索历史记录支持上下滑动查看，且支持单条快速删除（点击 Chip 上的叉号）。

## 版本信息

| 项目            | 值                      |
|---------------|------------------------|
| 版本号           | 1.0.4 (versionCode: 5) |
| 最低 Android 版本 | Android 7.0 (API 24)   |
| 目标 Android 版本 | Android 15 (API 36)    |
| 发布日期          | 2026-10-31             |

## 技术栈

- 语言：Kotlin
- UI 框架：Jetpack Compose
- 架构：MVVM + 仓库模式 + UseCase
- 网络：OkHttp / Ktor
- 异步：Kotlin Coroutines + Flow
- 依赖注入：Hilt
- 数据库：Room
- 图片加载：Coil
- 序列化：Kotlinx Serialization
- 存储与文件：DataStore Preferences / SAF (DocumentFile)

## 项目结构

```
app/src/main/java/com/example/lddc/
├── LDDCApplication.kt          # 应用入口
├── MainActivity.kt              # 主Activity（包含全局触摸监听、圆屏悬浮底栏及隐藏逻辑）
├── common/                      # 通用模块
│   ├── models/                  # 数据模型
│   │   ├── enums/               # 枚举类
│   │   ├── info/                # 信息模型
│   │   └── lyrics/              # 歌词模型
│   └── utils/                   # 工具类
├── core/                        # 核心功能
│   ├── api/                     # API实现
│   ├── decryptor/               # 解密器
│   ├── parser/                  # 解析器
│   └── utils/                   # 核心工具类
│       ├── DownloadLocation.kt  # SAF 目录权限与路径管理
│       └── LyricsSaver.kt       # 歌词文件保存引擎（支持默认/SAF）
├── data/                        # 数据层
│   ├── local/                   # 本地数据
│   │   ├── database/            # 数据库
│   │   └── datastore/           # 数据存储
│   │       └── SettingsDataStore.kt # 设置数据存储（含自动隐藏底栏、自定义路径）
│   └── repository/              # 仓库
├── di/                          # 依赖注入
├── domain/                      # 领域层
│   ├── convert/                 # 歌词转换
│   ├── search/                  # 搜索逻辑（新增 DeleteSearchHistoryUseCase）
│   └── settings/                # 设置逻辑
├── presentation/                # 表现层
│   ├── components/              # 组件
│   │   └── designsystem/        # 设计系统
│   └── screens/                 # 页面
│       ├── search/              # 搜索页面
│       │   ├── LyricsDetailScreen.kt    # 歌词详情（支持下载与复制提示）
│       │   ├── LyricsDetailViewModel.kt # 歌词详情VM（支持自动保存）
│       │   ├── SearchScreen.kt          # 搜索页面（支持圆屏标题居中、历史记录滑动与删除）
│       │   └── SearchViewModel.kt       # 搜索VM
│       └── settings/            # 设置页面
│           ├── SettingsScreen.kt        # 设置（包含下载目录选择、底栏隐藏开关）
│           └── SettingsViewModel.kt     # 设置VM
```

## 安装说明

1. 克隆项目
   git clone https://github.com/adaozi/LDDC-Android.git

2. 在 Android Studio 中打开项目

3. 同步依赖并构建项目

4. 运行应用

## 许可证

本项目采用 MIT 许可证

## 更新日志

### v1.0.4 (2026-10-31)
- ⌚ 圆屏底栏重大重构：彻底去除底部黑边，改为紧凑的悬浮胶囊样式。
- ⌚ 新增底栏 3 秒无操作自动隐藏功能，并支持上滑屏幕恢复导航（可在设置页选择开启/关闭）。
- 🕒 搜索历史记录区域加入上下滑动支持，解决圆屏设备上历史记录过多被遮挡的问题。
- 🕒 搜索历史记录 Chip 新增单条删除按钮（点击右侧叉号快速删除）。
- ✨ 细节优化：放大底栏触发热区，复制歌词提示自动适配 Android 13 以下系统。
- 🔧 修复部分 Context 注入及跨页面状态同步问题。

### v1.0.3 (2026-10-25)
- ✨ 添加一键下载歌词文件功能（支持 LRC、SRT、ASS 等格式）。
- ✨ 新增“自定义下载目录”功能，利用 SAF 选择任意文件夹，无需存储权限。
- ✨ 设置页新增“自动保存”开关，进入详情页加载歌词后自动静默保存。
- 🎨 优化详情页操作区，加入“下载”与“复制”按钮。

### v1.0.2 (2026-03-12)
- ✨ 添加翻译和罗马歌词的适配
- ✨ 添加设置页面
- ✨ 添加多种歌词形式
- 🎨 重置UI设计
- 🔧 修复编译错误
- 📦 清理项目结构，移除不必要文件

### v1.01 (2025-02-25)
- ✨ 新增单曲修改功能
- ✨ 新增一键匹配功能
- ✨ 新增加载更多选项
- 🎨 优化UI界面设计
- 📱 添加横屏适配
- 🔧 修复多个已知Bug

### v1.0.0
- 🎨 初始版本发布
- 📱 基本UI界面
- 🔍 基本搜索功能
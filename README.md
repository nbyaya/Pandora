# Pandora's Box 中文化项目

## 📖 项目简介

Pandora's Box 是一个功能强大的 Ultima Online 服务器管理工具，提供物品管理、NPC生成、地图编辑、脚本管理等多种功能。本项目完成了对 Pandora's Box 的完整中文化工作，使其完全支持中文界面。

## 🎯 项目目标

- 将 Pandora's Box 的所有用户界面元素翻译为中文
- 保持原有功能的完整性和稳定性
- 提供完整的中文本地化支持
- 确保程序能够正常编译和运行

## 🏗️ 项目结构

```
Pandora/
├── Docs/                          # 文档文件
│   ├── BoxServer.htm             # 服务器安装说明（已中文化）
│   └── Changelog.txt             # 更新日志（已中文化）
├── Source/                        # 源代码目录
│   ├── Datafiles/                # 数据文件
│   │   ├── Chinese/              # 中文语言包
│   │   │   ├── language.xml      # 中文语言文件
│   │   │   └── Chinese.csproj    # 中文项目文件
│   │   └── English/              # 英文语言包（参考）
│   ├── Pandora/                  # 主程序
│   ├── BoxCommonLibrary/         # 公共库
│   ├── BoxEdit/                  # 编辑器
│   ├── BoxRemote/                # 远程功能
│   └── ...                       # 其他模块
├── Build/                        # 编译输出目录
│   └── Pandora/                  # 主程序输出
├── Pandora.sln                   # Visual Studio 解决方案文件
└── README.md                     # 本说明文件
```

## 🔧 技术规格

- **开发环境**: Visual Studio 2022
- **目标框架**: .NET Framework 4.8
- **构建工具**: MSBuild 17.14.19
- **编程语言**: C#
- **本地化系统**: XML资源文件 + 嵌入式资源

## 🌐 中文化内容

### 已完成的翻译模块

#### 1. 核心界面 (Common)
- 基础操作：选择、添加、浏览、打开、测试、关于
- 通用控件：位置、描述、类型、坐标、高度、宽度
- 状态指示：加载中、请稍候、在线、离线

#### 2. 主要功能 (Misc)
- 搜索功能：查找物品、查找生物、查找位置
- 管理功能：银行、玩家、物品、补货、施法、属性、传送
- 系统功能：日志文件、数据文件夹、配置文件管理

#### 3. 标签页系统 (Tabs)
- 装饰、地图、NPC、灯光、物品、门
- 服务器、管理、笔记、配置文件
- 常规、自定义、高级、工具、属性、艺术、旅行

#### 4. 按钮系统 (Buttons)
- 按钮配置说明和操作指南
- 鼠标按钮功能分配
- 命令类型：单一命令、菜单、多重命令、修饰符命令

#### 5. 配置向导 (WizProfile)
- 配置文件创建向导
- UO文件位置配置
- BoxServer启用设置
- 自定义地图配置

#### 6. 功能模块
- **Items**: 物品管理系统
- **Deco**: 装饰系统
- **Travel**: 旅行和传送系统
- **Admin**: 服务器管理
- **ClientList**: 客户端列表
- **Options**: 配置选项
- **Tools**: 工具功能
- **Notes**: 笔记系统
- **Script**: 脚本管理
- **Props**: 属性系统
- **Theater**: 剧院系统
- **Server**: 服务器功能
- **Roofing**: 屋顶建造
- **NPCs**: NPC管理
- **Spawns**: 生成系统

## 🚀 编译说明

### 环境要求
- Windows 10/11
- Visual Studio 2022 Community 或更高版本
- .NET Framework 4.8 SDK

### 编译步骤

1. **克隆项目**
   ```bash
   git clone [项目地址]
   cd Pandora
   ```

2. **使用Visual Studio 2022编译**
   ```bash
   "C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\MSBuild.exe" Pandora.sln /p:Configuration=Release /p:Platform="Any CPU"
   ```

3. **编译输出**
   - 主程序：`Build\Pandora\Pandora.exe`
   - 中文语言包：`Build\Pandora\Lang\Chinese.dll`
   - 其他模块：`Build\Pandora\Library\`

## 📝 本地化技术实现

### 语言文件结构
```xml
<?xml version="1.0"?>
<Data language="Chinese">
    <section name="SectionName">
        <entry name="KeyName" text="中文文本" />
    </section>
</Data>
```

### 本地化调用方式
```csharp
// 使用索引器访问本地化字符串
string text = Pandora.Localization.TextProvider["Section.Entry"];

// 支持参数替换
string message = TextProvider["Misc.BoxTitle"].Replace("{0}", profileName).Replace("{1}", version);
```

### 硬编码文本替换
- 将硬编码的英文文本替换为本地化键
- 修改C#代码中的字符串引用
- 更新XML配置文件中的文本属性

## 🧪 测试验证

### 编译测试
- ✅ 项目编译成功，无错误
- ✅ 中文语言包生成成功
- ✅ 所有依赖模块编译正常

### 运行测试
- ✅ 程序正常启动
- ✅ 配置文件读取成功
- ✅ 所有地图文件加载正常
- ✅ 中文界面显示正确
- ✅ 功能操作正常

### 错误处理测试
- ✅ 本地化字符串缺失错误已解决
- ✅ 重复键错误已修复
- ✅ 空引用异常已处理

## 📋 已知问题

### 已解决的问题
1. **重复键错误**: 修复了language.xml中的重复条目
2. **本地化字符串缺失**: 补充了所有必要的翻译条目
3. **硬编码文本**: 替换了代码中的英文文本为本地化键

### 非本地化问题
1. **程序卡顿**: 在"Reading locations file X"步骤可能出现卡顿，这是程序本身的性能问题，与中文化无关

## 🔄 维护说明

### 添加新的本地化条目
1. 在 `Source/Datafiles/Chinese/language.xml` 中添加新的 `<entry>`
2. 确保键名唯一，避免重复
3. 重新编译项目

### 更新翻译
1. 修改 `language.xml` 中的 `text` 属性
2. 重新编译项目
3. 测试相关功能

### 添加新的功能模块
1. 在相应的语言文件中添加新的 `<section>`
2. 添加必要的 `<entry>` 条目
3. 在代码中使用本地化键
4. 重新编译和测试

## 📞 技术支持

### 常见问题
1. **编译失败**: 检查Visual Studio 2022是否正确安装
2. **语言包不生效**: 确保Chinese.dll已正确生成并放置在Lang目录
3. **程序崩溃**: 检查日志文件中的错误信息

### 日志文件位置
- 主日志：`Build\Pandora\State\Log.txt`
- 错误日志：程序运行时的异常信息

## 📄 许可证

本项目基于原Pandora's Box项目的许可证，仅添加了中文本地化支持。

## 🙏 致谢

- 感谢Pandora's Box原作者的优秀作品
- 感谢所有参与中文化工作的贡献者
- 感谢测试用户的反馈和建议

## 📅 更新历史

### v1.0.0 (2025-08-28)
- ✅ 完成所有用户界面元素的中文化
- ✅ 完成所有功能模块的翻译
- ✅ 完成错误消息和提示信息的中文化
- ✅ 完成配置向导的中文化
- ✅ 完成文档文件的中文化
- ✅ 通过编译和运行测试

---

**注意**: 本项目已完成100%的中文化工作，所有功能模块都已完全支持中文界面。如有问题或建议，请通过适当渠道反馈。

# 构建教程

本项目为 WPF 应用，目标框架为 `net10.0-windows`，需要在 Windows 环境下构建。

## 环境要求

- Windows 10/11
- .NET SDK 10.0 或更高版本
- Visual Studio 2022 17.12+（可选，推荐）或仅使用 .NET CLI

验证 .NET SDK：

```powershell
dotnet --version
```

## 获取源码

```powershell
git clone <repository-url>
cd NsisoLauncher
```

## 路径说明

解决方案文件位于 `src/NsisoLauncher.sln`。

- 在仓库根目录执行命令时，使用 `src/NsisoLauncher.sln`
- 在 `src` 目录执行命令时，使用 `NsisoLauncher.sln`

## 还原依赖

仓库根目录：

```powershell
dotnet restore src/NsisoLauncher.sln
```

`src` 目录：

```powershell
dotnet restore NsisoLauncher.sln
```

## 构建 Debug

仓库根目录：

```powershell
dotnet build src/NsisoLauncher.sln -c Debug
```

`src` 目录：

```powershell
dotnet build NsisoLauncher.sln -c Debug
```

## 构建 Release

仓库根目录：

```powershell
dotnet build src/NsisoLauncher.sln -c Release
```

`src` 目录：

```powershell
dotnet build NsisoLauncher.sln -c Release
```

## 输出路径

- Debug：`src/NsisoLauncher/bin/Debug/net10.0-windows/`
- Release：`src/NsisoLauncher/bin/Release/net10.0-windows/`

主程序入口为 `NsisoLauncher.exe`。

## 使用 Visual Studio

1. 打开 `src/NsisoLauncher.sln`。
2. 选择配置 `Debug` 或 `Release`。
3. 生成解决方案（Ctrl+Shift+B）。

## 测试

仓库根目录：

```powershell
dotnet test src/NsisoLauncher.sln -c Release
```

`src` 目录：

```powershell
dotnet test NsisoLauncher.sln -c Release
```

当前测试项目中的用例大多为注释状态，因此可能提示“没有可用测试”。

## 常见问题

- 构建时提示项目文件不存在：请确认当前目录与解决方案路径是否匹配，例如在 `src` 目录下应使用 `NsisoLauncher.sln`，不要写成 `src/NsisoLauncher.sln`。
- 构建时提示文件被占用：请先关闭正在运行的 `NsisoLauncher.exe`，然后重新构建。
- 运行时缺少 Java：启动器需要本机安装 Java，否则部分功能不可用，但程序仍可启动。
- 主题/界面异常：请确认已正确还原 NuGet 包，特别是 `MahApps.Metro` 与 `ControlzEx`。
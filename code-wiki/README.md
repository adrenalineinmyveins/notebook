# Jupyter Notebook Code Wiki

本 Wiki 是对 [jupyter/notebook](https://github.com/jupyter/notebook) 仓库（当前版本 7.7.0a2）源码的系统性分析文档，覆盖整体架构、模块职责、关键类与函数、依赖关系以及构建运行方式。所有结论均直接源自仓库源码，文中附有源文件相对路径，便于跳转对照阅读。

## 项目一句话简介

Jupyter Notebook 是一个基于 Web 的交互式计算笔记本环境；Notebook v7 的前端由 JupyterLab 组件构建、后端由 Jupyter Server 驱动，以"服务器扩展 + 多页前端应用"的形式发布为 `pip install notebook` 安装包。

## 文档地图

| 文档 | 内容 |
| --- | --- |
| [01-项目概览](01-项目概览.md) | 项目定位、版本策略、仓库目录结构、技术栈总览 |
| [02-整体架构](02-整体架构.md) | 分层架构图、多页应用（MPA）模型、请求生命周期、插件体系、联邦扩展机制 |
| [03-后端模块详解](03-后端模块详解.md) | `notebook/` Python 包：服务器扩展入口、路由处理器、page_config、打包分发 |
| [04-前端模块详解](04-前端模块详解.md) | `packages/` 下 12 个 TypeScript 包与 `app/` 组装层、`buildutils/` 构建脚本的职责 |
| [05-关键类与函数](05-关键类与函数.md) | `JupyterNotebookApp`、`NotebookApp`、`NotebookShell` 等核心类型的方法级说明 |
| [06-依赖关系](06-依赖关系.md) | Python 依赖、前端依赖分层图、包间依赖、与 Jupyter 生态的关系 |
| [07-构建与运行](07-构建与运行.md) | 用户安装运行、开发环境搭建、构建管线、watch 模式、发布流程 |
| [08-测试体系](08-测试体系.md) | pytest / jest / Playwright 三层测试与代码质量工具链 |

## 快速上手

以用户身份运行（详见 [07-构建与运行](07-构建与运行.md)）：

```bash
pip install notebook
jupyter notebook
```

以开发者身份构建（详见 [07-构建与运行](07-构建与运行.md#开发环境搭建)）：

```bash
pip install -e ".[dev,docs,test]"
jlpm install
jlpm build
jupyter notebook
```

## 阅读建议

- 想理解"这个项目是什么、由哪几块组成"：先读 [01-项目概览](01-项目概览.md)，再读 [02-整体架构](02-整体架构.md)。
- 想改后端行为（路由、页面配置、服务器扩展）：读 [03-后端模块详解](03-后端模块详解.md) 与 [05-关键类与函数](05-关键类与函数.md) 的后端部分。
- 想改前端界面（工具栏、菜单、Tree 页、Notebook 页）：读 [04-前端模块详解](04-前端模块详解.md) 与 [05-关键类与函数](05-关键类与函数.md) 的前端部分。
- 想跑起来、跑测试、发版本：读 [07-构建与运行](07-构建与运行.md) 与 [08-测试体系](08-测试体系.md)。

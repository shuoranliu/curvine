# GitHub Actions 工作流说明

本项目使用 GitHub Actions 自动化构建和测试流程，包含以下工作流：

## 1. 构建 Docker 镜像 (build-docker-image.yml)

此工作流用于构建 Rust 编译环境的 Docker 镜像。

### 特点

- 手动触发执行
- 可选择是否推送镜像到 GitHub Container Registry
- 使用 Docker 缓存加速构建

### 使用方法

1. 在 GitHub 仓库页面，点击 "Actions" 标签
2. 从左侧列表选择 "Build Docker Image" 工作流
3. 点击 "Run workflow" 按钮
4. 选择是否推送镜像到 GitHub Container Registry
5. 点击 "Run workflow" 开始构建

## 2. Rust 构建与测试 (build.yml)

此工作流用于构建和测试 Rust 项目。

### 特点

- 自动触发：在所有分支的推送和拉取请求上执行
- 使用自定义 Docker 镜像作为构建环境
- 使用 Rust 缓存加速构建
- 执行代码格式检查和 Clippy 静态分析

### 前提条件

在使用此工作流之前，需要先运行 "Build Docker Image" 工作流并推送镜像到 GitHub Container Registry。

## 注意事项

1. 首次使用时，需要确保 GitHub 仓库有权限访问 GitHub Container Registry
2. 如果修改了 Docker 镜像的配置，需要重新构建并推送镜像
3. Clippy 检查级别设置为 "deny"，可以在工作流文件中修改
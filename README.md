# Docker 云存储备份

Docker 镜像备份工具，支持多种云存储服务，使用 GitHub Actions 实现自动化备份流程。

## 🚀 功能特点

- 支持多种云存储服务：
  - 阿里云 OSS
  - 腾讯云 COS
  - 华为云 OBS
  - MinIO
  - Cloudflare R2
  - AWS S3
  - Azure Blob Storage
  - Google Cloud Storage
- 基于 GitHub Actions，使用简单
- 无需配置文件
- 灵活的镜像列表输入
- 自动清理备份后的临时文件

## 📋 使用前提

- GitHub 账号
- 至少一个支持的云存储服务的访问权限
- 需要备份的 Docker 镜像

## 🔑 配置说明

### 存储服务凭证

根据选择的存储服务，在 GitHub 仓库中配置以下密钥（Settings -> Secrets and variables -> Actions）：

#### 阿里云 OSS
ALIYUN_ACCESS_KEY<br>
ALIYUN_SECRET_KEY<br>
OSS_ENDPOINT<br>
OSS_BUCKET<br>

#### 腾讯云 COS
TENCENT_SECRET_ID<br>
TENCENT_SECRET_KEY<br>
COS_BUCKET<br>
COS_REGION<br>

#### 华为云 OBS
HUAWEI_ACCESS_KEY<br>
HUAWEI_SECRET_KEY<br>
OBS_ENDPOINT<br>
OBS_BUCKET<br>

#### MinIO
MINIO_ENDPOINT<br>
MINIO_ACCESS_KEY<br>
MINIO_SECRET_KEY<br>
MINIO_BUCKET<br>

#### Cloudflare R2
CF_ACCESS_KEY_ID<br>
CF_SECRET_KEY<br>
CF_ENDPOINT<br>
CF_BUCKET<br>

#### AWS S3
AWS_ACCESS_KEY<br>
AWS_SECRET_KEY<br>
AWS_REGION<br>
AWS_BUCKET<br>

#### Azure Blob Storage
AZURE_STORAGE_ACCOUNT<br>
AZURE_RESOURCE_GROUP<br>
AZURE_CONTAINER<br>

#### Google Cloud Storage
GCP_SERVICE_ACCOUNT_KEY<br>
GCP_BUCKET<br>


## 📝 使用方法

1. Fork 此仓库
2. 配置所选存储服务所需的密钥
3. 进入 Actions 页面
4. 选择 "Docker Image Backup" 工作流
5. 点击 "Run workflow"
6. 选择存储服务类型
7. 输入要备份的 Docker 镜像列表（每行一个），例如：
nginx:latest
mysql:8.0
redis:7.2
8. 点击 "Run workflow" 开始备份过程

## 📁 备份结构

备份文件按以下结构存储：
docker_images/
└── 镜像名称_标签_时间戳.tar


## 🔍 使用示例

将多个 Docker 镜像备份到阿里云 OSS：

1. 配置阿里云 OSS 密钥
2. 运行工作流并输入以下镜像列表：
debian:latest
ubuntu:22.04
python:3.9-slim
nginx:1.24
3. 工作流将：
   - 拉取每个镜像
   - 将其保存为 tar 文件
   - 上传到你的 OSS 存储桶
   - 清理临时文件

## ⚠️ 注意事项

- 确保云服务有足够的存储空间
- 注意带宽限制和成本
- 大型镜像可能需要更长的处理时间
- 检查 GitHub Actions 的使用限制

## 🤝 贡献

欢迎提交 Pull Request 来改进这个项目！

## 📄 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件

## 🙏 致谢

- GitHub Actions 提供自动化平台
- 所有支持的云存储服务
- Docker 容器技术

## 📞 支持

如果遇到问题或有疑问：
1. 在本仓库中创建 issue
2. 提供问题的详细信息
3. 包含相关日志和配置


# 区域、可用区与实例规格参考

## 区域列表

### 中国大陆

| 区域ID | 区域名称 | 说明 |
|--------|---------|------|
| cn-north-1 | 华北-北京一 | 早期区域，部分服务不可用 |
| cn-north-4 | 华北-北京四 | **推荐**，服务最全 |
| cn-east-2 | 华东-上海二 | 推荐华东用户 |
| cn-east-3 | 华东-上海一 | |
| cn-south-1 | 华南-广州 | 推荐华南用户 |
| cn-south-2 | 华南-深圳 | |
| cn-southwest-2 | 西南-贵阳一 | |
| cn-northeast-1 | 东北-大连 | |
| cn-north-9 | 华北-乌兰察布一 | |

### 亚太

| 区域ID | 区域名称 |
|--------|---------|
| ap-southeast-1 | 中国-香港 |
| ap-southeast-2 | 亚太-曼谷 |
| ap-southeast-3 | 亚太-新加坡 |
| ap-southeast-4 | 亚太-雅加达 |

### 非洲与拉美

| 区域ID | 区域名称 |
|--------|---------|
| af-south-1 | 非洲-约翰内斯堡 |
| la-north-2 | 拉美-墨西哥城二 |
| la-south-2 | 拉美-圣地亚哥 |
| sa-brazil-1 | 拉美-圣保罗一 |

### 欧洲

| 区域ID | 区域名称 |
|--------|---------|
| eu-west-1 | 欧洲-巴黎 |
| eu-west-101 | 欧洲-阿姆斯特丹 |

---

## 可用区

每个区域包含1-3个可用区（AZ），用字母后缀标识：

| 区域 | 可用区 |
|------|--------|
| cn-north-4 | cn-north-4a, cn-north-4b, cn-north-4c |
| cn-east-2 | cn-east-2a, cn-east-2b, cn-east-2c |
| cn-south-1 | cn-south-1a, cn-south-1b, cn-south-1c |
| ap-southeast-1 | ap-southeast-1a, ap-southeast-1b, ap-southeast-1c |
| ap-southeast-3 | ap-southeast-3a, ap-southeast-3b, ap-southeast-3c |

查看某个区域可用规格：
```bash
hcloud ECS ListFlavors --cli-region=cn-north-4 --availability_zone=cn-north-4a
```

---

## 实例规格参考

### 通用计算型（ac8系列）- 推荐

| 规格 | vCPU | 内存(GB) | 网络带宽(Gbps) | 适用场景 |
|------|------|----------|---------------|---------|
| ac8.large.2 | 2 | 4 | 1.5 | Web/开发测试 |
| ac8.large.4 | 2 | 8 | 1.5 | 轻量型应用 |
| ac8.xlarge.2 | 4 | 8 | 3 | 中型应用 |
| ac8.xlarge.4 | 4 | 16 | 3 | 数据库/缓存 |
| ac8.2xlarge.2 | 8 | 16 | 6 | 大型应用 |
| ac8.2xlarge.4 | 8 | 32 | 6 | 内存密集型 |
| ac8.4xlarge.2 | 16 | 32 | 10 | 计算密集型 |
| ac8.4xlarge.4 | 16 | 64 | 10 | 大内存 |
| ac8.8xlarge.2 | 32 | 64 | 15 | 高性能计算 |
| ac8.8xlarge.4 | 32 | 128 | 15 | 超大内存 |

### 通用计算型（as8系列）

| 规格 | vCPU | 内存(GB) | 适用场景 |
|------|------|----------|---------|
| as8.large.2 | 2 | 4 | 通用计算 |
| as8.xlarge.2 | 4 | 8 | 中型计算 |
| as8.2xlarge.2 | 8 | 16 | 大型计算 |

### 专属计算型（d8系列）

| 规格 | vCPU | 内存(GB) | 适用场景 |
|------|------|----------|---------|
| d8.large.2 | 2 | 4 | 专属主机 |
| d8.xlarge.2 | 4 | 8 | 专属主机 |

### 内存优化型（m8系列）

| 规格 | vCPU | 内存(GB) | 适用场景 |
|------|------|----------|---------|
| m8.large.4 | 2 | 8 | 内存密集 |
| m8.xlarge.4 | 4 | 16 | 数据库 |
| m8.2xlarge.4 | 8 | 32 | 缓存/数据库 |

### GPU加速型

| 规格 | vCPU | 内存(GB) | GPU | 适用场景 |
|------|------|----------|-----|---------|
| pi2.2xlarge.4 | 8 | 32 | 1×T4 | AI推理 |
| pi2.4xlarge.4 | 16 | 64 | 1×T4 | AI推理 |
| pi2.8xlarge.4 | 32 | 128 | 2×T4 | AI推理 |
| pw3.2xlarge.4 | 8 | 32 | 1×V100 | AI训练 |
| pw3.4xlarge.4 | 16 | 64 | 1×V100 | AI训练 |

### ⚠️ 已废弃规格

以下规格已废弃，**不可用于新建实例**：

| 废弃系列 | 替代系列 |
|---------|---------|
| ac7 (ac7.large.2, ac7.xlarge.2...) | ac8 |
| as7 (as7.large.2, as7.xlarge.2...) | as8 |
| s6 (s6.large.2, s6.xlarge.2...) | as8 |
| c6 (c6.large.2, c6.xlarge.2...) | ac8 |
| m6 (m6.large.4, m6.xlarge.4...) | m8 |

---

## 镜像参考

### 公共镜像（常用）

| 镜像 | OS | 说明 |
|------|-----|------|
| Ubuntu 22.04 server 64bit | Ubuntu 22.04 LTS | **推荐**，默认允许root SSH |
| Ubuntu 20.04 server 64bit | Ubuntu 20.04 LTS | 稳定版 |
| CentOS 7.9 64bit | CentOS 7.9 | 传统选择 |
| EulerOS 2.9 64bit | EulerOS 2.9 | 华为自研 |
| Debian 11.0 64bit | Debian 11 | 轻量级 |
| Windows Server 2022 | Windows 2022 | Windows应用 |

### 查看可用镜像

```bash
hcloud IMS ListImages --cli-region=cn-north-4 --limit=20
```

---

## 云硬盘类型参考

| 类型 | 代码 | 最大容量 | 最大IOPS | 最大吞吐 | 适用场景 |
|------|------|---------|---------|---------|---------|
| 高IO | SAS | 32768GB | 5,000 | 150MB/s | 通用 |
| 通用型SSD | SSD | 32768GB | 5,000 | 150MB/s | 通用 |
| 超高IO | SSD2 | 32768GB | 20,000 | 350MB/s | 数据库 |
| 通用型SSD V2 | GPSSD2 | 32768GB | 128,000 | 1000MB/s | 高性能 |
| 极速型SSD | ESSD2 | 32768GB | 256,000 | 1000MB/s | 极致性能 |

---

## 网络带宽参考

| 带宽(Mbps) | 适用场景 |
|-----------|---------|
| 1-5 | 开发测试 |
| 10-20 | 中小型Web |
| 50-100 | 中型应用 |
| 100-500 | 大型应用 |
| 500+ | 高流量应用 |

计费模式:
- **按带宽计费** (bandwidth): 适合稳定流量
- **按流量计费** (traffic): 适合突发流量

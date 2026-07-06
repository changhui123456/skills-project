# 华为云Skills完整目录

## 概述

华为云Agent Skills体系托管在GitCode `developer-skill/developer-skill` 仓库，安装在 `~/.hermes/skills/devops/` 目录。

---

## Skills清单

### 1. huawei-cloud-ecs-diagnose

| 属性 | 值 |
|------|-----|
| **名称** | huawei-cloud-ecs-diagnose |
| **版本** | v1.0.0 (刷新) |
| **分类** | 计算 > ECS |
| **说明** | 综合诊断ECS故障，涵盖云平台侧检查和GuestOS内部诊断 |
| **适用场景** | SSH不通、实例卡顿、磁碟满、CPU/内存告警 |
| **依赖** | KooCLI, sshpass |
| **文件数** | 7 (88KB) |
| **关键词** | ECS, 诊断, 故障, SSH, 磁盘, CPU, 内存 |

**核心命令**:
- `hcloud ECS ListServersDetails` — 列出实例
- `hcloud ECS ShowServer` — 查看实例详情
- `hcloud VPC ListSecurityGroups/v3` — 查看安全组
- `sshpass -p '密码' ssh root@IP` — SSH连接

---

### 2. huawei-cloud-ecs-diagnosis-workflow

| 属性 | 值 |
|------|-----|
| **名称** | huawei-cloud-ecs-diagnosis-workflow |
| **版本** | v2.0.0 |
| **分类** | 计算 > ECS, 运维 > 诊断 |
| **说明** | 分层诊断工作流，系统性ECS故障排查 |
| **适用场景** | 系统性ECS故障排查，从平台→网络→系统→应用逐层诊断 |
| **依赖** | KooCLI, sshpass |
| **文件数** | 7 (54KB) |
| **关键词** | ECS, 分层诊断, 工作流, 安全组, 网络连通, 系统检查 |

**4层诊断模型**:
1. **L1 平台层**: 实例状态/规格/计费
2. **L2 网络层**: 安全组/EIP/VPC/端口连通
3. **L3 系统层**: CPU/内存/磁盘/进程/内核
4. **L4 应用层**: 服务/端口/日志

---

### 3. huawei-cloud-cli-guidance

| 属性 | 值 |
|------|-----|
| **名称** | huawei-cloud-cli-guidance |
| **版本** | v1.0.0 |
| **分类** | 开发工具 > CLI |
| **说明** | KooCLI通用指导，覆盖100+华为云服务 |
| **适用场景** | CLI命令格式、参数规则、错误调试、服务发现 |
| **依赖** | KooCLI |
| **文件数** | 6 (48KB) |
| **关键词** | CLI, 命令, 参数, 调试, 服务, KooCLI |

**覆盖服务**: ECS, VPC, EIP, IMS, EVS, CES, RDS, CCE, ELB, DCS, SMN, IAM, DNS, AOM, OBS 等100+

---

### 4. huawei-cloud-obs-manage

| 属性 | 值 |
|------|-----|
| **名称** | huawei-cloud-obs-manage |
| **版本** | v1.0.0 |
| **分类** | 存储 > OBS |
| **说明** | OBS对象存储管理，基于KooCLI内置obsutil v5.5.9 |
| **适用场景** | 桶管理、上传下载、增量同步、定时备份、归档恢复 |
| **依赖** | KooCLI (内置obsutil) |
| **文件数** | 4 (28KB) |
| **关键词** | OBS, 对象存储, 桶, 上传, 下载, 同步, 备份, 归档 |

**核心命令**:
- `hcloud OBS ls/mb/rm/cp/sync/stat/sign/restore` — obsutil全套命令
- `hcloud OBS lifecycle/bucketpolicy` — 生命周期与桶策略

---

### 5. huawei-cloud-find-skills (本技能)

| 属性 | 值 |
|------|-----|
| **名称** | huawei-cloud-find-skills |
| **版本** | v1.0.0 |
| **分类** | 开发工具 > Skills |
| **说明** | 搜索、发现和浏览华为云Agent Skills |
| **适用场景** | 查找Skills、浏览分类、查看详情、安装指导 |
| **依赖** | KooCLI, GitCode API |
| **文件数** | 4 |
| **关键词** | 搜索, 发现, 浏览, 安装, Skills |

---

## Skills统计

| 统计项 | 数值 |
|--------|------|
| Skills总数 | 5 |
| 总文件数 | 28 |
| 总大小 | ~218KB |
| 覆盖服务 | 100+ (通过cli-guidance) |
| 覆盖分类 | 计算、存储、开发工具、运维 |

## 分类体系

```
华为云Skills
├── 计算
│   └── ECS
│       ├── huawei-cloud-ecs-diagnose (诊断)
│       └── huawei-cloud-ecs-diagnosis-workflow (分层诊断工作流)
├── 存储
│   └── OBS
│       └── huawei-cloud-obs-manage (对象存储管理)
├── 开发工具
│   ├── CLI
│   │   └── huawei-cloud-cli-guidance (通用CLI指导)
│   └── Skills
│       └── huawei-cloud-find-skills (技能搜索发现)
└── 运维
    └── 诊断
        └── huawei-cloud-ecs-diagnosis-workflow (分层诊断)
```

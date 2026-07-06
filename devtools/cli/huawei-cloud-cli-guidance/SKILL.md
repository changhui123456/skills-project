---
name: huawei-cloud-cli-guidance
description: |
  华为云KooCLI (hcloud) 通用指导技能。覆盖100+云服务的命令格式、参数规则、
  常见操作工作流、错误排查。适用于任何需要通过CLI管理华为云资源的场景。
  基于KooCLI v7.2.2+验证。
tags: [huawei-cloud, cli, koocli, hcloud, cloud-management, devops, guidance]
version: 1.0.0
---

# 华为云 KooCLI 通用指导技能

## 概述

本技能是华为云KooCLI（hcloud）的**通用命令行指导手册**，覆盖华为云100+服务的CLI操作规范、参数格式、常见工作流和错误排查。

**与诊断技能的区别**:
- `huawei-cloud-ecs-diagnosis-workflow` → 专注ECS实例故障诊断
- `huawei-cloud-cli-guidance`（本技能）→ **通用CLI操作指导**，覆盖所有服务

## KooCLI 命令格式标准

### 核心格式

```bash
hcloud <SERVICE> <Operation> --param1=value1 --param2=value2 --cli-region=<region>
```

### 格式规则

| 元素 | 格式 | 正确示例 | 错误示例 |
|------|------|---------|---------|
| 服务名 | **大写** | `ECS`, `VPC`, `CES` | `ecs`, `vpc` |
| 操作名 | **PascalCase** | `ListServersDetails` | `listServersDetails` |
| 区域参数 | `--cli-region=<值>` | `--cli-region=cn-north-4` | `--region=cn-north-4` |
| 普通参数 | `--key=value` | `--limit=10` | `--limit 10` |
| 数组参数 | `--key.1=val1 --key.2=val2` | `--servers.1.id=xxx` | `--servers=[xxx]` |
| 嵌套对象 | `--key.sub_key=value` | `--remote_console.protocol=vnc` | `--remote_console={protocol:vnc}` |
| 布尔参数 | `--key=true/false` | `--delete_publicip=true` | `--delete_publicip` |
| v3操作 | 操作名带`/v3`后缀 | `ListSecurityGroups/v3` | `ListSecurityGroups` |

### ⚠️ 已知陷阱

| 陷阱 | 说明 | 正确做法 |
|------|------|---------|
| `hcloud --version` | 不工作，无输出 | 使用 `hcloud --help` |
| VPC v3操作 | 部分VPC操作需`/v3`后缀 | `ListSecurityGroups/v3`, `ShowSecurityGroup/v3` |
| EIP独立服务 | 弹性公网IP不在VPC下 | 使用 `hcloud EIP ...` 而非 `hcloud VPC ...` |
| 批量操作格式 | 数组参数从1开始 | `--os-start.servers.1.id=<id>` |
| 安全组规则 | 使用嵌套对象格式 | `--security_group_rule.direction=ingress` |
| 实例规格废弃 | as7/ac7系列已废弃 | 使用 `ac8.large.2`, `as8.large.2` |
| 创建实例 | 需`--server.`前缀 | `--server.name=xxx --server.flavorRef=xxx` |

## 服务分类

### 计算
| 服务 | 代码 | 常用操作 |
|------|------|---------|
| 弹性云服务器 | `ECS` | 创建/查询/启停/删除实例 |
| 裸金属服务器 | `BMS` | 裸金属实例管理 |
| 弹性伸缩 | `AS` | 伸缩组/配置/策略 |
| 容器引擎 | `CCE` | 集群/节点/工作负载 |

### 网络
| 服务 | 代码 | 常用操作 |
|------|------|---------|
| 虚拟私有云 | `VPC` | VPC/子网/安全组/路由 |
| 弹性公网IP | `EIP` | 申请/绑定/解绑/释放 |
| 弹性负载均衡 | `ELB` | 负载均衡器/监听器/后端 |
| NAT网关 | `NAT` | NAT网关/SNAT/DNAT规则 |
| DNS | `DNS` | 域名/解析记录 |
| VPN | `VPN` | VPN网关/连接 |
| 企业路由器 | `ER` | 路由表/关联/传播 |

### 存储
| 服务 | 代码 | 常用操作 |
|------|------|---------|
| 云硬盘 | `EVS` | 创建/挂载/扩容/快照 |
| 对象存储 | `OBS`* | 桶/对象管理 |
| 文件系统 | `SFSTurbo` | 创建/挂载文件系统 |
| 云备份 | `CBR` | 备份/恢复/策略 |

*OBS推荐使用obsutil而非KooCLI

### 数据库
| 服务 | 代码 | 常用操作 |
|------|------|---------|
| 关系型数据库 | `RDS` | 实例/备份/参数 |
| GaussDB | `GaussDB` | 分布式数据库 |
| GaussDB NoSQL | `GaussDBforNoSQL` | Mongo/Cassandra/Redis |
| 分布式缓存 | `DCS` | Redis实例管理 |
| 数据复制 | `DRS` | 迁移/同步任务 |

### 安全
| 服务 | 代码 | 常用操作 |
|------|------|---------|
| 身份与访问管理 | `IAM` | 用户/组/策略/角色 |
| 主机安全 | `HSS` | 入侵检测/漏洞扫描 |
| Web应用防火墙 | `WAF` | 防护策略/规则 |
| 密钥管理 | `KMS` | 密钥创建/加密/解密 |
| 抗DDoS | `Anti-DDoS` | 防护配置 |

### 监控与运维
| 服务 | 代码 | 常用操作 |
|------|------|---------|
| 云监控 | `CES` | 指标/告警/事件 |
| 日志服务 | `LTS` | 日志组/流/查询 |
| 应用运维管理 | `AOM` | 组件/环境/阈值 |
| 配置审计 | `Config` | 合规规则/资源记录 |

### 开发与中间件
| 服务 | 代码 | 常用操作 |
|------|------|---------|
| 函数工作流 | `FunctionGraph` | 函数创建/触发器 |
| 消息通知 | `SMN` | 主题/订阅 |
| API网关 | `APIG` | API/分组/环境 |
| 分布式消息 | `Kafka`/`RabbitMQ`/`RocketMQ` | 实例/Topic |
| 微服务引擎 | `CSE` | 注册中心/配置中心 |

### 大数据与AI
| 服务 | 代码 | 常用操作 |
|------|------|---------|
| ModelArts | `ModelArts` | 训练/推理/开发环境 |
| 数据湖探索 | `DLI` | SQL作业/队列 |
| 数据仓库 | `DWS` | 集群/数据库/表 |
| MapReduce | `MRS` | 集群/作业 |

## 场景路由

根据用户意图路由到对应服务和工作流：

| 用户意图 | 关键词 | 路由 |
|---------|--------|------|
| 管理云服务器 | "ECS", "实例", "虚拟机", "创建服务器" | → ECS操作 |
| 管理网络 | "VPC", "子网", "安全组", "防火墙规则" | → VPC/EIP操作 |
| 管理数据库 | "RDS", "MySQL", "Redis", "数据库" | → RDS/DCS操作 |
| 管理存储 | "EVS", "云盘", "磁盘", "快照" | → EVS操作 |
| 查看监控 | "监控", "指标", "告警", "CPU", "内存" | → CES操作 |
| 管理权限 | "IAM", "用户", "权限", "策略", "角色" | → IAM操作 |
| 管理容器 | "CCE", "集群", "容器", "K8s" | → CCE操作 |
| 管理负载均衡 | "ELB", "负载均衡", "监听器" | → ELB操作 |
| 管理DNS | "DNS", "域名", "解析" | → DNS操作 |
| 管理函数 | "FunctionGraph", "函数计算", "Serverless" | → FunctionGraph操作 |
| 查看账单 | "账单", "费用", "消费", "BSS" | → 浏览器（KooCLI不支持BSS） |

## 快速命令参考

### ECS（弹性云服务器）

```bash
# 查询
hcloud ECS ListServersDetails --cli-region=<region>
hcloud ECS ShowServer --server_id=<id> --cli-region=<region>
hcloud ECS NovaShowServer --server_id=<id> --cli-region=<region>

# 生命周期
hcloud ECS NovaStartServers --os-start.servers.1.id=<id> --cli-region=<region>
hcloud ECS NovaStopServers --os-stop.servers.1.id=<id> --cli-region=<region>
hcloud ECS NovaRebootServers --os-reboot.servers.1.id=<id> --cli-region=<region>
hcloud ECS DeleteServers --servers.1.id=<id> --delete_publicip=true --delete_volume=true --cli-region=<region>

# 创建
hcloud ECS CreateServers --server.name=<name> --server.imageRef=<img> --server.flavorRef=ac8.large.2 --server.vpcid=<vpc> --server.subnet_id=<subnet> --server.security_groups.1.id=<sg> --server.adminPass=<pwd> --server.publicip.eip.bandwidth.sharetype=PER --server.publicip.eip.bandwidth.size=5 --cli-region=<region>

# VNC控制台
hcloud ECS ShowServerRemoteConsole --server_id=<id> --remote_console.protocol=vnc --remote_console.type=novnc --cli-region=<region>
```

### VPC（虚拟私有云）

```bash
# 安全组
hcloud VPC ListSecurityGroups/v3 --cli-region=<region>
hcloud VPC ShowSecurityGroup/v3 --security_group_id=<id> --cli-region=<region>
hcloud VPC CreateSecurityGroupRule/v3 --security_group_id=<id> --security_group_rule.direction=ingress --security_group_rule.protocol=tcp --security_group_rule.port_range_min=22 --security_group_rule.port_range_max=22 --security_group_rule.remote_ip_prefix=0.0.0.0/0 --cli-region=<region>
hcloud VPC DeleteSecurityGroupRule/v3 --security_group_rule_id=<rule-id> --cli-region=<region>
```

### EIP（弹性公网IP）

```bash
hcloud EIP ListPublicips/v3 --cli-region=<region>
hcloud EIP CreatePublicip/v3 --publicip.type=EIP --bandwidth.name=bw1 --bandwidth.size=5 --bandwidth.share_type=PER --bandwidth.charge_mode=bandwidth --cli-region=<region>
hcloud EIP AssociatePublicip/v3 --publicip_id=<eip-id> --publicip_associate.instance_id=<ecs-id> --publicip_associate.instance_type=ECS --cli-region=<region>
hcloud EIP DeletePublicip/v3 --publicip_id=<eip-id> --cli-region=<region>
```

### CES（云监控）

```bash
hcloud CES ListMetrics --namespace=SYS.ECS --cli-region=<region>
hcloud CES ShowMetricData --namespace=SYS.ECS --metric_name=cpu_util --dim.0=instance_id,<id> --from=<ts>000 --to=<ts>000 --period=300 --filter=average --cli-region=<region>
hcloud CES ListAlarms --cli-region=<region>
```

### EVS（云硬盘）

```bash
hcloud EVS ListVolumes --cli-region=<region>
hcloud EVS ShowVolume --volume_id=<id> --cli-region=<region>
hcloud EVS CreateVolume --volume.name=<name> --volume.size=100 --volume.volume_type=SSD --volume.availability_zone=<az> --cli-region=<region>
```

### RDS（关系型数据库）

```bash
hcloud RDS ListInstances --cli-region=<region>
hcloud RDS ShowInstance --instance_id=<id> --cli-region=<region>
```

### IAM（身份与访问管理）

```bash
hcloud IAM KeystoneListUsers --cli-region=<region>
hcloud IAM KeystoneShowUser --user_id=<id> --cli-region=<region>
hcloud IAM ListPolicies --cli-region=<region>
```

### ELB（弹性负载均衡）

```bash
hcloud ELB ListLoadBalancers --cli-region=<region>
hcloud ELB ShowLoadBalancer --loadbalancer_id=<id> --cli-region=<region>
```

### CCE（云容器引擎）

```bash
hcloud CCE ListClusters --cli-region=<region>
hcloud CCE ShowCluster --cluster_id=<id> --cli-region=<region>
```

## 认证与安全

### 配置认证

```bash
# 交互式配置
hcloud configure set

# 查看配置
hcloud configure list

# 多Profile配置
hcloud configure set --cli-profile=prod
```

### 🔒 安全红线

| 规则 | 说明 |
|------|------|
| 🚫 不暴露AK/SK | 绝不在对话/命令/日志中输出AccessKey值 |
| 🚫 不明文存储凭据 | 使用环境变量或密钥管理服务 |
| 🚫 不使用主账号AK/SK | 创建IAM用户并授予最小权限 |
| ✅ 启用MFA | 敏感操作需多因素认证 |
| ✅ 定期轮换AK/SK | 至少每90天更换一次 |
| ✅ 审计操作日志 | 通过CTS追踪所有API调用 |

## 参考文档

| 文档 | 说明 |
|------|------|
| [全服务目录](references/service-catalog.md) | 100+服务分类目录与命令速查 |
| [参数格式规则](references/parameter-format.md) | 参数格式规则与示例 |
| [常见操作工作流](references/common-workflows.md) | 创建实例/VPC/安全组等完整工作流 |
| [CLI错误排查](references/cli-troubleshooting.md) | CLI错误排查与FAQ |
| [区域与规格参考](references/region-and-spec.md) | 区域/可用区/实例规格参考 |

## 注意事项

- 本技能覆盖**通用CLI操作指导**，不包含特定诊断流程（使用 `huawei-cloud-ecs-diagnosis-workflow`）
- BSS账单服务**KooCLI不支持**，需通过浏览器访问控制台
- OBS对象存储**推荐使用obsutil**而非KooCLI
- 所有命令均基于KooCLI v7.2.2+验证
- 中文优先，命令和参数名保持英文

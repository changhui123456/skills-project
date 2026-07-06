# KooCLI 参数格式规则与示例

## 概述

KooCLI参数格式有严格规则，格式错误是最常见的CLI使用问题。本文档详细说明各类参数格式。

---

## 参数类型总览

| 类型 | 格式 | 示例 |
|------|------|------|
| 标量参数 | `--key=value` | `--limit=10`, `--name=my-instance` |
| 布尔参数 | `--key=true/false` | `--delete_publicip=true` |
| 数组参数 | `--key.1=val1 --key.2=val2` | `--servers.1.id=abc --servers.2.id=def` |
| 嵌套对象 | `--key.sub_key=value` | `--remote_console.protocol=vnc` |
| 数组对象 | `--key.1.sub_key=value` | `--security_group_id.1=sg-xxx` |
| 枚举参数 | `--key=<枚举值>` | `--filter=average` |

---

## 1. 标量参数

最基础的参数类型，直接 `--key=value` 格式。

```bash
# 字符串
--server_id=3d1537a9-9090-4045-8a83-cc6f2c5bc4ac
--name=my-instance
--description="My ECS instance"

# 数字
--limit=10
--offset=0
--bandwidth.size=5

# 布尔
--delete_publicip=true
--delete_volume=false
```

⚠️ **注意**: 值中包含空格或特殊字符时，用引号包裹：
```bash
# 正确
--description="Allow SSH from office"

# 错误（shell会拆分空格）
--description=Allow SSH from office
```

---

## 2. 数组参数

数组参数使用 **从1开始的索引**（不是0！）。

### 基本数组

```bash
# 安全组ID数组（VPC规则查询）
--security_group_id.1=sg-abc123
--security_group_id.1=sg-abc123 --security_group_id.2=sg-def456

# 实例ID数组（批量操作）
--servers.1.id=i-001 --servers.2.id=i-002 --servers.3.id=i-003

# 批量启动
hcloud ECS NovaStartServers \
  --os-start.servers.1.id=i-001 \
  --os-start.servers.2.id=i-002 \
  --cli-region=cn-north-4

# 批量停止
hcloud ECS NovaStopServers \
  --os-stop.servers.1.id=i-001 \
  --os-stop.servers.2.id=i-002 \
  --cli-region=cn-north-4

# 批量重启
hcloud ECS NovaRebootServers \
  --os-reboot.servers.1.id=i-001 \
  --os-reboot.servers.2.id=i-002 \
  --cli-region=cn-north-4
```

### 批量删除

```bash
hcloud ECS DeleteServers \
  --servers.1.id=i-001 \
  --servers.2.id=i-002 \
  --delete_publicip=true \
  --delete_volume=true \
  --cli-region=cn-north-4
```

### 维度数组（CES监控）

```bash
# 单维度
--dim.0=instance_id,i-001

# 双维度（磁盘指标需要instance_id + name）
--dim.0=instance_id,i-001 --dim.1=name,/dev/vda1
```

---

## 3. 嵌套对象参数

嵌套对象使用 **点号分隔** 的层级路径。

### VNC远程控制台

```bash
hcloud ECS ShowServerRemoteConsole \
  --server_id=i-001 \
  --remote_console.protocol=vnc \
  --remote_console.type=novnc \
  --cli-region=cn-north-4
```

### 安全组规则创建

```bash
hcloud VPC CreateSecurityGroupRule/v3 \
  --security_group_id=sg-001 \
  --security_group_rule.direction=ingress \
  --security_group_rule.protocol=tcp \
  --security_group_rule.port_range_min=22 \
  --security_group_rule.port_range_max=22 \
  --security_group_rule.remote_ip_prefix=0.0.0.0/0 \
  --security_group_rule.description="Allow SSH" \
  --cli-region=cn-north-4
```

### 创建实例（server嵌套对象）

```bash
hcloud ECS CreateServers \
  --server.name=my-instance \
  --server.imageRef=img-001 \
  --server.flavorRef=ac8.large.2 \
  --server.vpcid=vpc-001 \
  --server.subnet_id=subnet-001 \
  --server.adminPass=MyP@ssw0rd \
  --server.security_groups.1.id=sg-001 \
  --server.publicip.eip.bandwidth.sharetype=PER \
  --server.publicip.eip.bandwidth.size=5 \
  --server.publicip.eip.bandwidth.charge_mode=bandwidth \
  --cli-region=cn-north-4
```

### EIP绑定

```bash
hcloud EIP AssociatePublicip/v3 \
  --publicip_id=eip-001 \
  --publicip_associate.instance_id=i-001 \
  --publicip_associate.instance_type=ECS \
  --cli-region=cn-north-4
```

---

## 4. V3操作后缀

部分VPC服务操作需要 `/v3` 后缀，这是API版本区分。

### 需要/v3后缀的操作

| 操作 | 完整格式 |
|------|---------|
| ListSecurityGroups | `ListSecurityGroups/v3` |
| ShowSecurityGroup | `ShowSecurityGroup/v3` |
| CreateSecurityGroup | `CreateSecurityGroup/v3` |
| DeleteSecurityGroup | `DeleteSecurityGroup/v3` |
| ListSecurityGroupRules | `ListSecurityGroupRules/v3` |
| CreateSecurityGroupRule | `CreateSecurityGroupRule/v3` |
| DeleteSecurityGroupRule | `DeleteSecurityGroupRule/v3` |

### 不需要/v3后缀的操作

| 操作 | 格式 |
|------|------|
| ListVpcs | `ListVpcs` |
| ShowVpc | `ShowVpc` |
| ListSubnets | `ListSubnets` |
| ShowSubnet | `ShowSubnet` |

### EIP服务也需要/v3

| 操作 | 完整格式 |
|------|---------|
| ListPublicips | `ListPublicips/v3` |
| CreatePublicip | `CreatePublicip/v3` |
| DeletePublicip | `DeletePublicip/v3` |
| AssociatePublicip | `AssociatePublicip/v3` |
| DisassociatePublicip | `DisassociatePublicip/v3` |

---

## 5. 枚举值参考

### 实例状态
| 值 | 说明 |
|----|------|
| ACTIVE | 运行中 |
| SHUTOFF | 已关机 |
| ERROR | 错误 |
| BUILD | 创建中 |
| REBUILD | 重建中 |
| HARD_REBOOT | 强制重启中 |
| REBOOT | 重启中 |
| MIGRATING | 迁移中 |
| RESIZE | 规格变更中 |
| VERIFY_RESIZE | 等待确认规格变更 |
| LOCKED | 锁定 |
| PAUSED | 暂停 |
| SUSPENDED | 挂起 |
| SHELVED | 搁置 |
| SHELVED_OFFLOADED | 搁置卸载 |

### EIP状态
| 值 | 说明 |
|----|------|
| FREE | 未绑定 |
| ACTIVE | 已绑定 |
| DOWN | 未激活 |
| ERROR | 错误 |

### 安全组规则方向
| 值 | 说明 |
|----|------|
| ingress | 入方向 |
| egress | 出方向 |

### 安全组规则协议
| 值 | 说明 |
|----|------|
| tcp | TCP协议 |
| udp | UDP协议 |
| icmp | ICMP协议 |

### CES指标filter
| 值 | 说明 |
|----|------|
| average | 平均值 |
| max | 最大值 |
| min | 最小值 |
| variance | 方差 |
| sum | 求和 |

### CES指标period
| 值 | 说明 |
|----|------|
| 1 | 实时 |
| 60 | 1分钟 |
| 300 | 5分钟 |
| 1200 | 20分钟 |
| 3600 | 1小时 |
| 14400 | 4小时 |
| 86400 | 1天 |

### 带宽共享类型
| 值 | 说明 |
|----|------|
| PER | 独享带宽 |
| WHOLE | 共享带宽 |

### 带宽计费模式
| 值 | 说明 |
|----|------|
| bandwidth | 按带宽计费 |
| traffic | 按流量计费 |

---

## 6. 常见格式错误

| 错误写法 | 正确写法 | 说明 |
|---------|---------|------|
| `hcloud ecs ListServers` | `hcloud ECS ListServersDetails` | 服务名大写 |
| `--region=cn-north-4` | `--cli-region=cn-north-4` | 区域参数名 |
| `--limit 10` | `--limit=10` | 等号连接 |
| `--servers=[id1,id2]` | `--servers.1.id=id1 --servers.2.id=id2` | 数组格式 |
| `--remote_console={protocol:vnc}` | `--remote_console.protocol=vnc` | 嵌套对象格式 |
| `hcloud VPC ListPublicips` | `hcloud EIP ListPublicips/v3` | EIP独立服务 |
| `hcloud VPC ListSecurityGroups` | `hcloud VPC ListSecurityGroups/v3` | v3后缀 |
| `--os-start.1=<id>` | `--os-start.servers.1.id=<id>` | 批量操作格式 |
| `--delete_publicip` | `--delete_publicip=true` | 布尔需显式值 |
| `--dim=instance_id:id` | `--dim.0=instance_id,id` | 维度用逗号分隔 |

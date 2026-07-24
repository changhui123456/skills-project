# 常见操作工作流

## 概述

本文档提供华为云常见操作的完整CLI工作流，从零开始一步步完成。

---

## 工作流1: 创建ECS实例（完整流程）

### 步骤

```bash
# 1. 查看可用规格
hcloud ECS ListFlavors --cli-region=cn-north-4

# 2. 查看可用镜像（通过IMS服务）
hcloud IMS ListImages --cli-region=cn-north-4 --limit=10

# 3. 查看VPC和子网
hcloud VPC ListVpcs --cli-region=cn-north-4
hcloud VPC ListSubnets --cli-region=cn-north-4

# 4. 查看安全组
hcloud VPC ListSecurityGroups/v3 --cli-region=cn-north-4

# 5. 创建实例
hcloud ECS CreateServers \
  --server.name=my-instance \
  --server.imageRef=<image-id> \
  --server.flavorRef=ac8.large.2 \
  --server.vpcid=<vpc-id> \
  --server.subnet_id=<subnet-id> \
  --server.security_groups.1.id=<sg-id> \
  --server.adminPass=MyP@ssw0rd123! \
  --server.publicip.eip.bandwidth.sharetype=PER \
  --server.publicip.eip.bandwidth.size=5 \
  --server.publicip.eip.bandwidth.charge_mode=bandwidth \
  --cli-region=cn-north-4

# 6. 等待创建完成（轮询状态）
hcloud ECS ShowServer --server_id=<new-id> --cli-region=cn-north-4
# 直到 status=ACTIVE

# 7. 验证SSH连接
sshpass -p 'MyP@ssw0rd123!' ssh -o StrictHostKeyChecking=no root@<public-ip> "echo OK"
```

---

## 工作流2: 创建VPC+子网+安全组+实例

### 步骤

```bash
# 1. 创建VPC
hcloud VPC CreateVpc --vpc.name=my-vpc --vpc.cidr=10.0.0.0/16 --cli-region=cn-north-4
# 记录返回的 vpc.id

# 2. 创建子网
hcloud VPC CreateSubnet \
  --subnet.name=my-subnet \
  --subnet.cidr=10.0.1.0/24 \
  --subnet.vpc_id=<vpc-id> \
  --subnet.gateway_ip=10.0.1.1 \
  --cli-region=cn-north-4
# 记录返回的 subnet.id

# 3. 创建安全组
hcloud VPC CreateSecurityGroup/v3 \
  --security_group.name=my-sg \
  --security_group.vpc_id=<vpc-id> \
  --cli-region=cn-north-4
# 记录返回的 security_group.id

# 4. 添加安全组规则
# SSH入方向
hcloud VPC CreateSecurityGroupRule/v3 \
  --security_group_id=<sg-id> \
  --security_group_rule.direction=ingress \
  --security_group_rule.protocol=tcp \
  --security_group_rule.port_range_min=22 \
  --security_group_rule.port_range_max=22 \
  --security_group_rule.remote_ip_prefix=0.0.0.0/0 \
  --security_group_rule.description="Allow SSH" \
  --cli-region=cn-north-4

# HTTP入方向
hcloud VPC CreateSecurityGroupRule/v3 \
  --security_group_id=<sg-id> \
  --security_group_rule.direction=ingress \
  --security_group_rule.protocol=tcp \
  --security_group_rule.port_range_min=80 \
  --security_group_rule.port_range_max=80 \
  --security_group_rule.remote_ip_prefix=0.0.0.0/0 \
  --security_group_rule.description="Allow HTTP" \
  --cli-region=cn-north-4

# 5. 创建ECS实例（使用刚创建的资源）
hcloud ECS CreateServers \
  --server.name=my-instance \
  --server.imageRef=<image-id> \
  --server.flavorRef=ac8.large.2 \
  --server.vpcid=<vpc-id> \
  --server.subnet_id=<subnet-id> \
  --server.security_groups.1.id=<sg-id> \
  --server.adminPass=MyP@ssw0rd123! \
  --server.publicip.eip.bandwidth.sharetype=PER \
  --server.publicip.eip.bandwidth.size=5 \
  --server.publicip.eip.bandwidth.charge_mode=bandwidth \
  --cli-region=cn-north-4
```

---

## 工作流3: 为实例添加安全组规则

### 步骤

```bash
# 1. 查看实例的安全组
hcloud ECS ShowServer --server_id=<instance-id> --cli-region=cn-north-4
# 从返回的 security_groups 获取 sg-id

# 2. 查看当前规则
hcloud VPC ShowSecurityGroup/v3 --security_group_id=<sg-id> --cli-region=cn-north-4

# 3. 添加规则（如添加HTTPS）
hcloud VPC CreateSecurityGroupRule/v3 \
  --security_group_id=<sg-id> \
  --security_group_rule.direction=ingress \
  --security_group_rule.protocol=tcp \
  --security_group_rule.port_range_min=443 \
  --security_group_rule.port_range_max=443 \
  --security_group_rule.remote_ip_prefix=0.0.0.0/0 \
  --security_group_rule.description="Allow HTTPS" \
  --cli-region=cn-north-4

# 4. 验证规则已生效
hcloud VPC ShowSecurityGroup/v3 --security_group_id=<sg-id> --cli-region=cn-north-4

# 5. 测试端口连通性
nc -zv <public-ip> 443
```

---

## 工作流4: 绑定/解绑弹性公网IP

### 绑定EIP到实例

```bash
# 1. 申请EIP
hcloud EIP CreatePublicip/v3 \
  --publicip.type=EIP \
  --bandwidth.name=my-eip-bw \
  --bandwidth.size=5 \
  --bandwidth.share_type=PER \
  --bandwidth.charge_mode=bandwidth \
  --cli-region=cn-north-4
# 记录返回的 publicip_id 和 publicip_address

# 2. 绑定到实例
hcloud EIP AssociatePublicip/v3 \
  --publicip_id=<eip-id> \
  --publicip_associate.instance_id=<instance-id> \
  --publicip_associate.instance_type=ECS \
  --cli-region=cn-north-4

# 3. 验证绑定
hcloud EIP ListPublicips/v3 --cli-region=cn-north-4
```

### 解绑并释放EIP

```bash
# 1. 解绑
hcloud EIP DisassociatePublicip/v3 \
  --publicip_id=<eip-id> \
  --cli-region=cn-north-4

# 2. 释放EIP
hcloud EIP DeletePublicip/v3 \
  --publicip_id=<eip-id> \
  --cli-region=cn-north-4
```

---

## 工作流5: 扩容云硬盘

### 步骤

```bash
# 1. 查看当前云硬盘
hcloud EVS ListVolumes --cli-region=cn-north-4

# 2. 查看硬盘详情
hcloud EVS ShowVolume --volume_id=<vol-id> --cli-region=cn-north-4

# 3. 扩容（在线扩容，无需停机）
hcloud EVS ExtendVolume \
  --volume_id=<vol-id> \
  --volume.size=<new-size-gb> \
  --cli-region=cn-north-4

# 4. SSH登录扩展文件系统
sshpass -p '<password>' ssh root@<ip> "
  # 查看磁盘
  lsblk
  # 扩展分区（如/dev/vda1）
  growpart /dev/vda 1
  # 扩展文件系统
  resize2fs /dev/vda1   # ext4
  # 或 xfs_growfs /       # xfs
"
```

---

## 工作流6: 清理资源（删除实例+释放资源）

### 步骤

```bash
# 1. 列出所有实例
hcloud ECS ListServersDetails --cli-region=cn-north-4

# 2. 删除实例（同时释放EIP和云盘）
hcloud ECS DeleteServers \
  --servers.1.id=<instance-id> \
  --delete_publicip=true \
  --delete_volume=true \
  --cli-region=cn-north-4

# 3. 确认删除完成
hcloud ECS ListServersDetails --cli-region=cn-north-4

# 4. 清理安全组（如不再需要）
hcloud VPC DeleteSecurityGroup/v3 \
  --security_group_id=<sg-id> \
  --cli-region=cn-north-4

# 5. 清理VPC和子网（如不再需要）
hcloud VPC DeleteSubnet --vpc_id=<vpc-id> --subnet_id=<subnet-id> --cli-region=cn-north-4
hcloud VPC DeleteVpc --vpc_id=<vpc-id> --cli-region=cn-north-4
```

---

## 工作流7: 查看监控指标

### 步骤

```bash
# 1. 查看可用指标
hcloud CES ListMetrics --namespace=SYS.ECS --cli-region=cn-north-4

# 2. 查看CPU利用率（最近1小时）
hcloud CES ShowMetricData \
  --namespace=SYS.ECS \
  --metric_name=cpu_util \
  --dim.0=instance_id,<instance-id> \
  --from=$(date -d '1 hour ago' +%s)000 \
  --to=$(date +%s)000 \
  --period=300 \
  --filter=average \
  --cli-region=cn-north-4

# 3. 查看内存利用率
hcloud CES ShowMetricData \
  --namespace=SYS.ECS \
  --metric_name=mem_util \
  --dim.0=instance_id,<instance-id> \
  --from=$(date -d '1 hour ago' +%s)000 \
  --to=$(date +%s)000 \
  --period=300 \
  --filter=average \
  --cli-region=cn-north-4

# 4. 查看磁盘利用率
hcloud CES ShowMetricData \
  --namespace=SYS.ECS \
  --metric_name=disk_util_inband \
  --dim.0=instance_id,<instance-id> \
  --dim.1=name,/dev/vda1 \
  --from=$(date -d '1 hour ago' +%s)000 \
  --to=$(date +%s)000 \
  --period=300 \
  --filter=average \
  --cli-region=cn-north-4

# 5. 查看告警
hcloud CES ListAlarms --cli-region=cn-north-4
```

---

## 工作流8: SSH深度诊断

### 前提
- 实例有公网IP
- 安全组放行22端口
- 知道root密码

### 步骤

```bash
# 1. 基础连接测试
sshpass -p '<password>' ssh -o StrictHostKeyChecking=no root@<ip> "echo OK"

# 2. 系统概览
sshpass -p '<password>' ssh -o StrictHostKeyChecking=no root@<ip> "
  echo '=== System ===' && uname -a
  echo '=== Uptime ===' && uptime
  echo '=== Memory ===' && free -h
  echo '=== Disk ===' && df -h
  echo '=== CPU ===' && nproc
"

# 3. 网络检查
sshpass -p '<password>' ssh -o StrictHostKeyChecking=no root@<ip> "
  echo '=== Interfaces ===' && ip addr show
  echo '=== Routes ===' && ip route show
  echo '=== Listening ===' && ss -tlnp
  echo '=== Firewall ===' && (iptables -L -n 2>/dev/null || firewall-cmd --list-all 2>/dev/null)
"

# 4. 进程检查
sshpass -p '<password>' ssh -o StrictHostKeyChecking=no root@<ip> "
  echo '=== Top CPU ===' && ps aux --sort=-%cpu | head -10
  echo '=== Top Mem ===' && ps aux --sort=-%mem | head -10
  echo '=== Failed ===' && systemctl list-units --state=failed
"

# 5. 日志检查
sshpass -p '<password>' ssh -o StrictHostKeyChecking=no root@<ip> "
  echo '=== Errors ===' && (tail -200 /var/log/syslog 2>/dev/null || tail -200 /var/log/messages 2>/dev/null) | grep -i 'error\|fail' | tail -20
"
```

### SSH失败时使用VNC

```bash
# 获取VNC控制台URL
hcloud ECS ShowServerRemoteConsole \
  --server_id=<instance-id> \
  --remote_console.protocol=vnc \
  --remote_console.type=novnc \
  --cli-region=cn-north-4
# 在浏览器中打开URL进行控制台操作
```

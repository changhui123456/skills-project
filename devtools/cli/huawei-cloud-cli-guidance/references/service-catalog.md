# 华为云全服务目录与命令速查

## 概述

KooCLI v7.2.2+ 支持以下100+云服务。按功能域分类，列出服务代码和常用操作。

---

## 🔲 计算

### ECS - 弹性云服务器
```bash
hcloud ECS ListServersDetails --cli-region=<r>          # 列出实例
hcloud ECS ShowServer --server_id=<id> --cli-region=<r>  # 实例详情
hcloud ECS NovaShowServer --server_id=<id> --cli-region=<r>  # Nova详情
hcloud ECS CreateServers --server.name=<n> ... --cli-region=<r>  # 创建实例
hcloud ECS DeleteServers --servers.1.id=<id> --delete_publicip=true --delete_volume=true --cli-region=<r>  # 删除实例
hcloud ECS NovaStartServers --os-start.servers.1.id=<id> --cli-region=<r>  # 启动
hcloud ECS NovaStopServers --os-stop.servers.1.id=<id> --cli-region=<r>   # 停止
hcloud ECS NovaRebootServers --os-reboot.servers.1.id=<id> --cli-region=<r>  # 重启
hcloud ECS ShowServerRemoteConsole --server_id=<id> --remote_console.protocol=vnc --remote_console.type=novnc --cli-region=<r>  # VNC控制台
hcloud ECS ListFlavors --cli-region=<r>                  # 可用规格
hcloud ECS NovaListVersions --cli-region=<r>             # API版本
```

### BMS - 裸金属服务器
```bash
hcloud BMS ListServersDetails --cli-region=<r>
hcloud BMS ShowServer --server_id=<id> --cli-region=<r>
```

### AS - 弹性伸缩
```bash
hcloud AS ListScalingGroups --cli-region=<r>
hcloud AS ShowScalingGroup --scaling_group_id=<id> --cli-region=<r>
hcloud AS CreateScalingGroup --cli-region=<r>
```

### CCE - 云容器引擎
```bash
hcloud CCE ListClusters --cli-region=<r>
hcloud CCE ShowCluster --cluster_id=<id> --cli-region=<r>
hcloud CCE CreateCluster --cli-region=<r>
hcloud CCE ListNodes --cluster_id=<id> --cli-region=<r>
```

### CCI - 云容器实例
```bash
hcloud CCI ListNamespaces --cli-region=<r>
```

### FunctionGraph - 函数工作流
```bash
hcloud FunctionGraph ListFunctions --cli-region=<r>
hcloud FunctionGraph ShowFunction --function_urn=<urn> --cli-region=<r>
```

---

## 🌐 网络

### VPC - 虚拟私有云
```bash
hcloud VPC ListVpcs --cli-region=<r>                     # 列出VPC
hcloud VPC ShowVpc --vpc_id=<id> --cli-region=<r>        # VPC详情
hcloud VPC ListSubnets --cli-region=<r>                   # 列出子网
hcloud VPC ShowSubnet --subnet_id=<id> --cli-region=<r>   # 子网详情
hcloud VPC ListSecurityGroups/v3 --cli-region=<r>         # 安全组列表
hcloud VPC ShowSecurityGroup/v3 --security_group_id=<id> --cli-region=<r>  # 安全组详情
hcloud VPC ListSecurityGroupRules/v3 --security_group_id.1=<id> --cli-region=<r>  # 安全组规则
hcloud VPC CreateSecurityGroupRule/v3 --security_group_id=<id> --security_group_rule.direction=ingress --security_group_rule.protocol=tcp --security_group_rule.port_range_min=<port> --security_group_rule.port_range_max=<port> --security_group_rule.remote_ip_prefix=<cidr> --cli-region=<r>  # 添加规则
hcloud VPC DeleteSecurityGroupRule/v3 --security_group_rule_id=<rule-id> --cli-region=<r>  # 删除规则
```

### EIP - 弹性公网IP
```bash
hcloud EIP ListPublicips/v3 --cli-region=<r>
hcloud EIP CreatePublicip/v3 --publicip.type=EIP --bandwidth.name=<n> --bandwidth.size=5 --bandwidth.share_type=PER --bandwidth.charge_mode=bandwidth --cli-region=<r>
hcloud EIP AssociatePublicip/v3 --publicip_id=<eip> --publicip_associate.instance_id=<ecs> --publicip_associate.instance_type=ECS --cli-region=<r>
hcloud EIP DisassociatePublicip/v3 --publicip_id=<eip> --cli-region=<r>
hcloud EIP DeletePublicip/v3 --publicip_id=<eip> --cli-region=<r>
```

### ELB - 弹性负载均衡
```bash
hcloud ELB ListLoadBalancers --cli-region=<r>
hcloud ELB ShowLoadBalancer --loadbalancer_id=<id> --cli-region=<r>
hcloud ELB ListListeners --loadbalancer_id=<id> --cli-region=<r>
hcloud ELB ListPools --loadbalancer_id=<id> --cli-region=<r>
```

### NAT - NAT网关
```bash
hcloud NAT ListNatGateways --cli-region=<r>
hcloud NAT ShowNatGateway --nat_gateway_id=<id> --cli-region=<r>
```

### DNS - 域名解析
```bash
hcloud DNS ListPublicZones --cli-region=<r>
hcloud DNS ListPrivateZones --type=private --cli-region=<r>
hcloud DNS ShowPublicZone --zone_id=<id> --cli-region=<r>
hcloud DNS ListRecordSets --zone_id=<id> --cli-region=<r>
```

### VPN - 虚拟专用网络
```bash
hcloud VPN ListVpnGateways --cli-region=<r>
hcloud VPN ShowVpnGateway --vpn_gateway_id=<id> --cli-region=<r>
```

### ER - 企业路由器
```bash
hcloud ER ListInstances --cli-region=<r>
hcloud ER ShowInstance --instance_id=<id> --cli-region=<r>
```

### CFW - 云防火墙
```bash
hcloud CFW ListFirewalls --cli-region=<r>
```

---

## 💾 存储

### EVS - 云硬盘
```bash
hcloud EVS ListVolumes --cli-region=<r>
hcloud EVS ShowVolume --volume_id=<id> --cli-region=<r>
hcloud EVS CreateVolume --volume.name=<n> --volume.size=<gb> --volume.volume_type=SSD --volume.availability_zone=<az> --cli-region=<r>
hcloud EVS AttachVolume --volume_id=<id> --server_id=<ecs-id> --cli-region=<r>
hcloud EVS DetachVolume --volume_id=<id> --server_id=<ecs-id> --cli-region=<r>
hcloud EVS ExtendVolume --volume_id=<id> --volume.size=<new-gb> --cli-region=<r>
```

### CBR - 云备份恢复
```bash
hcloud CBR ListVaults --cli-region=<r>
hcloud CBR ShowVault --vault_id=<id> --cli-region=<r>
```

### SFSTurbo - 弹性文件服务
```bash
hcloud SFSTurbo ListShares --cli-region=<r>
hcloud SFSTurbo ShowShare --share_id=<id> --cli-region=<r>
```

---

## 🗄️ 数据库

### RDS - 关系型数据库
```bash
hcloud RDS ListInstances --cli-region=<r>
hcloud RDS ShowInstance --instance_id=<id> --cli-region=<r>
hcloud RDS ListBackups --instance_id=<id> --cli-region=<r>
hcloud RDS CreateInstance --cli-region=<r>
```

### GaussDB - 分布式数据库
```bash
hcloud GaussDB ListInstances --cli-region=<r>
hcloud GaussDB ShowInstance --instance_id=<id> --cli-region=<r>
```

### GaussDBforNoSQL - NoSQL数据库
```bash
hcloud GaussDBforNoSQL ListInstances --cli-region=<r>
```

### GaussDBforopenGauss - openGauss
```bash
hcloud GaussDBforopenGauss ListInstances --cli-region=<r>
```

### DCS - 分布式缓存服务
```bash
hcloud DCS ListInstances --cli-region=<r>
hcloud DCS ShowInstance --instance_id=<id> --cli-region=<r>
```

### DDS - 文档数据库服务
```bash
hcloud DDS ListInstances --cli-region=<r>
```

### DRS - 数据复制服务
```bash
hcloud DRS ListJobs --cli-region=<r>
```

---

## 🔒 安全

### IAM - 身份与访问管理
```bash
hcloud IAM KeystoneListUsers --cli-region=<r>
hcloud IAM KeystoneShowUser --user_id=<id> --cli-region=<r>
hcloud IAM ListPolicies --cli-region=<r>
hcloud IAM ShowPolicy --policy_id=<id> --cli-region=<r>
hcloud IAM ListRoles --cli-region=<r>
hcloud IAM ListGroups --cli-region=<r>
```

### HSS - 主机安全服务
```bash
hcloud HSS ListHosts --cli-region=<r>
```

### WAF - Web应用防火墙
```bash
hcloud WAF ListInstances --cli-region=<r>
```

### KMS - 密钥管理服务
```bash
hcloud KMS ListKeys --cli-region=<r>
hcloud KMS ShowKey --key_id=<id> --cli-region=<r>
```

### Anti-DDoS - 抗DDoS
```bash
hcloud Anti-DDoS ListConfigs --cli-region=<r>
```

### CTS - 云审计服务
```bash
hcloud CTS ListTraces --cli-region=<r>
```

### CSMS - 凭据管理服务
```bash
hcloud CSMS ListSecrets --cli-region=<r>
```

---

## 📊 监控与运维

### CES - 云监控服务
```bash
hcloud CES ListMetrics --namespace=SYS.ECS --cli-region=<r>
hcloud CES ShowMetricData --namespace=SYS.ECS --metric_name=cpu_util --dim.0=instance_id,<id> --from=<ts>000 --to=<ts>000 --period=300 --filter=average --cli-region=<r>
hcloud CES ListAlarms --cli-region=<r>
hcloud CES ShowAlarm --alarm_id=<id> --cli-region=<r>
```

### LTS - 日志服务
```bash
hcloud LTS ListLogGroups --cli-region=<r>
hcloud LTS ListLogStreams --group_id=<id> --cli-region=<r>
```

### AOM - 应用运维管理
```bash
hcloud AOM ListApplications --cli-region=<r>
```

### Config - 配置审计
```bash
hcloud Config ListResources --cli-region=<r>
```

---

## 📨 消息与通知

### SMN - 消息通知服务
```bash
hcloud SMN ListTopics --cli-region=<r>
hcloud SMN ShowTopic --topic_urn=<urn> --cli-region=<r>
hcloud SMN ListSubscriptions --topic_urn=<urn> --cli-region=<r>
```

### Kafka - 分布式消息Kafka
```bash
hcloud Kafka ListInstances --cli-region=<r>
```

### RabbitMQ - 分布式消息RabbitMQ
```bash
hcloud RabbitMQ ListInstances --cli-region=<r>
```

### RocketMQ - 分布式消息RocketMQ
```bash
hcloud RocketMQ ListInstances --cli-region=<r>
```

---

## 🔧 开发工具

### APIG - API网关
```bash
hcloud APIG ListInstances --cli-region=<r>
hcloud APIG ListApis --instance_id=<id> --cli-region=<r>
```

### CSE - 微服务引擎
```bash
hcloud CSE ListEngines --cli-region=<r>
```

### CodeArts系列
```bash
hcloud CodeArtsRepo ListRepositories --cli-region=<r>
hcloud CodeArtsBuild ListBuildRecords --cli-region=<r>
hcloud CodeArtsPipeline ListPipelines --cli-region=<r>
hcloud CodeArtsDeploy ListDeployTasks --cli-region=<r>
```

---

## 🧠 大数据与AI

### ModelArts
```bash
hcloud ModelArts ListNotebooks --cli-region=<r>
hcloud ModelArts ListTrainingJobs --cli-region=<r>
```

### DLI - 数据湖探索
```bash
hcloud DLI ListQueues --cli-region=<r>
```

### DWS - 数据仓库服务
```bash
hcloud DWS ListClusters --cli-region=<r>
```

### MRS - MapReduce服务
```bash
hcloud MRS ListClusters --cli-region=<r>
```

### DIS - 数据接入服务
```bash
hcloud DIS ListStreams --cli-region=<r>
```

---

## 📺 媒体

### VOD - 视频点播
```bash
hcloud VOD ListAssets --cli-region=<r>
```

### Live - 直播
```bash
hcloud Live ListDomains --cli-region=<r>
```

### MPC - 媒体处理
```bash
hcloud MPC ListTranscodingTasks --cli-region=<r>
```

---

## 🏢 企业与管理

### EPS - 企业项目
```bash
hcloud EPS ListEnterpriseProjects --cli-region=<r>
```

### Organizations - 组织管理
```bash
hcloud Organizations ListAccounts --cli-region=<r>
```

### TMS - 标签管理服务
```bash
hcloud TMS ListTags --resource_type=ecs --cli-region=<r>
```

### RMS - 资源管理服务
```bash
hcloud RMS ListResources --cli-region=<r>
```

---

## ⚠️ KooCLI不支持的服务

以下服务需通过控制台或其他专用CLI工具操作：

| 服务 | 替代方案 |
|------|---------|
| BSS (账单) | 浏览器访问 https://bss.huaweicloud.com |
| OBS (对象存储) | 使用 obsutil CLI |
| Console (控制台) | 浏览器访问 |

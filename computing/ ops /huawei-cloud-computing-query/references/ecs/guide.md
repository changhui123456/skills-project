# ECS Python 脚本使用指南

---

## 列表查询脚本

### list_servers_details.py — 查询 ECS 实例列表

作用：查询 ECS 实例列表，包括 ID、名称、状态、flavor_id、vCPU、memory(GiB)。
用法详见：python scripts/ecs/list_servers_details.py -h

---

### list_servers_details_by_id.py — 按实例 ID 查询 ECS 详情

作用：查询 ECS 实例详情，包括 名称、状态、flavor_id、vCPU、memory(GiB)。
用法详见：python scripts/ecs/list_servers_details_by_id.py -h

---

### list_cloud_servers.py — 查询云服务器列表（v1.1）

作用：查询 ECS 云服务器列表，包括 名称、状态、flavor_id、vCPU、ram(GiB)、镜像ID。
用法详见：python scripts/ecs/list_cloud_servers.py -h

---

### list_flavors.py — 查询 ECS 规格列表

作用：查询 ECS 规格列表，包括 规格名称、vCPU、内存(GiB)。
用法详见：python scripts/ecs/list_flavors.py -h

---

### list_flavor_sell_policies.py — 查询规格销售策略

作用：查询 ECS 规格销售策略列表，包括 ID、flavor_id、销售模式、销售状态、availability_zone_id。
用法详见：python scripts/ecs/list_flavor_sell_policies.py -h

---

### list_resize_flavors.py — 查询变更规格列表

作用：查询 ECS 变更规格列表，包括 flavor_id、名称、vCPU、ram(GiB)。
用法详见：python scripts/ecs/list_resize_flavors.py -h

---

### list_server_az_info.py — 查询可用区列表

作用：查询 ECS 可用区信息列表，包括 availability_zone_id、类型。
用法详见：python scripts/ecs/list_server_az_info.py -h

---

### list_server_block_devices.py — 查询服务器磁盘列表详情

作用：查询 ECS 服务器块设备列表，包括 云硬盘ID、boot_index、device、size(GB)。
用法详见：python scripts/ecs/list_server_block_devices.py -h

---

### list_server_groups.py — 查询服务器组列表

作用：查询 ECS 服务器组列表，包括 ID、名称、策略。
用法详见：python scripts/ecs/list_server_groups.py -h

---

### list_server_interfaces.py — 查询服务器网卡信息

作用：查询 ECS 服务器网卡列表，包括 端口ID、网络ID、ip_addr、mac_addr。
用法详见：python scripts/ecs/list_server_interfaces.py -h

---

### list_server_tags.py — 查询项目标签

作用：查询 ECS 服务器标签列表，包括 键、values。
用法详见：python scripts/ecs/list_server_tags.py -h

---

### list_server_volume_attachments.py — 查询服务器挂载磁盘列表

作用：查询 ECS 服务器挂载卷列表，包括 ID、device、服务器ID、云硬盘ID。
用法详见：python scripts/ecs/list_server_volume_attachments.py -h

---

### list_servers_by_tag.py — 按标签查询服务器列表

作用：按标签查询 ECS 服务器列表，包括 资源ID、资源名称、标签。
用法详见：python scripts/ecs/list_servers_by_tag.py -h

---

### list_launch_template_versions.py — 查询模板版本列表

作用：查询 ECS 启动模板版本列表，包括 version_number、启动模板ID、创建时间。
用法详见：python scripts/ecs/list_launch_template_versions.py -h

---

### list_recycle_bin_servers.py — 查询回收站服务器列表

作用：查询 ECS 回收站服务器列表，包括 ID、名称、状态、flavor_id。
用法详见：python scripts/ecs/list_recycle_bin_servers.py -h

---

### list_scheduled_events.py — 查询计划事件列表

作用：查询 ECS 计划事件列表，包括 ID、instance_id、类型、state、publish_time。
用法详见：python scripts/ecs/list_scheduled_events.py -h

---

### list_templates.py — 查询启动模板列表

作用：查询 ECS 启动模板列表，包括 ID、名称、创建时间。
用法详见：python scripts/ecs/list_templates.py -h

---

### show_server.py — 查询服务器详情

作用：查询 ECS 服务器详情。
用法详见：python scripts/ecs/show_server.py -h

---

### show_server_block_device.py — 查询单个磁盘详情

作用：查询 ECS 服务器块设备详情。
用法详见：python scripts/ecs/show_server_block_device.py -h

---

### show_server_group.py — 查询服务器组详情

作用：查询 ECS 服务器组详情。
用法详见：python scripts/ecs/show_server_group.py -h

---

### show_server_limits.py — 查询租户配额

作用：查询 ECS 服务器配额。
用法详见：python scripts/ecs/show_server_limits.py -h

---

### show_server_tags.py — 查询服务器标签

作用：查询 ECS 服务器标签详情，包括 键、值。
用法详见：python scripts/ecs/show_server_tags.py -h

---

### show_server_password.py — 获取服务器密码

作用：查询 ECS 服务器密码。
用法详见：python scripts/ecs/show_server_password.py -h

---

### show_server_remote_console.py — 获取 VNC 远程登录地址

作用：查询 ECS 服务器远程控制台。
用法详见：python scripts/ecs/show_server_remote_console.py -h

---

### show_server_attachable_nic_num.py — 查询可挂载网卡数

作用：查询 ECS 服务器可挂载网卡数量。
用法详见：python scripts/ecs/show_server_attachable_nic_num.py -h

---

### show_appendable_volume_quota.py — 查询可追加卷数量

作用：查询 ECS 服务器可挂载卷配额。
用法详见：python scripts/ecs/show_appendable_volume_quota.py -h

---

### show_flavor_capacity.py — 查询规格容量

作用：查询 ECS 规格容量，包括 可用区、区域ID、prefer。
用法详见：python scripts/ecs/show_flavor_capacity.py -h

---

### show_metadata_options.py — 查询元数据配置

作用：查询 ECS 服务器元数据选项。
用法详见：python scripts/ecs/show_metadata_options.py -h

---

### show_recycle_bin.py — 查询回收站配置

作用：查询 ECS 回收站配置。
用法详见：python scripts/ecs/show_recycle_bin.py -h

---

### show_reset_password_flag.py — 查询是否支持重置密码

作用：查询 ECS 服务器重置密码标志。
用法详见：python scripts/ecs/show_reset_password_flag.py -h

---

### show_serial_console_actions.py — 获取串口登录地址

作用：查询 ECS 服务器串口控制台。
用法详见：python scripts/ecs/show_serial_console_actions.py -h

---

### show_job.py — 查询异步任务状态

作用：查询 ECS 异步任务详情。
用法详见：python scripts/ecs/show_job.py -h

---

### nova_list_keypairs.py — 查询 SSH 密钥对列表

作用：查询 ECS SSH 密钥对列表，包括 name、type、fingerprint。
用法详见：python scripts/ecs/nova_list_keypairs.py -h

---

### nova_show_keypair.py — 查询 SSH 密钥对详情

作用：查询 ECS SSH 密钥对详情，包括 name、type、fingerprint、public_key、created_at、user_id。
用法详见：python scripts/ecs/nova_show_keypair.py -h

---

### nova_list_server_security_groups.py — 查询服务器安全组列表

作用：查询 ECS 服务器安全组列表，包括 id、name、description。
用法详见：python scripts/ecs/nova_list_server_security_groups.py -h

---

### nova_show_flavor_extra_specs.py — 查询规格扩展属性

作用：查询 ECS 规格扩展属性，包括 key、value。
用法详见：python scripts/ecs/nova_show_flavor_extra_specs.py -h

---

### nova_show_server_interface.py — 查询服务器指定网卡详情

作用：查询 ECS 服务器指定网卡详情，包括 port_id、net_id、mac_addr、port_state、fixed_ips。
用法详见：python scripts/ecs/nova_show_server_interface.py -h

# BMS（裸金属服务器）查询指南

## 列表查询

### list_bare_metal_servers.py — 查询裸金属服务器列表（OpenStack原生，含总数）

作用：查询裸金属服务器列表，返回服务器ID、名称、状态、规格、vCPU、内存、磁盘、可用区、创建时间等关键信息，包含总数。
用法详见：python scripts/bms/list_bare_metal_servers.py -h

### list_bare_metal_servers_detail.py — 查询裸金属服务器详情列表（OpenStack原生，无总数）

作用：查询裸金属服务器详情列表，返回服务器ID、名称、状态、规格、vCPU、内存、磁盘、可用区、创建时间等关键信息，不含总数。
用法详见：python scripts/bms/list_bare_metal_servers_detail.py -h

### list_bare_metal_server_details.py — 查询裸金属服务器详情（按ID）

作用：按服务器ID查询单个裸金属服务器的详细信息，包括规格详情（GPU/ASIC加速器）、镜像、元数据（计费模式、操作系统类型等）、挂载磁盘、标签等。
用法详见：python scripts/bms/list_bare_metal_server_details.py -h

### list_baremetal_flavor_detail_extends.py — 查询裸金属服务器规格详情列表

作用：查询裸金属服务器规格详情列表，返回规格ID、名称、vCPU、内存、磁盘、资源类型、CPU架构、磁盘详情等信息。
用法详见：python scripts/bms/list_baremetal_flavor_detail_extends.py -h

---

## 详情查询

### show_available_resource.py — 查询可用区资源信息

作用：查询指定可用区和规格的裸金属服务器资源可用情况，返回可用区、规格ID、可用数量、状态。
用法详见：python scripts/bms/show_available_resource.py -h

### show_baremetal_server_interface_attachments.py — 查询裸金属服务器网卡信息

作用：查询指定裸金属服务器的网卡信息，返回端口ID、网络ID、MAC地址、端口状态、驱动模式、PCI地址、IP地址等。
用法详见：python scripts/bms/show_baremetal_server_interface_attachments.py -h

### show_baremetal_server_tags.py — 查询裸金属服务器标签

作用：查询指定裸金属服务器的标签列表，返回标签键和值。
用法详见：python scripts/bms/show_baremetal_server_tags.py -h

### show_baremetal_server_volume_info.py — 查询裸金属服务器挂载磁盘信息

作用：查询指定裸金属服务器挂载的磁盘信息，返回磁盘ID、服务器ID、卷ID、设备名。
用法详见：python scripts/bms/show_baremetal_server_volume_info.py -h

### show_job_infos.py — 查询异步任务状态

作用：查询异步任务的状态信息，返回任务ID、状态、类型、开始时间、结束时间、错误码、失败原因等，包含子任务信息。
用法详见：python scripts/bms/show_job_infos.py -h

### show_metadata_options.py — 查询裸金属服务器元数据配置

作用：查询指定裸金属服务器的元数据配置，返回 http_endpoint 和 http_tokens 配置。
用法详见：python scripts/bms/show_metadata_options.py -h

### show_reset_pwd.py — 查询裸金属服务器是否支持重置密码

作用：查询指定裸金属服务器是否支持重置密码，返回 resetpwd_flag 标识。
用法详见：python scripts/bms/show_reset_pwd.py -h

### show_server_remote_console.py — 获取裸金属服务器VNC远程登录地址

作用：获取指定裸金属服务器的VNC远程登录地址，返回协议、类型和URL。
用法详见：python scripts/bms/show_server_remote_console.py -h

### show_specified_version.py — 查询BMS API指定版本信息

作用：查询BMS API指定版本信息，返回版本ID、状态、最小版本、更新时间等。
用法详见：python scripts/bms/show_specified_version.py -h

### show_tenant_quota.py — 查询裸金属服务器租户配额

作用：查询当前租户的裸金属服务器配额信息，返回最大实例数、已用实例数、最大核数、已用核数、最大内存、已用内存等配额数据。
用法详见：python scripts/bms/show_tenant_quota.py -h

### show_windows_baremetal_server_pwd.py — 查询Windows裸金属服务器初始密码

作用：查询指定Windows裸金属服务器的初始密码，返回加密后的密码。
用法详见：python scripts/bms/show_windows_baremetal_server_pwd.py -h

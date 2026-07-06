# VPN Python 脚本使用指南

---

## 可用区查询

### list_availability_zones.py — 查询 VPN 可用区列表

作用：查询 VPN 可用区列表，包括 类别、类型、可用区列表。
用法详见：python scripts/vpn/list_availability_zones.py -h

---

### list_extended_availability_zones.py — 查询扩展可用区列表

作用：查询 VPN 扩展可用区列表，包括 名称、公共边界组、可用规格。
用法详见：python scripts/vpn/list_extended_availability_zones.py -h

---

### list_p2c_vgw_availability_zones.py — 查询 P2C VPN 网关可用区列表

作用：查询 P2C VPN 网关可用区列表。
用法详见：python scripts/vpn/list_p2c_vgw_availability_zones.py -h

### list_cgws.py — 查询对端网关列表

作用：查询对端网关列表，包括 ID、名称、BGP AS号、标识类型、标识值、创建时间。
用法详见：python scripts/vpn/list_cgws.py -h

---

### show_cgw.py — 查询对端网关详情

作用：查询对端网关详情，包括 ID、名称、BGP AS号、标识类型、标识值、CA证书、创建时间、更新时间。
用法详见：python scripts/vpn/show_cgw.py -h

### list_vgws.py — 查询 VPN 网关列表

作用：查询 VPN 网关列表，包括 ID、名称、状态、关联类型、VPC ID、规格、连接数、已用连接数、企业项目ID。
用法详见：python scripts/vpn/list_vgws.py -h

---

### show_vgw.py — 查询 VPN 网关详情

作用：查询 VPN 网关详情，包括 ID、名称、状态、关联类型、IP版本、VPC ID、规格、连接数、已用连接数、企业项目ID、HA模式、创建时间、更新时间。
用法详见：python scripts/vpn/show_vgw.py -h

---

### show_vpn_gateway_certificate.py — 查询 VPN 网关证书

作用：查询 VPN 网关证书详情，包括 ID、名称、VPN网关ID、状态、颁发者、签名算法、证书序列号、证书主题、证书过期时间、创建时间、更新时间。
用法详见：python scripts/vpn/show_vpn_gateway_certificate.py -h

---

### show_vpn_gateway_routing_table.py — 查询 VPN 网关路由表

作用：查询 VPN 网关路由表，包括 目的地址、下一跳、出接口IP、来源、AS路径、MED值。
用法详见：python scripts/vpn/show_vpn_gateway_routing_table.py -h

### list_vpn_connections.py — 查询 VPN 连接列表

作用：查询 VPN 连接列表，包括 ID、名称、状态、VPN网关ID、对端网关ID、连接模式、企业项目ID。
用法详见：python scripts/vpn/list_vpn_connections.py -h

---

### show_vpn_connection.py — 查询 VPN 连接详情

作用：查询 VPN 连接详情，包括 ID、名称、状态、VPN网关ID、VPN网关IP、连接模式、对端网关ID、隧道本端地址、隧道对端地址、NQA开关、Hub开关、创建时间、更新时间、企业项目ID。
用法详见：python scripts/vpn/show_vpn_connection.py -h

---

### show_vpn_connection_log.py — 查询 VPN 连接日志

作用：查询 VPN 连接日志，包括 时间、原始消息。
用法详见：python scripts/vpn/show_vpn_connection_log.py -h

### list_connection_monitors.py — 查询连接监控列表

作用：查询 VPN 连接监控列表，包括 ID、状态、VPN连接ID、类型、源IP、目的IP。
用法详见：python scripts/vpn/list_connection_monitors.py -h

---

### show_connection_monitor.py — 查询连接监控详情

作用：查询 VPN 连接监控详情，包括 ID、状态、VPN连接ID、类型、源IP、目的IP、协议类型。
用法详见：python scripts/vpn/show_connection_monitor.py -h

### list_vpn_gateway_jobs.py — 查询 VPN 网关任务

作用：查询 VPN 网关任务列表，包括 ID、资源ID、任务类型、状态、创建时间。
用法详见：python scripts/vpn/list_vpn_gateway_jobs.py -h

---

### list_p2c_vpn_gateway_jobs.py — 查询 P2C VPN 网关任务

作用：查询 P2C VPN 网关任务列表，包括 ID、资源ID、任务类型、状态、创建时间。
用法详见：python scripts/vpn/list_p2c_vpn_gateway_jobs.py -h

### list_p2c_vgws.py — 查询 P2C VPN 网关列表

作用：查询 P2C VPN 网关列表，包括 ID、名称、状态、VPC ID、规格、最大连接数、当前连接数、企业项目ID。
用法详见：python scripts/vpn/list_p2c_vgws.py -h

---

### show_p2c_vgw.py — 查询 P2C VPN 网关详情

作用：查询 P2C VPN 网关详情，包括 ID、名称、状态、VPC ID、连接子网、规格、最大连接数、当前连接数、企业项目ID、创建时间、更新时间。
用法详见：python scripts/vpn/show_p2c_vgw.py -h

---

### list_p2c_vgw_connections.py — 查询 P2C VPN 网关连接列表

作用：查询 P2C VPN 网关连接列表，包括 连接ID、客户端IP、客户端用户名、入包数、出包数。
用法详见：python scripts/vpn/list_p2c_vgw_connections.py -h

---

### show_vpn_connections_log_config.py — 查询 VPN 连接日志配置

作用：查询 VPN 连接日志配置，包括 日志组ID、日志流ID。
用法详见：python scripts/vpn/show_vpn_connections_log_config.py -h

### list_vpn_servers_by_project.py — 查询项目下 VPN 服务端列表

作用：查询项目下 VPN 服务端列表，包括 ID、P2C VPN网关ID、客户端认证类型、隧道协议、状态。
用法详见：python scripts/vpn/list_vpn_servers_by_project.py -h

---

### list_vpn_servers_by_vgw.py — 查询 VPN 网关下服务端列表

作用：查询 VPN 网关下 VPN 服务端列表，包括 ID、P2C VPN网关ID、客户端认证类型、隧道协议、状态。
用法详见：python scripts/vpn/list_vpn_servers_by_vgw.py -h

---

### show_client_ca.py — 查询客户端 CA 证书

作用：查询客户端 CA 证书详情，包括 ID、名称、颁发者、主题、序列号、过期时间、签名算法、创建时间、更新时间。
用法详见：python scripts/vpn/show_client_ca.py -h

### list_vpn_access_policies.py — 查询 VPN 访问策略列表

作用：查询 VPN 访问策略列表，包括 ID、名称、类型、用户组ID、用户组名称、描述。
用法详见：python scripts/vpn/list_vpn_access_policies.py -h

---

### show_vpn_access_policy.py — 查询 VPN 访问策略详情

作用：查询 VPN 访问策略详情，包括 ID、名称、类型、用户组ID、用户组名称、描述、创建时间、更新时间。
用法详见：python scripts/vpn/show_vpn_access_policy.py -h

### list_vpn_user_groups.py — 查询 VPN 用户组列表

作用：查询 VPN 用户组列表，包括 ID、名称、描述、类型、用户数。
用法详见：python scripts/vpn/list_vpn_user_groups.py -h

---

### show_vpn_user_group.py — 查询 VPN 用户组详情

作用：查询 VPN 用户组详情，包括 ID、名称、描述、类型、用户数、创建时间、更新时间。
用法详见：python scripts/vpn/show_vpn_user_group.py -h

### list_vpn_users.py — 查询 VPN 用户列表

作用：查询 VPN 用户列表，包括 ID、名称、描述、用户组ID、用户组名称。
用法详见：python scripts/vpn/list_vpn_users.py -h

---

### show_vpn_user.py — 查询 VPN 用户详情

作用：查询 VPN 用户详情，包括 ID、名称、描述、用户组ID、用户组名称、创建时间、更新时间。
用法详见：python scripts/vpn/show_vpn_user.py -h

---

### list_vpn_users_in_group.py — 查询用户组内用户列表

作用：查询 VPN 用户组内用户列表，包括 ID、名称、描述。
用法详见：python scripts/vpn/list_vpn_users_in_group.py -h

### show_quotas_info.py — 查询配额信息

作用：查询 VPN 配额信息，包括 类型、已使用、配额、单位。
用法详见：python scripts/vpn/show_quotas_info.py -h

---

### list_project_tags.py — 查询项目标签

作用：查询 VPN 项目标签，包括 键、values。
用法详见：python scripts/vpn/list_project_tags.py -h

---

### list_resources_by_tags.py — 按标签查询资源实例列表

作用：按标签查询 VPN 资源实例列表，包括 resource_id、resource_name、tags。
用法详见：python scripts/vpn/list_resources_by_tags.py -h

---

### show_resource_tags.py — 查询资源标签

作用：查询 VPN 资源标签，包括 键、值。
用法详见：python scripts/vpn/show_resource_tags.py -h

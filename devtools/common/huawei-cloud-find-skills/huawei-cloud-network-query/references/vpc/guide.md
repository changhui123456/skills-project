# VPC Python 脚本使用指南

---

## v3 列表查询

### list_vpcs.py — 查询 VPC 列表

作用：查询 VPC 列表，包括 名称、ID、CIDR、状态、描述。
用法详见：python scripts/vpc/list_vpcs.py -h

---

### list_virsubnets.py — 查询子网列表

作用：查询子网列表，包括 名称、ID、VPC ID、状态、范围、可用区ID、描述。
用法详见：python scripts/vpc/list_virsubnets.py -h

---

### list_security_groups.py — 查询安全组列表

作用：查询安全组列表，包括 名称、ID、描述。
用法详见：python scripts/vpc/list_security_groups.py -h

---

### list_security_group_rules.py — 查询安全组规则列表

作用：查询安全组规则列表，包括 ID、方向、协议、动作、远端IP前缀、远端安全组ID、安全组ID、优先级。
用法详见：python scripts/vpc/list_security_group_rules.py -h

---

### list_ports.py — 查询端口列表

作用：查询端口列表，包括 ID、名称、设备ID、设备归属、MAC地址、状态、管理状态、VPC ID、子网ID。
用法详见：python scripts/vpc/list_ports.py -h

---

### list_firewall.py — 查询防火墙列表

作用：查询防火墙列表，包括 ID、名称、状态、管理状态、描述、企业项目ID。
用法详见：python scripts/vpc/list_firewall.py -h

---

### list_address_group.py — 查询地址组列表

作用：查询地址组列表，包括 ID、名称、IP版本、最大容量、描述。
用法详见：python scripts/vpc/list_address_group.py -h

---

### list_sub_network_interfaces.py — 查询子网络接口列表

作用：查询子网络接口列表，包括 ID、子网ID、私网IP地址、MAC地址、VPC ID、父节点ID。
用法详见：python scripts/vpc/list_sub_network_interfaces.py -h

---

### list_traffic_mirror_filters.py — 查询流量镜像过滤器列表

作用：查询流量镜像过滤器列表，包括 ID、名称、描述、创建时间、更新时间。
用法详见：python scripts/vpc/list_traffic_mirror_filters.py -h

---

### list_traffic_mirror_filter_rules.py — 查询流量镜像过滤规则列表

作用：查询流量镜像过滤规则列表，包括 ID、流量镜像过滤器ID、方向、协议、源CIDR、目的CIDR、动作、优先级。
用法详见：python scripts/vpc/list_traffic_mirror_filter_rules.py -h

---

### list_traffic_mirror_sessions.py — 查询流量镜像会话列表

作用：查询流量镜像会话列表，包括 ID、名称、流量镜像过滤器ID、流量镜像目标ID、虚拟网络ID、优先级、是否启用。
用法详见：python scripts/vpc/list_traffic_mirror_sessions.py -h

---

### list_virsubnet_cidr_reservations.py — 查询子网 CIDR 保留列表

作用：查询子网CIDR保留列表，包括 ID、子网ID、CIDR、IP版本、名称、描述。
用法详见：python scripts/vpc/list_virsubnet_cidr_reservations.py -h

### list_address_groups_dependency.py — 查询地址组依赖

作用：查询地址组依赖，包括 ID、名称、IP版本、最大容量、描述。
用法详见：python scripts/vpc/list_address_groups_dependency.py -h

### show_vpc.py — 查询 VPC 详情

作用：查询VPC详情，包括 ID、名称、CIDR、状态、描述、企业项目ID、创建时间、更新时间。
用法详见：python scripts/vpc/show_vpc.py -h

---

### show_virsubnet.py — 查询子网详情

作用：查询子网详情，包括 ID、名称、VPC ID、状态、范围、可用区ID、描述、创建时间、更新时间。
用法详见：python scripts/vpc/show_virsubnet.py -h

---

### show_security_group.py — 查询安全组详情

作用：查询安全组详情，包括 ID、名称、描述、企业项目ID、创建时间、更新时间。
用法详见：python scripts/vpc/show_security_group.py -h

---

### show_security_group_rule.py — 查询安全组规则详情

作用：查询安全组规则详情，包括 ID、方向、协议、动作、远端IP前缀、远端安全组ID、安全组ID、优先级、IP协议类型、端口范围下限、端口范围上限。
用法详见：python scripts/vpc/show_security_group_rule.py -h

---

### show_port.py — 查询端口详情

作用：查询端口详情，包括 ID、名称、设备ID、设备归属、MAC地址、状态、管理状态、VPC ID、子网ID。
用法详见：python scripts/vpc/show_port.py -h

---

### show_firewall.py — 查询防火墙详情

作用：查询防火墙详情，包括 ID、名称、状态、管理状态、描述、企业项目ID、创建时间、更新时间。
用法详见：python scripts/vpc/show_firewall.py -h

---

### show_address_group.py — 查询地址组详情

作用：查询地址组详情，包括 ID、名称、IP版本、最大容量、描述、创建时间、更新时间。
用法详见：python scripts/vpc/show_address_group.py -h

---

### show_sub_network_interface.py — 查询子网络接口详情

作用：查询子网络接口详情，包括 ID、子网ID、私网IP地址、MAC地址、VPC ID、父节点ID、描述。
用法详见：python scripts/vpc/show_sub_network_interface.py -h

---

### show_virsubnet_cidr_reservation.py — 查询子网 CIDR 保留详情

作用：查询子网CIDR保留详情，包括 ID、子网ID、CIDR、IP版本、名称、描述。
用法详见：python scripts/vpc/show_virsubnet_cidr_reservation.py -h

---

### show_traffic_mirror_filter.py — 查询流量镜像过滤器详情

作用：查询流量镜像过滤器详情，包括 ID、名称、描述、创建时间、更新时间。
用法详见：python scripts/vpc/show_traffic_mirror_filter.py -h

---

### show_traffic_mirror_filter_rule.py — 查询流量镜像过滤规则详情

作用：查询流量镜像过滤规则详情，包括 ID、流量镜像过滤器ID、方向、协议、源CIDR、目的CIDR、动作、优先级。
用法详见：python scripts/vpc/show_traffic_mirror_filter_rule.py -h

---

### show_traffic_mirror_session.py — 查询流量镜像会话详情

作用：查询流量镜像会话详情，包括 ID、名称、流量镜像过滤器ID、流量镜像目标ID、虚拟网络ID、优先级、是否启用、描述。
用法详见：python scripts/vpc/show_traffic_mirror_session.py -h

---

### show_quota.py — 查询配额

作用：查询配额，包括 键、值。
用法详见：python scripts/vpc/show_quota.py -h

---

### show_sub_network_interfaces_quantity.py — 查询子网络接口数量

作用：查询子网络接口数量。
用法详见：python scripts/vpc/show_sub_network_interfaces_quantity.py -h

### list_subnets.py — 查询子网列表（v2）

作用：查询子网列表（v2），包括 名称、ID、CIDR、网关IP、VPC ID、状态、可用区。
用法详见：python scripts/vpc/list_subnets.py -h

---

### list_flow_logs.py — 查询 VPC 流日志列表

作用：查询VPC流日志列表，包括 ID、名称、资源类型、资源ID、流量类型、日志组ID、日志主题ID、状态。
用法详见：python scripts/vpc/list_flow_logs.py -h

---

### list_route_tables.py — 查询路由表列表

作用：查询路由表列表，包括 ID、VPC ID、名称。
用法详见：python scripts/vpc/list_route_tables.py -h

---

### list_vpc_peerings.py — 查询 VPC 对等连接列表

作用：查询VPC对等连接列表，包括 ID、名称、状态、请求方VPC ID、请求方租户ID、接受方VPC ID、接受方租户ID。
用法详见：python scripts/vpc/list_vpc_peerings.py -h

---

### list_vpc_routes.py — 查询 VPC 路由列表

作用：查询VPC路由列表，包括 ID、类型、目的地址、VPC ID、下一跳。
用法详见：python scripts/vpc/list_vpc_routes.py -h

---

### list_privateips.py — 查询私有 IP 列表

作用：查询私有IP列表，包括 ID、子网ID、IP地址、状态、设备归属。
用法详见：python scripts/vpc/list_privateips.py -h

### show_subnet.py — 查询子网详情（v2）

作用：查询子网详情（v2），包括 ID、名称、CIDR、网关IP、VPC ID、状态、可用区、DHCP开关、主DNS、备DNS、描述。
用法详见：python scripts/vpc/show_subnet.py -h

---

### show_flow_log.py — 查询 VPC 流日志详情

作用：查询VPC流日志详情，包括 ID、名称、资源类型、资源ID、流量类型、日志组ID、日志主题ID、状态、描述。
用法详见：python scripts/vpc/show_flow_log.py -h

---

### show_route_table.py — 查询路由表详情

作用：查询路由表详情，包括 ID、名称、VPC ID、描述。
用法详见：python scripts/vpc/show_route_table.py -h

---

### show_vpc_peering.py — 查询 VPC 对等连接详情

作用：查询VPC对等连接详情，包括 ID、名称、状态。
用法详见：python scripts/vpc/show_vpc_peering.py -h

---

### show_vpc_route.py — 查询 VPC 路由详情

作用：查询VPC路由详情，包括 ID、类型、目的地址、VPC ID、下一跳。
用法详见：python scripts/vpc/show_vpc_route.py -h

---

### show_privateip.py — 查询私有 IP 详情

作用：查询私有IP详情，包括 ID、子网ID、IP地址、状态、设备归属。
用法详见：python scripts/vpc/show_privateip.py -h

---

### show_network_ip_availabilities.py — 查询网络 IP 可用数量

作用：查询网络IP可用数量。
用法详见：python scripts/vpc/show_network_ip_availabilities.py -h

---

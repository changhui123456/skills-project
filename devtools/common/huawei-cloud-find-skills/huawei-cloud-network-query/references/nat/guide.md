# NAT 网关 Python 脚本使用指南

---

## 公网 NAT 网关

### list_nat_gateways.py — 查询 NAT 网关列表

作用：查询 NAT 网关列表，包括 ID、名称、状态、spec、router_id、internal_network_id、描述、企业项目ID。
用法详见：python scripts/nat/list_nat_gateways.py -h

---

### list_nat_gateway_dnat_rules.py — 查询 DNAT 规则列表

作用：查询 NAT 网关 DNAT 规则列表，包括 ID、状态、协议、floating_ip_address、internal_service_port、private_ip、external_service_port、nat_gateway_id、描述。
用法详见：python scripts/nat/list_nat_gateway_dnat_rules.py -h

---

### list_nat_gateway_snat_rules.py — 查询 SNAT 规则列表

作用：查询 NAT 网关 SNAT 规则列表，包括 ID、状态、floating_ip_address、CIDR、source_type、nat_gateway_id、网络ID、描述。
用法详见：python scripts/nat/list_nat_gateway_snat_rules.py -h

---

### list_nat_gateway_specs.py — 查询公网 NAT 网关规格列表

作用：查询 NAT 网关规格列表，包括 spec。
用法详见：python scripts/nat/list_nat_gateway_specs.py -h

---

### show_nat_gateway.py — 查询 NAT 网关详情

作用：查询 NAT 网关详情，包括 ID、名称、描述、spec、状态、管理状态、router_id、internal_network_id、企业项目ID、创建时间、dnat_rules_limit、snat_rule_public_ip_limit。
用法详见：python scripts/nat/show_nat_gateway.py -h

---

### show_nat_gateway_dnat_rule.py — 查询 DNAT 规则详情

作用：查询 NAT 网关 DNAT 规则详情，包括 ID、nat_gateway_id、协议、floating_ip_address、floating_ip_id、external_service_port、internal_service_port、private_ip、端口ID、状态、管理状态、描述、创建时间、global_eip_id、global_eip_address。
用法详见：python scripts/nat/show_nat_gateway_dnat_rule.py -h

---

### show_nat_gateway_snat_rule.py — 查询 SNAT 规则详情

作用：查询 NAT 网关 SNAT 规则详情，包括 ID、nat_gateway_id、CIDR、source_type、floating_ip_id、floating_ip_address、网络ID、状态、管理状态、描述、创建时间、global_eip_id、global_eip_address。
用法详见：python scripts/nat/show_nat_gateway_snat_rule.py -h

### list_private_nats.py — 查询私网 NAT 网关列表

作用：查询私网 NAT 网关列表，包括 ID、名称、状态、spec、描述、企业项目ID。
用法详见：python scripts/nat/list_private_nats.py -h

---

### list_private_dnats.py — 查询私网 DNAT 规则列表

作用：查询私网 NAT 网关 DNAT 规则列表，包括 ID、gateway_id、协议、私网IP地址、internal_service_port、transit_service_port、transit_ip_id、状态、描述。
用法详见：python scripts/nat/list_private_dnats.py -h

---

### list_private_snats.py — 查询私网 SNAT 规则列表

作用：查询私网 NAT 网关 SNAT 规则列表，包括 ID、gateway_id、CIDR、子网ID、描述、状态。
用法详见：python scripts/nat/list_private_snats.py -h

---

### list_specs.py — 查询私网 NAT 网关规格列表

作用：查询私网 NAT 网关规格列表，包括 名称、code、rule_max、sess_max、bps_max、pps_max、qps_max。
用法详见：python scripts/nat/list_specs.py -h

---

### show_private_nat.py — 查询私网 NAT 网关详情

作用：查询私网 NAT 网关详情，包括 ID、名称、描述、spec、状态、企业项目ID、创建时间、更新时间、rule_max。
用法详见：python scripts/nat/show_private_nat.py -h

---

### show_private_dnat.py — 查询私网 DNAT 规则详情

作用：查询私网 NAT 网关 DNAT 规则详情，包括 ID、gateway_id、transit_ip_id、network_interface_id、类型、协议、私网IP地址、internal_service_port、transit_service_port、状态、描述、企业项目ID、创建时间、更新时间。
用法详见：python scripts/nat/show_private_dnat.py -h

---

### show_private_snat.py — 查询私网 SNAT 规则详情

作用：查询私网 NAT 网关 SNAT 规则详情，包括 ID、gateway_id、CIDR、子网ID、描述、状态、企业项目ID、创建时间、更新时间。
用法详见：python scripts/nat/show_private_snat.py -h

### list_transit_ip.py — 查询中转 IP 列表

作用：查询中转 IP 列表，包括 ID、IP地址、network_interface_id、gateway_id、子网ID、状态、企业项目ID。
用法详见：python scripts/nat/list_transit_ip.py -h

---

### show_transit_ip.py — 查询中转 IP 详情

作用：查询中转 IP 详情，包括 ID、IP地址、network_interface_id、gateway_id、子网ID、状态、企业项目ID、创建时间、更新时间。
用法详见：python scripts/nat/show_transit_ip.py -h

### list_transit_subnet.py — 查询中转子网列表

作用：查询中转子网列表，包括 ID、名称、VPC ID、子网ID、CIDR、类型、状态、ip_count、描述。
用法详见：python scripts/nat/list_transit_subnet.py -h

---

### show_transit_subnet.py — 查询中转子网详情

作用：查询中转子网详情，包括 ID、名称、描述、VPC ID、子网ID、CIDR、类型、状态、ip_count、创建时间、更新时间。
用法详见：python scripts/nat/show_transit_subnet.py -h

---

### list_nat_gateway_tag.py — 查询公网NAT网关项目标签

作用：查询公网NAT网关项目标签，包括 键、values。
用法详见：python scripts/nat/list_nat_gateway_tag.py -h

---

### list_nat_gateway_by_tag.py — 按标签过滤查询公网NAT网关实例

作用：按标签过滤查询公网NAT网关实例，包括 resource_id、resource_name、tags。
用法详见：python scripts/nat/list_nat_gateway_by_tag.py -h

---

### show_nat_gateway_tag.py — 查询指定公网NAT网关的标签

作用：查询指定公网NAT网关的标签，包括 键、值。
用法详见：python scripts/nat/show_nat_gateway_tag.py -h

---

### list_private_nat_tags.py — 查询私网NAT网关项目标签

作用：查询私网NAT网关项目标签，包括 键、values。
用法详见：python scripts/nat/list_private_nat_tags.py -h

---

### list_private_nats_by_tags.py — 按标签过滤查询私网NAT网关实例

作用：按标签过滤查询私网NAT网关实例，包括 resource_id、resource_name、tags。
用法详见：python scripts/nat/list_private_nats_by_tags.py -h

---

### show_private_nat_tags.py — 查询指定私网NAT网关的标签

作用：查询指定私网NAT网关的标签，包括 键、值。
用法详见：python scripts/nat/show_private_nat_tags.py -h

---

### list_transit_ip_tags.py — 查询中转IP项目标签

作用：查询中转IP项目标签，包括 键、values。
用法详见：python scripts/nat/list_transit_ip_tags.py -h

---

### list_transit_ips_by_tags.py — 按标签过滤查询中转IP实例

作用：按标签过滤查询中转IP实例，包括 resource_id、resource_name、tags。
用法详见：python scripts/nat/list_transit_ips_by_tags.py -h

---

### show_transit_ip_tags.py — 查询指定中转IP的标签

作用：查询指定中转IP的标签，包括 键、值。
用法详见：python scripts/nat/show_transit_ip_tags.py -h

---

### list_transit_subnet_tags.py — 查询中转子网项目标签

作用：查询中转子网项目标签，包括 键、values。
用法详见：python scripts/nat/list_transit_subnet_tags.py -h

---

### list_transit_subnets_by_tags.py — 按标签过滤查询中转子网实例

作用：按标签过滤查询中转子网实例，包括 resource_id、resource_name、tags。
用法详见：python scripts/nat/list_transit_subnets_by_tags.py -h

---

### show_transit_subnet_tags.py — 查询指定中转子网的标签

作用：查询指定中转子网的标签，包括 键、值。
用法详见：python scripts/nat/show_transit_subnet_tags.py -h

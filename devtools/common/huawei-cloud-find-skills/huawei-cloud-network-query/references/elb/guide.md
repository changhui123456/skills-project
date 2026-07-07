# ELB Python 脚本使用指南

---

## 列表查询接口

### list_load_balancers.py — 查询负载均衡器列表

作用：查询 ELB 负载均衡器列表，包括 名称、ID、vip_address、provisioning_status、operating_status、VPC ID。
用法详见：python scripts/elb/list_load_balancers.py -h

---

### list_listeners.py — 查询监听器列表

作用：查询 ELB 监听器列表，包括 名称、ID、协议、protocol_port、loadbalancer_id、default_pool_id、管理状态。
用法详见：python scripts/elb/list_listeners.py -h

---

### list_pools.py — 查询后端服务器组列表

作用：查询 ELB 后端服务器组列表，包括 名称、ID、协议、lb_algorithm、healthmonitor_id、VPC ID。
用法详见：python scripts/elb/list_pools.py -h

---

### list_members.py — 查询后端服务器列表

作用：查询 ELB 后端服务器列表，包括 名称、ID、address、protocol_port、weight、operating_status、管理状态。
用法详见：python scripts/elb/list_members.py -h

---

### list_health_monitors.py — 查询健康检查列表

作用：查询 ELB 健康检查列表，包括 名称、ID、类型、delay、timeout、max_retries、管理状态。
用法详见：python scripts/elb/list_health_monitors.py -h

---

### list_certificates.py — 查询证书列表

作用：查询 ELB 证书列表，包括 名称、ID、类型、domain、过期时间、管理状态。
用法详见：python scripts/elb/list_certificates.py -h

---

### list_l7_policies.py — 查询七层策略列表

作用：查询 ELB 七层策略列表，包括 名称、ID、动作、position、优先级、listener_id、provisioning_status。
用法详见：python scripts/elb/list_l7_policies.py -h

---

### list_l7_rules.py — 查询七层规则列表

作用：查询 ELB 七层规则列表，包括 ID、类型、compare_type、值、键、管理状态、provisioning_status。
用法详见：python scripts/elb/list_l7_rules.py -h

---

### list_flavors.py — 查询规格列表

作用：查询 ELB 规格列表，包括 ID、名称、类型、shared、flavor_sold_out。
用法详见：python scripts/elb/list_flavors.py -h

---

### list_logtanks.py — 查询云日志列表

作用：查询 ELB 云日志列表，包括 ID、loadbalancer_id、日志组ID、日志主题ID。
用法详见：python scripts/elb/list_logtanks.py -h

---

### list_security_policies.py — 查询安全策略列表

作用：查询 ELB 安全策略列表，包括 ID、名称、描述、protocols、ciphers。
用法详见：python scripts/elb/list_security_policies.py -h

---

### list_ip_groups.py — 查询IP地址组列表

作用：查询 ELB IP 地址组列表，包括 ID、名称、描述、项目ID。
用法详见：python scripts/elb/list_ip_groups.py -h

---

### list_jobs.py — 查询任务列表

作用：查询 ELB 任务列表，包括 任务ID、任务类型、状态、资源ID、begin_time、结束时间。
用法详见：python scripts/elb/list_jobs.py -h

---

### list_master_slave_pools.py — 查询主备后端服务器组列表

作用：查询 ELB 主备后端服务器组列表，包括 ID、名称、协议、lb_algorithm、VPC ID、类型。
用法详见：python scripts/elb/list_master_slave_pools.py -h

---

### list_all_l7_rules.py — 查询全部七层规则列表

作用：查询 ELB 全部七层规则列表，包括 ID、类型、compare_type、值、键、管理状态、provisioning_status。
用法详见：python scripts/elb/list_all_l7_rules.py -h

---

### list_all_members.py — 查询全部后端服务器列表

作用：查询 ELB 全部后端服务器列表，包括 ID、名称、address、protocol_port、weight、池ID、operating_status。
用法详见：python scripts/elb/list_all_members.py -h

---

### list_availability_zones.py — 查询可用区列表

作用：查询 ELB 可用区列表，包括 code、state、协议、公共边界组、类别。
用法详见：python scripts/elb/list_availability_zones.py -h

---

### list_system_security_policies.py — 查询系统安全策略列表

作用：查询 ELB 系统安全策略列表，包括 名称、protocols、ciphers、项目ID。
用法详见：python scripts/elb/list_system_security_policies.py -h

---

### list_loadbalancer_tags.py — 查询负载均衡器标签

作用：查询 ELB 负载均衡器标签列表，包括 键、values。
用法详见：python scripts/elb/list_loadbalancer_tags.py -h

---

### list_listener_tags.py — 查询监听器标签

作用：查询 ELB 监听器标签列表，包括 键、values。
用法详见：python scripts/elb/list_listener_tags.py -h

---

### list_api_versions.py — 查询API版本列表

作用：查询 ELB API 版本列表，包括 ID、状态。
用法详见：python scripts/elb/list_api_versions.py -h

---

### list_domain_i_ps.py — 查询域名IP列表

作用：查询 ELB 域名 IP 列表，包括 ID、IP地址、类型、域名称、enable。
用法详见：python scripts/elb/list_domain_i_ps.py -h

---

### list_feature_configs.py — 查询特性配置列表

作用：查询 ELB 特性配置列表，包括 ID、feature、类型、值、开关、描述。
用法详见：python scripts/elb/list_feature_configs.py -h

---

### list_quota_details.py — 查询配额详情列表

作用：查询 ELB 配额详情列表，包括 quota_key、quota_limit、已使用、单位。
用法详见：python scripts/elb/list_quota_details.py -h

---

### list_recycle_bin_load_balancers.py — 查询回收站负载均衡器列表

作用：查询 ELB 回收站负载均衡器列表，包括 ID、名称、vip_address、provisioning_status、operating_status、VPC ID。
用法详见：python scripts/elb/list_recycle_bin_load_balancers.py -h

---

### list_loadbalancer_feature.py — 查询负载均衡器特性列表

作用：查询 ELB 负载均衡器特性列表，包括 feature、类型、值。
用法详见：python scripts/elb/list_loadbalancer_feature.py -h

### show_load_balancer.py — 查询负载均衡器详情

作用：查询 ELB 负载均衡器详情，包括 ID、名称、描述、vip_address、provisioning_status、operating_status、VPC ID、管理状态、guaranteed、创建时间、更新时间。
用法详见：python scripts/elb/show_load_balancer.py -h

---

### show_listener.py — 查询监听器详情

作用：查询 ELB 监听器详情，包括 ID、名称、协议、protocol_port、loadbalancer_id、default_pool_id、管理状态、connection_limit、创建时间、更新时间。
用法详见：python scripts/elb/show_listener.py -h

---

### show_pool.py — 查询后端服务器组详情

作用：查询 ELB 后端服务器组详情，包括 ID、名称、协议、lb_algorithm、healthmonitor_id、VPC ID、管理状态、描述、类型、创建时间、更新时间。
用法详见：python scripts/elb/show_pool.py -h

---

### show_member.py — 查询后端服务器详情

作用：查询 ELB 后端服务器详情，包括 ID、名称、address、protocol_port、weight、管理状态、operating_status、subnet_cidr_id、IP版本。
用法详见：python scripts/elb/show_member.py -h

---

### show_health_monitor.py — 查询健康检查详情

作用：查询 ELB 健康检查详情，包括 ID、名称、类型、delay、timeout、max_retries、max_retries_down、管理状态、monitor_port、域名称、url_path、http_method、expected_codes。
用法详见：python scripts/elb/show_health_monitor.py -h

---

### show_certificate.py — 查询证书详情

作用：查询 ELB 证书详情，包括 ID、名称、类型、domain、描述、管理状态、过期时间、common_name、fingerprint、source、创建时间、更新时间。
用法详见：python scripts/elb/show_certificate.py -h

---

### show_l7_policy.py — 查询七层策略详情

作用：查询 ELB 转发策略详情，包括 ID、名称、动作、position、优先级、listener_id、redirect_pool_id、redirect_listener_id、redirect_url、provisioning_status、管理状态、描述。
用法详见：python scripts/elb/show_l7_policy.py -h

---

### show_l7_rule.py — 查询七层规则详情

作用：查询 ELB 转发规则详情，包括 ID、类型、compare_type、值、键、管理状态、provisioning_status、invert。
用法详见：python scripts/elb/show_l7_rule.py -h

---

### show_flavor.py — 查询规格详情

作用：查询 ELB Flavor 详情，包括 ID、名称、类型、shared、flavor_sold_out、公共边界组、类别。
用法详见：python scripts/elb/show_flavor.py -h

---

### show_logtank.py — 查询云日志详情

作用：查询 ELB 云日志详情，包括 ID、loadbalancer_id、日志组ID、日志主题ID、项目ID。
用法详见：python scripts/elb/show_logtank.py -h

---

### show_security_policy.py — 查询安全策略详情

作用：查询 ELB 安全策略详情，包括 ID、名称、描述、protocols、ciphers、企业项目ID、创建时间、更新时间。
用法详见：python scripts/elb/show_security_policy.py -h

---

### show_job.py — 查询任务详情

作用：查询 ELB 任务详情，包括 任务ID、任务类型、状态、资源ID、错误码、错误消息、begin_time、结束时间。
用法详见：python scripts/elb/show_job.py -h

---

### show_master_slave_pool.py — 查询主备后端服务器组详情

作用：查询 ELB 主备后端服务器组详情，包括 ID、名称、协议、lb_algorithm、VPC ID、类型、描述、IP版本、企业项目ID。
用法详见：python scripts/elb/show_master_slave_pool.py -h

---

### show_load_balancer_status.py — 查询负载均衡器状态树

作用：查询 ELB 负载均衡器状态树。
用法详见：python scripts/elb/show_load_balancer_status.py -h

---

### show_load_balancer_topology.py — 查询负载均衡器拓扑

作用：查询 ELB 负载均衡器拓扑。
用法详见：python scripts/elb/show_load_balancer_topology.py -h

---

### show_load_balancer_ports.py — 查询负载均衡器端口列表

作用：查询 ELB 负载均衡器端口列表，包括 端口ID、IP地址、ipv6_address、类型、子网ID。
用法详见：python scripts/elb/show_load_balancer_ports.py -h

---

### show_member_health_check_job.py — 查询成员健康检查任务

作用：查询 ELB 成员健康检查任务详情，包括 任务ID、状态、listener_id、member_id、check_item_total_num、check_item_finished_num、创建时间、更新时间。
用法详见：python scripts/elb/show_member_health_check_job.py -h

---

### show_ip_group.py — 查询IP地址组详情

作用：查询 ELB IP 地址组详情，包括 ID、名称、描述、项目ID、企业项目ID、创建时间、更新时间。
用法详见：python scripts/elb/show_ip_group.py -h

---

### show_ip_group_related_listeners.py — 查询IP地址组关联监听器

作用：查询 ELB IP 地址组关联的监听器列表，包括 ID。
用法详见：python scripts/elb/show_ip_group_related_listeners.py -h

---

### show_listener_tags.py — 查询监听器标签

作用：查询 ELB 监听器标签列表，包括 键、值。
用法详见：python scripts/elb/show_listener_tags.py -h

---

### show_loadbalancer_tags.py — 查询负载均衡器标签

作用：查询 ELB 负载均衡器标签列表，包括 键、值。
用法详见：python scripts/elb/show_loadbalancer_tags.py -h

---

### show_quota.py — 查询配额

作用：查询 ELB 配额，包括 项目ID、loadbalancer、listener、pool、member、healthmonitor、l7policy、certificate、ipgroup、security_policy。
用法详见：python scripts/elb/show_quota.py -h

---

### show_recycle_bin.py — 查询回收站配置

作用：查询 ELB 回收站配置，包括 项目ID、enable、policy。
用法详见：python scripts/elb/show_recycle_bin.py -h

---

### show_certificate_private_key_echo.py — 查询证书私钥回显开关

作用：查询 ELB 证书私钥回显开关。
用法详见：python scripts/elb/show_certificate_private_key_echo.py -h

### count_preoccupy_ip_num.py — 计算预占IP数量

作用：计算LB预占IP数量。
用法详见：python scripts/elb/count_preoccupy_ip_num.py -h

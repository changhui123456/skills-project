# DNS Python 脚本使用指南

---

## 公网域名

### list_public_zones.py — 查询公网域名列表

作用：查询公网域名列表，包括 ID、名称、状态、域名类型、TTL、记录集数量、企业项目ID、创建时间。支持按名称、ID、状态、标签、企业项目等条件过滤，支持模糊/精确搜索和排序。
用法详见：python scripts/dns/list_public_zones.py -h

---

### show_public_zone.py — 查询公网域名详情

作用：查询公网域名详情，包括 ID、名称、描述、邮箱、域名类型、TTL、serial、状态、记录集数量、pool_id、项目ID、企业项目ID、masters 等。
用法详见：python scripts/dns/show_public_zone.py -h

---

### show_public_zone_name_server.py — 查询公网域名的名称服务器

作用：查询公网域名的名称服务器，包括 hostname、priority。
用法详见：python scripts/dns/show_public_zone_name_server.py -h

---

### list_public_zone_lines.py — 查询公网域名的线路列表

作用：查询公网域名的线路列表，包括 线路ID、名称、IP段、创建时间、更新时间。
用法详见：python scripts/dns/list_public_zone_lines.py -h

---

## 内网域名

### list_private_zones.py — 查询内网域名列表

作用：查询内网域名列表，包括 ID、名称、状态、域名类型、TTL、记录集数量、企业项目ID、创建时间。支持按名称、ID、状态、标签、企业项目、关联VPC等条件过滤，支持模糊/精确搜索和排序。
用法详见：python scripts/dns/list_private_zones.py -h

---

### show_private_zone.py — 查询内网域名详情

作用：查询内网域名详情，包括 ID、名称、描述、邮箱、域名类型、TTL、serial、状态、记录集数量、pool_id、项目ID、企业项目ID、proxy_pattern、masters、关联VPC路由信息等。
用法详见：python scripts/dns/show_private_zone.py -h

---

### show_private_zone_name_server.py — 查询内网域名的名称服务器

作用：查询内网域名的名称服务器，包括 hostname、priority、address。
用法详见：python scripts/dns/show_private_zone_name_server.py -h

---

## 记录集

### list_record_sets.py — 查询租户记录集列表

作用：查询租户记录集列表，包括 ID、名称、类型、状态、TTL、域名ID、域名名称。支持按域名类型、名称、ID、类型、状态、标签等条件过滤，支持模糊/精确搜索和排序。
用法详见：python scripts/dns/list_record_sets.py -h

---

### list_record_sets_by_zone.py — 查询域名下的记录集列表

作用：查询指定域名下的记录集列表，包括 ID、名称、类型、状态、TTL、记录值。支持按名称、ID、类型、状态、标签等条件过滤，支持模糊/精确搜索和排序。
用法详见：python scripts/dns/list_record_sets_by_zone.py -h

---

### list_record_sets_with_line.py — 查询租户记录集列表（支持线路）

作用：查询租户记录集列表（支持线路），包括 ID、名称、类型、状态、TTL、域名ID、域名名称、线路、权重。支持按域名类型、域名ID、线路ID、名称、类型、状态、标签、健康检查ID等条件过滤。
用法详见：python scripts/dns/list_record_sets_with_line.py -h

---

### show_record_set.py — 查询记录集详情

作用：查询记录集详情，包括 ID、名称、描述、域名ID、域名名称、类型、TTL、状态、default、项目ID、bundle、记录值等。
用法详见：python scripts/dns/show_record_set.py -h

---

### show_record_set_by_zone.py — 查询域名下的记录集详情

作用：查询指定域名下的记录集详情，包括 ID、名称、类型、状态、TTL、记录值。支持按线路ID、名称、类型、状态、标签等条件过滤。
用法详见：python scripts/dns/show_record_set_by_zone.py -h

---

### show_record_set_with_line.py — 查询记录集详情（支持线路）

作用：查询记录集详情（支持线路），包括 ID、名称、描述、域名ID、域名名称、类型、TTL、状态、default、项目ID、线路、权重、健康检查ID、bundle、记录值、alias_target 等。
用法详见：python scripts/dns/show_record_set_with_line.py -h

---

## 反向解析（PTR）

### list_ptr_records.py — 查询反向解析记录列表

作用：查询弹性公网IP的反向解析记录列表，包括 ID、IP地址、PTR域名、状态、TTL。支持按企业项目ID、标签、状态等条件过滤。
用法详见：python scripts/dns/list_ptr_records.py -h

---

### list_ptrs.py — 查询反向解析记录列表

作用：查询弹性公网IP的反向解析记录列表，包括 ID、IP地址、PTR域名、状态、TTL。支持按企业项目ID、标签、状态、资源类型等条件过滤。
用法详见：python scripts/dns/list_ptrs.py -h

---

### show_ptr.py — 查询反向解析记录详情

作用：查询弹性公网IP的反向解析记录详情，包括 ID、PTR域名、描述、TTL、状态、企业项目ID、公网IP信息（ID、地址、类型）。
用法详见：python scripts/dns/show_ptr.py -h

---

### show_ptr_record_set.py — 查询弹性公网IP的反向解析记录

作用：查询指定弹性公网IP的反向解析记录，包括 ID、PTR域名、描述、TTL、IP地址、状态、action、企业项目ID。
用法详见：python scripts/dns/show_ptr_record_set.py -h

---

## 线路管理

### list_line_groups.py — 查询线路分组列表

作用：查询线路分组列表，包括 线路分组ID、名称、状态、描述、创建时间、更新时间。支持按线路分组ID、名称等条件过滤。
用法详见：python scripts/dns/list_line_groups.py -h

---

### show_line_group.py — 查询线路分组详情

作用：查询线路分组详情，包括 线路分组ID、名称、状态、描述、包含的线路列表、创建时间、更新时间。
用法详见：python scripts/dns/show_line_group.py -h

---

### list_custom_line.py — 查询自定义线路列表

作用：查询自定义线路列表，包括 线路ID、名称、状态、创建时间、更新时间。支持按线路ID、名称、状态、IP地址等条件过滤。
用法详见：python scripts/dns/list_custom_line.py -h

---

### list_system_lines.py — 查询系统线路列表

作用：查询系统线路列表，包括 线路ID、名称、创建时间、更新时间。支持按语言标识过滤。
用法详见：python scripts/dns/list_system_lines.py -h

---

## 终端节点

### list_endpoints.py — 查询终端节点列表

作用：查询终端节点列表，包括 ID、名称、方向（inbound/outbound）、状态、创建时间、更新时间。支持按VPC ID、名称等条件过滤。
用法详见：python scripts/dns/list_endpoints.py -h

---

### show_endpoint.py — 查询终端节点详情

作用：查询终端节点详情，包括 ID、名称、方向、状态、创建时间、更新时间、IP地址列表。
用法详见：python scripts/dns/show_endpoint.py -h

---

### list_endpoint_vpcs.py — 查询终端节点VPC列表

作用：查询终端节点VPC列表，包括 VPC ID、VPC名称、区域。支持按VPC ID过滤。
用法详见：python scripts/dns/list_endpoint_vpcs.py -h

---

### list_endpoint_ipaddresses.py — 查询终端节点IP地址列表

作用：查询指定终端节点的IP地址列表，包括 ID、IP地址、状态、创建时间、更新时间。
用法详见：python scripts/dns/list_endpoint_ipaddresses.py -h

---

## 解析器转发规则

### list_resolver_rules.py — 查询解析器转发规则列表

作用：查询解析器转发规则列表，包括 ID、名称、域名、终端节点ID、状态、创建时间、更新时间。支持按域名、名称、终端节点ID、转发规则ID等条件过滤。
用法详见：python scripts/dns/list_resolver_rules.py -h

---

### show_resolver_rule.py — 查询解析器转发规则详情

作用：查询解析器转发规则详情，包括 ID、名称、域名、终端节点ID、状态、创建时间、更新时间、IP地址列表。
用法详见：python scripts/dns/show_resolver_rule.py -h

---

## 解析器访问日志

### list_resolver_query_log_configs.py — 查询解析器访问日志配置列表

作用：查询解析器访问日志配置列表，包括 ID、LTS日志组ID、LTS日志主题ID、关联VPC ID列表。支持按VPC ID过滤。
用法详见：python scripts/dns/list_resolver_query_log_configs.py -h

---

### show_resolver_query_log_config.py — 查询解析器访问日志配置详情

作用：查询解析器访问日志配置详情，包括 ID、LTS日志组ID、LTS日志主题ID、关联VPC ID列表。
用法详见：python scripts/dns/show_resolver_query_log_config.py -h

---

## 名称服务器

### list_name_servers.py — 查询名称服务器列表

作用：查询名称服务器列表，包括 域名类型、区域、名称服务器记录（hostname、priority、address）。支持按域名类型、区域过滤。
用法详见：python scripts/dns/list_name_servers.py -h

---

### show_zone_name_server.py — 查询公网域名的DNS服务器地址

作用：查询公网域名的DNS服务器地址，包括 域名名称、是否全华为云DNS、是否包含华为云DNS、实际DNS服务器列表、预期DNS服务器列表。
用法详见：python scripts/dns/show_zone_name_server.py -h

---

## 标签

### list_tags.py — 查询指定实例类型的所有标签集合

作用：查询指定实例类型的所有标签集合，包括 标签key、values列表。resource_type 支持：DNS-public_zone、DNS-private_zone、DNS-public_recordset、DNS-private_recordset、DNS-ptr_record。
用法详见：python scripts/dns/list_tags.py -h

---

### show_resource_tag.py — 查询指定实例的标签信息

作用：查询指定实例的标签信息，包括 标签key、value。resource_type 支持：DNS-public_zone、DNS-private_zone、DNS-public_recordset、DNS-private_recordset、DNS-ptr_record。
用法详见：python scripts/dns/show_resource_tag.py -h

---

## DNSSEC

### show_dnssec_config.py — 查询DNSSEC配置

作用：查询DNSSEC配置，包括 域名名称、key_tag、flag、摘要算法、摘要类型、摘要、签名、签名类型、KSK公钥、DS记录、状态、创建时间、更新时间。
用法详见：python scripts/dns/show_dnssec_config.py -h

---

## 配额与诊断

### show_domain_quota.py — 查询租户配额

作用：查询租户配额，包括 配额项、配额上限、已使用量、单位。
用法详见：python scripts/dns/show_domain_quota.py -h

---

### show_domain_detection.py — 查询公网域名的域名诊断

作用：查询公网域名的域名诊断，包括 域名名称、类型、状态。支持按记录集类型（MX/CNAME/TXT）和域名名称过滤。
用法详见：python scripts/dns/show_domain_detection.py -h

---

## 批量操作

### show_batch_operation_task.py — 查询批量操作任务

作用：查询批量操作任务，包括 任务ID、类型、状态、创建时间、成功数量、失败数量、失败条目列表。
用法详见：python scripts/dns/show_batch_operation_task.py -h

---

### show_batch_create_record_sets_task.py — 查询批量创建记录集任务

作用：查询批量创建记录集任务，包括 任务ID、状态、创建时间、更新时间、总数、成功数量、失败数量、失败条目列表。
用法详见：python scripts/dns/show_batch_create_record_sets_task.py -h

---

## 域名授权与找回

### show_authorize_txt_record.py — 查询公网子域名授权

作用：查询公网子域名授权，包括 ID、域名名称、状态、二级域名名称、创建时间、更新时间、TXT记录（host、value）。
用法详见：python scripts/dns/show_authorize_txt_record.py -h

---

### show_retrieval.py — 查询公网域名找回

作用：查询公网域名找回，包括 ID、域名名称、状态、创建时间、更新时间、TXT记录（host、value）。
用法详见：python scripts/dns/show_retrieval.py -h

---

### show_retrieval_verification.py — 查询公网域名找回结果

作用：查询公网域名找回结果，包括 任务ID、状态、更新时间。
用法详见：python scripts/dns/show_retrieval_verification.py -h

---

## 邮箱与网站域名

### show_email_record_set.py — 查询公网域名的邮箱域名记录集

作用：查询公网域名的邮箱域名记录集，包括 ID、名称、类型、状态、TTL、记录值。
用法详见：python scripts/dns/show_email_record_set.py -h

---

### show_website_record_set.py — 查询公网域名的网站域名记录集

作用：查询公网域名的网站域名记录集，包括 ID、名称、类型、状态、TTL、记录值。
用法详见：python scripts/dns/show_website_record_set.py -h

---

## DNS解析量统计

### list_instances.py — 批量查询DNS解析量统计资源

作用：批量查询DNS解析量统计相关的资源，包括 ID、名称、状态、区域、企业项目ID。支持按域名ID、域名名称、时间范围过滤。
用法详见：python scripts/dns/list_instances.py -h

---

## API版本

### list_api_versions.py — 查询API版本信息列表

作用：查询DNS API版本信息列表，包括 版本ID、状态。
用法详见：python scripts/dns/list_api_versions.py -h

---

### show_api_info.py — 查询指定版本号的API版本信息

作用：查询指定版本号的API版本信息，包括 版本ID、状态、version、min_version、updated、links。
用法详见：python scripts/dns/show_api_info.py -h

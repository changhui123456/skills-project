# 华为云弹性伸缩(AS)查询指南

## 伸缩组

### list_scaling_groups.py — 查询弹性伸缩组列表

作用：查询所有伸缩组，返回伸缩组ID、名称、状态、当前/期望/最小/最大实例数、VPC ID、创建时间等。
用法详见：python scripts/as/list_scaling_groups.py -h

### show_scaling_group.py — 查询弹性伸缩组详情

作用：查询单个伸缩组完整详情，包括网络、安全组、可用区、负载均衡监听器、标签等。
用法详见：python scripts/as/show_scaling_group.py -h

---

## 伸缩配置

### list_scaling_configs.py — 查询弹性伸缩配置列表

作用：查询所有伸缩配置，返回配置ID、名称、关联伸缩组ID、创建时间等。
用法详见：python scripts/as/list_scaling_configs.py -h

### show_scaling_config.py — 查询弹性伸缩配置详情

作用：查询单个伸缩配置完整详情，包括规格、镜像、磁盘、密钥、公网IP、安全组等。
用法详见：python scripts/as/show_scaling_config.py -h

---

## 伸缩组实例

### list_scaling_instances.py — 查询伸缩组实例列表

作用：查询指定伸缩组内的实例，返回实例ID、名称、生命周期状态、健康状态、保护状态等。
用法详见：python scripts/as/list_scaling_instances.py -h

---

## 伸缩策略(v1)

### list_scaling_policies.py — 查询伸缩策略列表(v1)

作用：查询指定伸缩组的策略列表(v1版)，返回策略ID、名称、状态、类型、告警ID等。
用法详见：python scripts/as/list_scaling_policies.py -h

### show_scaling_policy.py — 查询伸缩策略详情(v1)

作用：查询单个策略详情(v1版)，包括策略动作、定时策略等。
用法详见：python scripts/as/show_scaling_policy.py -h

---

## 伸缩策略(v2)

### list_scaling_v2_policies.py — 查询伸缩策略列表(v2)

作用：查询指定伸缩组的策略列表(v2版)，支持分段区间告警策略。
用法详见：python scripts/as/list_scaling_v2_policies.py -h

### show_scaling_v2_policy.py — 查询伸缩策略详情(v2)

作用：查询单个策略详情(v2版)，包括分段区间告警动作、元数据等。
用法详见：python scripts/as/show_scaling_v2_policy.py -h

### list_all_scaling_v2_policies.py — 查询全量伸缩策略列表(v2)

作用：查询所有伸缩组和带宽对应的策略列表(v2版)，支持排序、企业项目过滤等。
用法详见：python scripts/as/list_all_scaling_v2_policies.py -h

---

## 伸缩活动日志

### list_scaling_activity_logs.py — 查询伸缩活动日志列表(v1)

作用：查询指定伸缩组的活动日志，返回活动ID、状态、时间、伸缩值、描述等。
用法详见：python scripts/as/list_scaling_activity_logs.py -h

### list_scaling_activity_v2_logs.py — 查询伸缩活动日志列表(v2)

作用：查询指定伸缩组的活动日志(v2版)，支持按类型和状态过滤，返回更详细的实例变更信息。
用法详见：python scripts/as/list_scaling_activity_v2_logs.py -h

---

## 策略执行日志

### list_scaling_policy_execute_logs.py — 查询策略执行日志列表

作用：查询指定策略的执行日志，返回执行状态、类型、时间、旧值/期望值/限制值等。
用法详见：python scripts/as/list_scaling_policy_execute_logs.py -h

---

## 通知

### list_scaling_notifications.py — 查询伸缩组通知列表

作用：查询指定伸缩组的SMN通知配置，返回Topic URN、名称、场景等。
用法详见：python scripts/as/list_scaling_notifications.py -h

---

## 生命周期挂钩

### list_life_cycle_hooks.py — 查询生命周期挂钩列表

作用：查询指定伸缩组的生命周期挂钩，返回挂钩名称、类型、默认结果、超时时间等。
用法详见：python scripts/as/list_life_cycle_hooks.py -h

### show_life_cycle_hook.py — 查询生命周期挂钩详情

作用：查询单个生命周期挂钩详情，包括SMN通知配置等。
用法详见：python scripts/as/show_life_cycle_hook.py -h

### list_hook_instances.py — 查询伸缩组挂钩实例列表

作用：查询处于生命周期挂钩等待状态的实例，返回实例ID、挂钩名称、状态、超时等。
用法详见：python scripts/as/list_hook_instances.py -h

---

## 计划任务

### list_group_scheduled_tasks.py — 查询伸缩组计划任务列表

作用：查询指定伸缩组的计划任务，返回任务ID、名称、创建/更新时间等。
用法详见：python scripts/as/list_group_scheduled_tasks.py -h

---

## 暖池

### list_warm_pool_instances.py — 查询暖池实例列表

作用：查询指定伸缩组的暖池实例，返回实例ID、名称、状态等。
用法详见：python scripts/as/list_warm_pool_instances.py -h

### list_warm_pool_instances_new.py — 查询暖池实例列表(新)

作用：查询指定伸缩组的暖池实例(新版API)，返回实例ID、名称、状态等。
用法详见：python scripts/as/list_warm_pool_instances_new.py -h

### show_warm_pool.py — 查询暖池信息

作用：查询指定伸缩组的暖池配置，返回最小/最大容量、初始化等待时间、状态等。
用法详见：python scripts/as/show_warm_pool.py -h

### show_warm_pool_new.py — 查询暖池信息(新)

作用：查询指定伸缩组的暖池配置(新版API)，返回最小/最大容量、初始化等待时间、状态等。
用法详见：python scripts/as/show_warm_pool_new.py -h

---

## 配额

### show_resource_quota.py — 查询AS资源配额

作用：查询AS服务的资源配额，返回各资源类型的已使用/配额/最大/最小值。
用法详见：python scripts/as/show_resource_quota.py -h

### show_policy_and_instance_quota.py — 查询伸缩组策略和实例配额

作用：查询指定伸缩组的策略和实例配额，返回各类型的已使用/配额/最大/最小值。
用法详见：python scripts/as/show_policy_and_instance_quota.py -h

---

## 标签

### list_scaling_tag_infos_by_resource_id.py — 按资源ID查询标签

作用：查询指定资源的标签列表，返回用户标签和系统标签。
用法详见：python scripts/as/list_scaling_tag_infos_by_resource_id.py -h

### list_scaling_tag_infos_by_tenant_id.py — 按租户ID查询标签

作用：查询租户下所有资源的标签，返回标签键和值列表。
用法详见：python scripts/as/list_scaling_tag_infos_by_tenant_id.py -h

### list_resource_instances.py — 按标签查询资源实例

作用：按标签过滤查询资源实例，返回资源ID、名称、详情和标签。
用法详见：python scripts/as/list_resource_instances.py -h

---

## API版本

### list_api_versions.py — 查询AS API版本列表

作用：查询AS服务支持的API版本列表。
用法详见：python scripts/as/list_api_versions.py -h

### show_api_version.py — 查询AS API版本详情

作用：查询指定API版本的详情，包括版本ID、状态、链接等。
用法详见：python scripts/as/show_api_version.py -h

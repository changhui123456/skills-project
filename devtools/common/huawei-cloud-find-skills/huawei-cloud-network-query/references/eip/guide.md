# EIP Python 脚本使用指南

---

## list_publicips.py — 查询弹性公网IP列表

作用：查询弹性公网IP列表，包括 ID、公网IP地址、状态、类型、alias、带宽大小。
用法详见：python scripts/eip/list_publicips.py -h

---

## list_bandwidth.py — 查询带宽列表

作用：查询带宽列表，包括 ID、名称、大小、类型、计费模式、publicip_count。
用法详见：python scripts/eip/list_bandwidth.py -h

---

## list_bandwidths_limit.py — 查询租户带宽限制

作用：查询租户带宽限制，包括 ID、计费模式、min_size、max_size。
用法详见：python scripts/eip/list_bandwidths_limit.py -h

---

## list_common_pools.py — 查询公共池列表

作用：查询公共池列表，包括 公共边界组、publicip_pools。
用法详见：python scripts/eip/list_common_pools.py -h

---

## list_publicip_pool.py — 查询公网IP池列表

作用：查询公网IP池列表，包括 ID、名称、类型、状态、大小、已使用、公共边界组。
用法详见：python scripts/eip/list_publicip_pool.py -h

---

## list_share_bandwidth_types.py — 查询共享带宽类型列表

作用：查询共享带宽类型列表，包括 ID、带宽类型、name_zh、name_en、公共边界组。
用法详见：python scripts/eip/list_share_bandwidth_types.py -h

---

## list_project_geip_bindings.py — 查询GEIP绑定关系列表

作用：查询GEIP与实例绑定关系的租户列表，包括 geip_id、geip_ip_address、instance_type、instance_id。
用法详见：python scripts/eip/list_project_geip_bindings.py -h

---

## list_tenant_vpc_igws.py — 查询虚拟IGW列表

作用：查询租户下的虚拟IGW列表，包括 ID、名称、VPC ID、enable_ipv6。
用法详见：python scripts/eip/list_tenant_vpc_igws.py -h

---

## show_publicip.py — 查询弹性公网IP详情

作用：查询弹性公网IP详情。
用法详见：python scripts/eip/show_publicip.py -h

---

## show_publicip_pool.py — 查询公网IP池详情

作用：查询公网IP池详情。
用法详见：python scripts/eip/show_publicip_pool.py -h

---

## show_publicip_pool_types.py — 查询公网IP池类型

作用：查询公网IP池类型。
用法详见：python scripts/eip/show_publicip_pool_types.py -h

---

## show_internal_vpc_igw.py — 查询虚拟IGW详情

作用：查询虚拟IGW详情。
用法详见：python scripts/eip/show_internal_vpc_igw.py -h

---

## count_eip_available_resources.py — 查询弹性公网IP可用资源数量

作用：查询弹性公网IP可用资源数量，包括 可用数量。
用法详见：python scripts/eip/count_eip_available_resources.py -h

---

## list_eip_bandwidths.py — 查询带宽列表（v3接口）

作用：查询带宽列表（v3接口，返回更详细的带宽信息），包括 ID、名称、size、type、bandwidth_type、admin_state、publicip_count。
用法详见：python scripts/eip/list_eip_bandwidths.py -h

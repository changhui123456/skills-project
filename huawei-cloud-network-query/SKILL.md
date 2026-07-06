---
name: huawei-cloud-network-query
description: "Queries Huawei Cloud network resources (VPC/EIP/ELB/NAT/VPN/DNS). Covers VPCs, subnets, security groups, firewalls, route tables, flow logs, EIPs, bandwidths, load balancers, listeners, pools, health monitors, NAT gateways, SNAT/DNAT rules, VPN gateways, VPN connections, DNS zones, record sets, PTR records, and endpoints. No write operations. Use this skill when the user needs to query network topology, security group rules, load balancer config, NAT rules, VPN status, or DNS resolution info. Triggers: VPC, 子网, 安全组, EIP, 弹性公网IP, ELB, 负载均衡, NAT网关, VPN, DNS, 域名解析, 路由表, 防火墙, 带宽, network, subnet, security group."
---
# 华为云资源查询

> **⚠️ 执行方式（必读）：本技能通过本地 Python 脚本执行查询，禁止使用 hcloud、openstack 等 CLI 工具或直接调用 API。**
>
> - 查询脚本位于技能目录下 `scripts/<服务分类>/`（如 `scripts/as/list_scaling_groups.py`）
> - 所有脚本和环境检查脚本均在 skill 包内部，**必须使用 `skill action=exec` 执行，不要在 shell 中直接运行**
> - 具体脚本路径和参数参见 `references/<服务>/guide.md`
> - **不要尝试 hcloud、openstack、curl IAM 等 CLI/API 方式，本技能不依赖这些工具**
> - **所有路径均为技能目录下的相对路径，技能目录即本 SKILL.md 所在目录**

## 概述

本技能是一个独立的只读查询技能，用于通过本地 Python 脚本调用华为云 Python SDK，查询华为云资源、可售规格以及现网已有资源信息。

本技能适用于以下场景：

1. 查询某个 region 下可用的云资源规格
2. 查询某类操作系统有哪些镜像可用
3. 查询云硬盘类型与现有云硬盘信息
4. 查询已有资源及其关键属性
5. 查询并非通过 Terraform 或其他 IaC 工具创建的资源
6. 为自动化配置、资源核对或环境盘点准备真实参数
7. 获取资源 ID、名称、规格、镜像、网络、磁盘等可复用信息

本技能不负责以下事项：

1. 创建资源
2. 修改资源
3. 删除资源
4. 对未查询到的信息进行猜测或编造

---

## 能力范围

本技能通过 scripts 目录下的分类脚本提供查询能力，并通过 references 目录下的分类说明书提供使用说明。
本技能提供的能力包括：

1. 查询资源列表
2. 查询单个资源详情
3. 查询现网资源的关键标识和依赖关系

---

## 使用原则

重要：本技能内执行的脚本路径均为技能目录下的相对路径，技能目录即本 SKILL.md 所在目录

1. 本技能只做查询，不做任何写操作
2. 优先使用用户明确指定的 region、project、az、资源名称、资源 ID 等信息
3. 查询结果必须以真实接口返回为准，不凭经验推测
4. 返回结果应优先保留关键字段，便于后续复用
5. 当结果集较大时，应优先按 region、name、id、status、tag 等条件缩小范围
6. 如果当前资源类型没有对应脚本或说明书，应明确说明未支持，不返回不可靠结果
7. 如果用户未提供必要范围信息，且环境中也没有默认值，应先补充确认后再执行查询
8. 直接按照guide.md执行即可，不要查看scripts目录中的脚本内容
9. 当输出比较大的时候要缓存
10. 每个脚本执行之前都必须先执行-h查看用法
11. 不要凭空想象脚本的名称，要按照guide.md中的脚本名称执行，如果guide.md中没有对应的脚本名称，就说明不支持

---

## 前置条件

**使用前必须先运行环境检查脚本，一键完成环境校验与依赖安装：**

- Linux / macOS：`skill action=exec: bash skill://scripts/check_env.sh`
- Windows：`skill action=exec: powershell -ExecutionPolicy Bypass -File skill://scripts/check_env.ps1`

> Windows 注意：不要使用 `&&` 拼接命令（PowerShell 5.x 不支持），如需先切换目录请用分号

脚本会依次检查：Python >= 3.6 → 安装依赖 → 校验 SDK → 校验凭据 → 校验服务可用性。若环境检查失败，修复问题后才能继续执行其他脚本。

**网络需求：**

本技能需要网络访问以下华为云服务端点（通过 Python SDK 发起 HTTPS 请求）：

- `myhuaweicloud.com` — 华为云 API 网关（IAM、VPC、EIP、ELB、NAT、VPN、DNS 等服务）
- `pypi.org` / `repo.huaweicloud.com` — Python 依赖安装镜像源（仅在环境检查时访问）

**环境变量：**

| 变量 | 必填 | 说明 |
|------|------|------|
| HW_ACCESS_KEY | 是 | 华为云 AK |
| HW_SECRET_KEY | 是 | 华为云 SK |
| HW_REGION_NAME | 否 | 默认 cn-north-4 |
| HW_PROJECT_ID | 否 | 项目 ID（未设置时自动通过 IAM 接口获取） |
| HW_SECURITY_TOKEN | 否 | 临时 AK/SK 时需要 |

**禁止输出以上环境变量的值。** 其他资源脚本如需额外参数（可用区、企业项目等），见对应 guide.md。

---

## 执行流程

**当本技能被调用时，必须按以下步骤执行，不要等待用户再次提示：**

### 步骤 1：环境准备

执行环境检查脚本，确保依赖已安装、凭据已配置：

- Linux / macOS：`skill action=exec: bash skill://scripts/check_env.sh`
- Windows：`skill action=exec: powershell -ExecutionPolicy Bypass -File skill://scripts/check_env.ps1`

如果环境检查失败，按提示修复后重新执行，直到通过。

### 步骤 2：识别并执行查询脚本

1. 根据用户查询意图，读取 `references/<服务>/guide.md`，确定要执行的脚本路径和参数
2. 先执行 `-h` 查看脚本用法：
   - Linux / macOS：`skill action=exec: skill://.venv/bin/python3 skill://scripts/<服务>/<脚本>.py -h`
   - Windows：`skill action=exec: skill://.venv/Scripts/python3.exe skill://scripts/<服务>/<脚本>.py -h`
3. 根据用户需求组装参数，执行脚本：
   - Linux / macOS：`skill action=exec: skill://.venv/bin/python3 skill://scripts/<服务>/<脚本>.py <参数>`
   - Windows：`skill action=exec: skill://.venv/Scripts/python3.exe skill://scripts/<服务>/<脚本>.py <参数>`
4. 将结果格式化后返回给用户

**重要**：

- 所有脚本和环境检查脚本均在 skill 包内部，**必须使用 `skill action=exec` 执行，不要在 shell 中直接运行**
- venv 由 check_env 脚本自动创建，Linux/macOS 下 Python 位于 `.venv/bin/python3`，Windows 下位于 `.venv/Scripts/python3.exe`
- 不要直接用 `python3` 执行脚本
- 不要读取 scripts 目录下的脚本源码，按照 guide.md 中的说明执行即可
- 当输出较大时，应缓存结果
- `--project_id` 参数为可选，未提供时自动根据 region 通过 IAM 接口获取

---

## 目录结构

目录约定如下（所有路径基于技能目录）：

1. scripts/资源分类/ 下存放对应资源的 Python 查询脚本。不需要读取脚本内容，按照 guide.md 中的使用说明执行脚本即可
2. references/资源分类/guide.md 下存放对应资源的使用说明书
3. 每个脚本只负责一个清晰、单一的查询动作
4. 每类资源至少维护一份 guide.md，用于说明脚本能力、参数和使用方式

---

## 参数确认

执行查询脚本前，需确认以下参数：

| 参数 | 必填 | 说明 |
|------|------|------|
| region | 是 | 华为云区域，如 cn-north-4 |
| --project_id | 否 | 项目 ID，未提供时自动获取 |
| --availability_zone | 否 | 可用区，部分资源查询需要 |

其他脚本特有参数见 `references/<服务>/guide.md`。

---

## 输出格式

查询结果默认以 **制表符分隔（TSV）纯文本** 格式输出

- 具体字段因脚本而异，详见各 guide.md

---

## 验证方法

1. 执行环境检查脚本确认依赖和凭据可用
2. 使用 `-h` 参数查看脚本用法，确认参数正确
3. 对已知资源执行查询，对比控制台数据验证结果准确性
4. 检查返回的 `total` 数量是否合理

---

## 最佳实践

1. 先缩小查询范围（指定 region、可用区等），避免返回过多数据
2. 使用 `--help` 查看脚本支持的完整参数列表
3. 查询结果较大时缓存到本地，避免重复请求
4. 需要多个资源信息时，按依赖顺序查询（如先查 VPC 再查子网）
5. 脚本执行失败时，先检查环境变量和网络连通性

---

## 参考文档

- [华为云 Python SDK 官方文档](https://doc.huihua.com/api/sdk/python.html)
- [华为云 API Explorer](https://support.huaweicloud.com/apiexplorer/index.html)
- 各服务查询脚本使用说明：`references/<服务>/guide.md`

---

## 注意事项

1. 本技能仅提供只读查询能力，不执行任何写操作
2. 禁止输出 HW_ACCESS_KEY、HW_SECRET_KEY 等环境变量的值
3. 所有脚本必须通过 `skill action=exec` 执行，不要在 shell 中直接运行
4. 不要凭空猜测脚本名称，严格按照 guide.md 中的名称执行
5. 查询前必须先运行环境检查脚本
6. 临时 AK/SK 使用时需设置 HW_SECURITY_TOKEN
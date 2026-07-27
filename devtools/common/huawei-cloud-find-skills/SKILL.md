---
name: huawei-cloud-find-skills
description: >
  搜索、发现和浏览华为云Agent Skills。当用户想查找华为云相关技能时触发，
  包括："华为云有什么skill"、"搜索华为云技能"、"有没有管理ECS/OBS的skill"、
  "华为云skills有哪些类目"、"帮我找一个skill"、"浏览华为云skills"、
  "华为云agent skill市场"、"搜一下华为云的skill"、"XX Skill的内容是什么"。
tags: [huawei-cloud, skills, search, discovery, find, devops]
version: 1.0.0
---

# 华为云 Agent Skills 搜索与发现

## 概述

本技能帮助用户搜索、发现和了解华为云Agent Skills。华为云Skills体系托管在GitCode仓库，通过KooCLI + GitCode API + 浏览器实现技能的搜索、浏览和安装。

**架构**: KooCLI + GitCode API → developer-skill仓库 → Skills目录

## 场景描述

本技能支持用户：

1. **搜索Skills** — 按关键词、分类或服务名搜索华为云Skills
2. **浏览分类** — 查看所有可用Skills分类和子分类
3. **查看Skill详情** — 获取特定Skill的完整内容
4. **安装Skills** — 指导用户完成Skill安装
5. **验证Skills** — 验证已安装Skill的命令是否可用

## 华为云Skills目录

### 按服务分类

| 分类 | Skills | 说明 |
|------|--------|------|
| **计算** | huawei-cloud-ecs-diagnose, huawei-cloud-ecs-diagnosis-workflow | ECS实例诊断与故障排查 |
| **存储** | huawei-cloud-obs-manage | OBS对象存储管理 |
| **开发工具** | huawei-cloud-cli-guidance | KooCLI通用指导(100+服务) |
| **运维** | huawei-cloud-ecs-diagnosis-workflow | 分层诊断工作流 |

### 按功能分类

| 功能域 | Skills | 关键词 |
|--------|--------|--------|
| **故障诊断** | huawei-cloud-ecs-diagnose, huawei-cloud-ecs-diagnosis-workflow | 诊断, 故障, SSH不通, 磁盘满, CPU高 |
| **对象存储** | huawei-cloud-obs-manage | OBS, 上传, 下载, 同步, 备份, 桶 |
| **CLI指导** | huawei-cloud-cli-guidance | CLI, 命令, 参数, 报错, 调试 |
| **技能发现** | huawei-cloud-find-skills | 搜索, 浏览, 安装, 发现 |

## 核心工作流

### Step 1: 搜索Skills

根据用户意图，选择关键词搜索、分类搜索或两者结合：

```bash
# 方法A: 通过GitCode API搜索仓库内容
curl -s -H "PRIVATE-TOKEN: <token>" \
  "https://api.gitcode.com/api/v5/repos/developer-skill/developer-skill/contents?ref=master" \
  | python3 -c "import sys,json; [print(d['name']) for d in json.load(sys.stdin) if d['type']=='dir']"

# 方法B: 搜索本地已安装Skills
ls ~/.hermes/skills/devops/

# 方法C: 搜索Skill内容（关键词匹配）
grep -r "关键词" ~/.hermes/skills/devops/*/SKILL.md
```

### Step 2: 浏览分类

```bash
# 列出所有已安装Skills
ls -la ~/.hermes/skills/devops/

# 查看Skill基本信息（YAML frontmatter）
head -10 ~/.hermes/skills/devops/*/SKILL.md

# 按标签过滤
grep -l "tags:.*ECS" ~/.hermes/skills/devops/*/SKILL.md
```

### Step 3: 查看Skill详情

```bash
# 查看完整SKILL.md
cat ~/.hermes/skills/devops/<skill-name>/SKILL.md

# 查看references文件
ls ~/.hermes/skills/devops/<skill-name>/references/

# 查看特定reference
cat ~/.hermes/skills/devops/<skill-name>/references/<file>.md
```

### Step 4: 安装Skill

华为云Skills通过GitCode仓库获取，安装到 `~/.hermes/skills/devops/` 目录：

```bash
# 方法A: 从GitCode仓库克隆并复制
git clone https://gitcode.com/developer-skill/developer-skill.git /tmp/skill-download
cp -r /tmp/skill-download/<skill-name> ~/.hermes/skills/devops/

# 方法B: 通过Hermes skill命令安装
# (如果技能已发布到Hermes Skills Hub)
```

### Step 5: 验证Skill可用性

```bash
# 验证KooCLI基础命令
hcloud --help | head -1

# 验证特定服务的CLI支持
hcloud <SERVICE> <Operation> --cli-region=cn-north-4 2>&1 | head -5

# 验证Skill文件完整性
ls ~/.hermes/skills/devops/<skill-name>/SKILL.md
ls ~/.hermes/skills/devops/<skill-name>/references/
```

## 搜索策略

### 1. 关键词选择

| 搜索意图 | 推荐关键词 | 可能匹配的Skill |
|---------|-----------|----------------|
| ECS管理/诊断 | ECS, 云服务器, 诊断, 故障 | ecs-diagnose, ecs-diagnosis-workflow |
| 对象存储 | OBS, 对象存储, 桶, 上传, 下载 | obs-manage |
| CLI命令 | CLI, 命令行, 参数, 调试 | cli-guidance |
| 备份/同步 | 备份, 同步, 定时, cron | obs-manage |
| 网络问题 | 网络, 连通, 带宽, 探测 | obs-manage, ecs-diagnosis-workflow |
| 权限 | IAM, ACL, 策略, 权限 | cli-guidance |

### 2. 搜索迭代

如果首次搜索未找到目标Skill：

1. **切换中英文关键词**: "云服务器" → "ECS", "对象存储" → "OBS"
2. **扩大关键词**: "RDS备份" → "RDS", "ECS SSH不通" → "ECS诊断"
3. **移除分类过滤**: 仅按关键词搜索
4. **尝试同义词**: "实例" → "ECS", "桶" → "OBS"
5. **浏览全部分类**: 列出所有Skills让用户选择

### 3. 结果展示格式

```
找到 N 个华为云Skills:

| Skill名称 | 版本 | 说明 | 分类 | 关键服务 |
|-----------|------|------|------|---------|
| huawei-cloud-ecs-diagnosis-workflow | v2.0.0 | ECS分层诊断工作流 | 计算 | ECS/VPC/EIP/CES |
| huawei-cloud-obs-manage | v1.0.0 | OBS对象存储管理 | 存储 | OBS |
| ... | ... | ... | ... | ... |
```

## 认证要求

> **前置检查: KooCLI已配置AKSK**
>
> **安全规则:**
>
> - **禁止** 读取、回显或打印AK/SK值
> - **禁止** 在对话或命令行中直接输入AK/SK
> - **仅** 使用 `hcloud configure list` 检查认证状态
>
> ```bash
> hcloud configure list
> ```
>
> 检查输出中是否有有效的AKSK配置。
>
> **如果没有有效配置，停止操作：**
>
> 1. 通过华为云控制台获取AK/SK
> 2. 在**本会话外**配置凭证（通过 `hcloud configure set` 或环境变量）
> 3. 配置完成后重新执行

## IAM权限

本技能为只读操作，不创建任何资源。搜索Skills仅需：
- GitCode仓库读取权限（公开仓库无需认证）
- KooCLI基础认证（验证CLI可用性）

## 参考文档

| 文档 | 说明 |
|------|------|
| [references/skill-catalog.md](references/skill-catalog.md) | 华为云Skills完整目录与功能说明 |
| [references/search-commands.md](references/search-commands.md) | 搜索命令完整参考 |

## 故障排查

### 问题: GitCode API返回403
**原因**: PAT令牌无效或过期
**解决**: 重新生成GitCode PAT，更新认证头

### 问题: 本地Skills目录为空
**原因**: Skills未安装
**解决**: 从GitCode仓库克隆并安装到 `~/.hermes/skills/devops/`

### 问题: 搜索无结果
**原因**: 关键词不匹配或Skills数量有限
**解决**:
1. 尝试更广泛的关键词
2. 浏览全部分类
3. 切换中英文关键词
4. 确认Skill是否已创建（华为云Skills持续扩展中）

### 问题: KooCLI命令报错
**原因**: AKSK未配置或服务不支持
**解决**: `hcloud configure list` 检查认证，`hcloud --help` 检查CLI版本

## 注意事项

- 本技能为**只读操作**，不创建任何云资源
- 华为云Skills数量持续扩展中，如未找到所需Skill可提出需求
- 搜索结果以本地已安装Skills和GitCode仓库为准
- Skills安装后需重启Agent会话才能生效

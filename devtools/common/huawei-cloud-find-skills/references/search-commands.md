# 搜索命令完整参考

## GitCode API搜索

### 列出仓库目录

```bash
# 列出developer-skill仓库根目录
curl -s -H "PRIVATE-TOKEN: <token>" \
  "https://api.gitcode.com/api/v5/repos/developer-skill/developer-skill/contents?ref=master"

# 列出特定Skill目录
curl -s -H "PRIVATE-TOKEN: <token>" \
  "https://api.gitcode.com/api/v5/repos/developer-skill/developer-skill/contents/huawei-cloud-obs-manage?ref=master"
```

### 获取文件内容

```bash
# 获取SKILL.md内容
curl -s -H "PRIVATE-TOKEN: <token>" \
  "https://api.gitcode.com/api/v5/repos/developer-skill/developer-skill/contents/huawei-cloud-obs-manage/SKILL.md?ref=master" \
  | python3 -c "import sys,json,base64; print(base64.b64decode(json.load(sys.stdin)['content']).decode())"
```

### 搜索仓库内容

```bash
# 搜索代码内容
curl -s -H "PRIVATE-TOKEN: <token>" \
  "https://api.gitcode.com/api/v5/repos/developer-skill/developer-skill/search?q=OBS&ref=master"
```

---

## 本地Skills搜索

### 列出已安装Skills

```bash
# 列出所有已安装Skills
ls ~/.hermes/skills/devops/

# 详细列表
ls -la ~/.hermes/skills/devops/

# 统计数量
ls ~/.hermes/skills/devops/ | wc -l
```

### 按关键词搜索

```bash
# 搜索SKILL.md中的关键词
grep -rl "关键词" ~/.hermes/skills/devops/*/SKILL.md

# 搜索tags字段
grep -rl "tags:.*ECS" ~/.hermes/skills/devops/*/SKILL.md

# 搜索description字段
grep -rl "description:" ~/.hermes/skills/devops/*/SKILL.md | xargs grep "诊断"

# 搜索所有文件内容
grep -rl "关键词" ~/.hermes/skills/devops/
```

### 按分类搜索

```bash
# 搜索计算类Skills
grep -rl "计算\|ECS" ~/.hermes/skills/devops/*/SKILL.md

# 搜索存储类Skills
grep -rl "存储\|OBS" ~/.hermes/skills/devops/*/SKILL.md

# 搜索开发工具类Skills
grep -rl "CLI\|开发工具" ~/.hermes/skills/devops/*/SKILL.md
```

### 查看Skill详情

```bash
# 查看SKILL.md
cat ~/.hermes/skills/devops/<skill-name>/SKILL.md

# 查看references文件列表
ls ~/.hermes/skills/devops/<skill-name>/references/

# 查看特定reference文件
cat ~/.hermes/skills/devops/<skill-name>/references/<file>.md

# 查看Skill基本信息（YAML frontmatter）
head -20 ~/.hermes/skills/devops/<skill-name>/SKILL.md
```

---

## KooCLI验证命令

### 验证CLI基础

```bash
# KooCLI版本
hcloud --help | head -1

# 认证状态
hcloud configure list

# 可用服务列表
hcloud --help 2>&1 | grep -i "supported"
```

### 验证特定Skill的命令

```bash
# ECS相关
hcloud ECS ListServersDetails --cli-region=cn-north-4 2>&1 | head -5

# VPC相关
hcloud VPC ListSecurityGroups/v3 --cli-region=cn-north-4 2>&1 | head -5

# OBS相关
hcloud OBS help 2>&1 | head -10

# CES相关
hcloud CES ListMetrics --namespace=SYS.ECS --cli-region=cn-north-4 --limit=5 2>&1 | head -5

# IAM相关
hcloud IAM KeystoneListUsers --cli-region=cn-north-4 2>&1 | head -5
```

---

## 搜索参数说明

| 参数 | 必选/可选 | 说明 | 默认值 |
|------|----------|------|--------|
| `keyword` | 可选 | 搜索关键词（服务名、功能名或描述） | 无 |
| `category` | 可选 | 分类过滤（计算/存储/开发工具/运维） | 无 |
| `scope` | 可选 | 搜索范围（local=本地, remote=GitCode, all=全部） | all |
| `detail` | 可选 | 是否显示详细内容 | false |

---

## 结果格式

搜索结果以表格形式展示：

```
找到 N 个华为云Skills:

| Skill名称 | 版本 | 说明 | 分类 | 关键服务 |
|-----------|------|------|------|---------|
| huawei-cloud-ecs-diagnosis-workflow | v2.0.0 | ECS分层诊断工作流 | 计算 | ECS/VPC/EIP/CES |
```

字段说明：
- **Skill名称**: 用于安装和详细查询
- **版本**: 当前版本号
- **说明**: 功能概述
- **分类**: 所属分类
- **关键服务**: 涉及的主要华为云服务

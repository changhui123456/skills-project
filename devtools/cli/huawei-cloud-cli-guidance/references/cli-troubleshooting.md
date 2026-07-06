# KooCLI 错误排查与FAQ

## 常见错误分类

### 1. 安装与配置错误

| 错误 | 原因 | 解决方案 |
|------|------|---------|
| `hcloud: command not found` | KooCLI未安装或不在PATH | `sudo mv hcloud /usr/local/bin/` |
| `Permission denied` | 无执行权限 | `chmod +x /usr/local/bin/hcloud` |
| `hcloud --version` 无输出 | 已知Bug | 使用 `hcloud --help` |
| SSL/TLS证书错误 | 系统CA证书过旧 | `apt update && apt install ca-certificates` |
| 连接超时 | 网络限制/代理 | 检查防火墙/代理设置 |

### 2. 认证错误

| 错误 | 原因 | 解决方案 |
|------|------|---------|
| `InvalidAccessKeyId` | AK不存在或拼写错误 | 检查AK值，重新配置 |
| `SignatureDoesNotMatch` | SK错误 | 检查SK值，重新配置 |
| `TokenIsExpired` | 临时Token过期 | 重新获取Token |
| `NoPermission` | IAM权限不足 | 联系管理员授权 |
| `AccountRestricted` | 账号被限制 | 联系华为云支持 |

**检查认证状态**:
```bash
hcloud configure list
```

**重新配置认证**:
```bash
hcloud configure set
```

### 3. 参数错误

| 错误 | 原因 | 解决方案 |
|------|------|---------|
| `Unsupported service` | 服务名拼写错误 | 确保服务名**大写**: `ECS` 非 `ecs` |
| `Unsupported operation` | 操作名拼写错误 | 确保PascalCase: `ListServersDetails` |
| `parameter is required` | 缺少必填参数 | 查看帮助: `hcloud <SERVICE> <Op> --help` |
| `cli-region is required` | 未指定区域 | 添加 `--cli-region=<region>` |
| `Invalid parameter` | 参数值格式错误 | 参考 parameter-format.md |
| `InvalidParameterValue` | 参数值不在允许范围 | 检查枚举值 |

**查看操作帮助**:
```bash
hcloud ECS CreateServers --help
```

### 4. 资源错误

| 错误 | 原因 | 解决方案 |
|------|------|---------|
| `404 Not Found` | 资源不存在 | 检查ID和区域 |
| `409 Conflict` | 资源状态冲突 | 实例可能正在执行其他操作 |
| `QuotaExceeded` | 配额超限 | 申请提升配额或清理资源 |
| `ResourceNotFound` | 资源ID无效 | 确认ID正确，检查区域 |
| `InstanceLocked` | 实例锁定 | 等待当前操作完成 |

### 5. 网络错误

| 错误 | 原因 | 解决方案 |
|------|------|---------|
| `Connection refused` | API端点不可达 | 检查网络/代理 |
| `Connection timeout` | 网络超时 | 检查防火墙/增加超时 |
| `Too many requests` | 请求频率过高 | 降低请求频率 |

---

## FAQ

### Q1: hcloud --version 为什么不工作？
**A**: 这是KooCLI的已知问题。使用 `hcloud --help` 查看版本信息。

### Q2: VPC操作什么时候需要/v3后缀？
**A**: 安全组相关操作需要/v3后缀（ListSecurityGroups/v3, ShowSecurityGroup/v3等），VPC和子网操作不需要但也可以加（ListVpcs/v3同样有效）。EIP操作也需要/v3后缀。ELB也支持/v3后缀。

### Q3: EIP是VPC的子服务吗？
**A**: 不是。EIP是独立服务，使用 `hcloud EIP ...` 而非 `hcloud VPC ...`。

### Q4: 批量操作参数格式是什么？
**A**: 使用 `--操作.资源名.索引.字段=值` 格式：
```bash
# 启动多个实例
hcloud ECS NovaStartServers --os-start.servers.1.id=<id1> --os-start.servers.2.id=<id2>

# 删除多个实例
hcloud ECS DeleteServers --servers.1.id=<id1> --servers.2.id=<id2>
```

### Q5: 如何查看某个操作的所有参数？
**A**: 使用 `--help`：
```bash
hcloud ECS CreateServers --help
```

### Q6: 如何切换区域？
**A**: 每个命令指定 `--cli-region=<region>`，或设置默认区域：
```bash
hcloud configure set --cli-region=cn-north-4
```

### Q7: 如何使用多个Profile？
**A**:
```bash
# 创建新Profile
hcloud configure set --cli-profile=prod

# 使用指定Profile
hcloud ECS ListServersDetails --cli-profile=prod --cli-region=cn-north-4
```

### Q8: KooCLI能查看账单吗？
**A**: 不能。BSS（费用账单）服务KooCLI不支持，需通过浏览器访问 https://bss.huaweicloud.com。

### Q9: OBS对象存储用KooCLI还是obsutil？
**A**: 推荐使用obsutil，功能更完整，性能更好。

### Q10: Ubuntu 22.04实例默认允许root SSH吗？
**A**: 是的。华为云Ubuntu 22.04公共镜像默认 PermitRootLogin=yes, PasswordAuthentication=yes。自定义镜像可能不同。

### Q11: 实例规格as7/ac7还能用吗？
**A**: 不能。as7/ac7系列已废弃，使用ac8/as8系列（如ac8.large.2）。

### Q12: 安全组规则如何指定端口范围？
**A**: 使用 port_range_min 和 port_range_max：
```bash
# 单端口
--security_group_rule.port_range_min=22 --security_group_rule.port_range_max=22

# 端口范围
--security_group_rule.port_range_min=8000 --security_group_rule.port_range_max=9000
```

### Q13: CES监控时间戳格式是什么？
**A**: Unix时间戳（秒）× 1000（毫秒）：
```bash
# 最近1小时
--from=$(date -d '1 hour ago' +%s)000 --to=$(date +%s)000
```

### Q14: 如何获取VNC远程控制台？
**A**:
```bash
hcloud ECS ShowServerRemoteConsole \
  --server_id=<id> \
  --remote_console.protocol=vnc \
  --remote_console.type=novnc \
  --cli-region=<region>
# 在浏览器中打开返回的URL
```

---

## 调试技巧

### 1. 查看详细日志
```bash
hcloud ECS ListServersDetails --cli-region=cn-north-4 --cli-debug=true
```

### 2. 查看API请求
```bash
# 输出原始HTTP请求和响应
hcloud ECS ShowServer --server_id=<id> --cli-region=cn-north-4 --cli-output=raw
```

### 3. JSON输出处理
```bash
# 用jq处理JSON输出
hcloud ECS ListServersDetails --cli-region=cn-north-4 | python3 -c "
import sys, json
data = json.load(sys.stdin)
for s in data.get('servers', []):
    print(f\"{s['id'][:12]}  {s['name']:20s}  {s['status']}\")
"
```

### 4. 重试机制
```bash
# 对于偶发错误，可重试
for i in 1 2 3; do
  result=$(hcloud ECS ShowServer --server_id=<id> --cli-region=cn-north-4 2>&1)
  if echo "$result" | grep -q "id"; then
    echo "$result"
    break
  fi
  echo "Retry $i..."
  sleep 2
done
```

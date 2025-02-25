---
name: "🚀 NPU Runner Deployment Request"
about: "Request NPU compute resources for organization workflows"
title: "[NPU REQUEST] Add {org-name} to NPU Runners"
labels: "npu-resources"
assignees: ""
---

<!-- 🌟 请填写以下信息以申请NPU计算资源 -->

<details open>
<summary><strong>🏢 组织信息</strong></summary>

| 字段 | 描述 | 示例 | 必填 |
|------|------|------|-----|
| `org-name` | 申请组织的全称 | `awesome-ai-org` | ✅ |
| `github-app` | 关联的GitHub应用ID | `NPU-Manager-App` | ✅ |
| `installation-id` | 应用安装ID | `987654321` | ✅ |

</details>

<details open>
<summary><strong>⚙️ 运行器配置</strong></summary>

| 字段 | 描述 | 示例 | 必填 |
|------|------|------|-----|
| `runner-group` | 运行器组类型 | `accelerated-compute` | ✅ |
| `group-name` | 自定义组名称 | `npu-research-team` | ✅ |
| `runner-set` | 运行器集合标识 | `npu-v100-cluster` | ✅ |
| `npu-counts` | 需要的NPU数量 | `8` | ✅ |

</details>

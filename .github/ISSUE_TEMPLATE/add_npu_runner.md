---
name: "🚀 Add Organization"
about: "Request NPU compute resources for organization workflows"
title: "[Insert] Add Organization to NPU Runners"
labels: "npu-resources"
assignees: ""
---

Welcome to use this template to submit an issue to add your organization to the NPU operator. Please follow the instructions below to fill in the relevant information so that we can process your request more efficiently.

```yaml
org-name: 
github-app: 
  instalation-id: 
runner-group: 
  group-name: 
runner-set: 
  npu-counts: 
```

| Field | Description | Example | Required |
|------|------|------|-----|
| `org-name` | Full name of the organization | `awesome-ai-org` | ✅ |
| `github-app.installation-id` | Installation ID after installing ascend-runner-mgmt | `11111111` | ✅ |
| `runner-group.group-name` | The group name of the configured runner group | `ascend-ci` | ✅ |
| `runner-set.npu-counts` | The number array of NPU chip | `1,2` | ✅ |


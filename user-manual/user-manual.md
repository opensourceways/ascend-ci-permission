# 组织管理员->组织/仓库如何为github action接入昇腾设备
## 准备工作
需要具备组织的管理权限
## 1 安装 github app
在浏览器输入`https://github.com/apps/ascend-runner-mgmt`并且点击`Install`或者`Configure`
![alt text](assets/使用说明文档/image-3.png)
![alt text](<assets/user manual/image.png>)
选择组织，选择仓库，点击`Install`
![alt text](assets/使用说明文档/image-5.png)

## 2 获取 github app 的 installation-id
依次点击组织的`Settings`, `GitHub Apps`, `ascend-runner-mgmt`的`Configure`，进入install页面。
![alt text](assets/使用说明文档/image-7.png)
`installation url`形如`https://github.com/organizations/<your-organization>/settings/installations/<installation-id>`，将`installation-id`提交给后端配置。

## 3 配置 runner group
依次点击组织的`Settings`, `Actions`, `Runner groups`, `New runner group`，进入创建页面。
![alt text](assets/使用说明文档/image-8.png)

配置好`group name, repository access, workflow access`即可创建`runner group`。`group name`需要提交给后端配置。

注意：如果未打钩`Allow public repositories`，则无法让`public`仓库执行`github action`。

如果要限定`workflow`范围，`Workflow access`写法如下，多个分支以逗号分隔。
```text
<organization>/<repo>/.github/workflows/<workflow.yaml>@<branch>
例子：
my-org/my-repo/.github/workflows/my.yaml@main
```
![alt text](assets/使用说明文档/image-2.png)

配置好后，runners为0
![alt text](<assets/user manual/image-2.png>)

## 4 等待后端配置
在`ascend-ci-config`目录下参考`my-org.yaml`创建yaml文件。文件名是组织名。
```yaml
# 组织名
org-name: my-org
github-app:
  # github app的installation id
  installation-id: 11111111
runner-group:
  # runner-group的group-name
  group-name: xxxxx
runner-set:
  # npu-counts代表当前仓库所需要的npu卡数
  npu-counts: 1, 2
```
等后端配置好后，可以在runners查看。`Status`为`Online`表示可以运行,为`Offline`表示无法运行。
![alt text](<assets/user manual/image-4.png>)

## 5 测试使用
测试workflow：
```yaml
name: Show npu resource
on:
  workflow_dispatch:
jobs:
  jobs_npu1:
    runs-on: linux-arm64-npu-1
    container:
      image: ascendai/cann:latest

    steps:
      - name: Show NPU info
        run: |
          npu-smi info
  jobs_npu2:
    runs-on: linux-arm64-npu-2
    container:
      image: ascendai/cann:latest

    steps:
      - name: Show NPU info
        run: |
          npu-smi info
```
依次点击`Actions`, `Test NPU`, `Run workflow`, `Run workflow`即可实现测试。
![alt text](<assets/user manual/image-5.png>)


# workflow使用者->如何在github action中使用昇腾设备
## 准备工作
已经完成[组织仓库接入昇腾设备](#组织管理员-组织仓库如何为github-action接入昇腾设备)中的步骤

## 操作步骤
参考[yaml](#5-测试使用)填写workflow.

## 测试使用
以`https://github.com/cllouud-7-org/repo1`仓库为例，配置单卡runner和2卡runner

测试 workflow:
https://github.com/cllouud-7-org/repo1/actions/runs/13470382216


如果需要帮忙，请联系yaml_1@163.com。

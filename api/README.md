## Baobaozhuan Api 设计文档

{:.no_toc}

* 目录
{:toc}

---

### 如何使用

1. 打开 [Swagger Editor](http://editor.swagger.io/)

2. 将该 [api.yaml](./api.yaml) 文件内容复制到编辑器中

3. 右侧将显示可交互的动态api文档，可查看并测试

### 编辑历史

| 版本 |   日期    | 描述 |  作者   |
| :--: | :-------: | :--: | :-----: |
| v1.0 | 2019-05-13 | 登录注册api | gitgiter |
| v1.1 | 2019-05-14 | 修改用户资料api | gitgiter |
| v1.2 | 2019-05-14 | 发布任务api | gitgiter |
| v1.3 | 2019-05-14 | 终止、验证、修改任务api | gitgiter |
| v1.4 | 2019-05-14 | 接受、浏览、查看任务api | gitgiter |
| v1.5 | 2019-05-14 | 取消任务、广告投放api | gitgiter |
| v1.6 | 2019-05-15 | 初步完善api | gitgiter |
| v2.0 | 2019-05-21 | 全面完善api | gitgiter |
| v2.1 | 2019-05-21 | 偏好、标签api | gitgiter |
| v2.2 | 2019-05-21 | 提交任务api，细节完善 | gitgiter |
| v2.3 | 2019-05-24 | 字段命名修改，user_id细化 | gitgiter |
| v2.4 | 2019-05-27 | task字段更正，增加resources列表类api | gitgiter |
| v2.5 | 2019-05-27 | 增加获取已提交、已发布、已接受任务列表api | gitgiter |
| v2.6 | 2019-05-28 | 修改ad返回格式，完善resources列表类api | gitgiter |
| v2.7 | 2019-06-01 | 重写获取已提交任务api，task增加status | gitgiter |
| v2.8 | 2019-06-03 | 统计结果查询、下载api，细节完善 | gitgiter |
| v2.9 | 2019-06-03 | 删除问卷的statistic字段，拆分招募的time | gitgiter |
| v3.0 | 2019-06-04 | 重写获取已接受任务api，约束answer格式 | gitgiter |
| v3.1 | 2019-06-04 | 修改gender字段类型，长表单改json | gitgiter |
| v3.2 | 2019-06-06 | status字段类型更正，获取接受任务api更正 | gitgiter |
| v3.3 | 2019-06-06 | 获取任务详情api加入acceptance，注释细节完善 | gitgiter |
| v4.0 | 2019-06-06 | 全面整改api风格，去除冗余user_id，细节完善 | gitgiter |
| v4.1 | 2019-06-07 | 增加获取用户信息api、preference修改api，去掉用户信息修改中的preference，将获取推荐、已发布、已接受任务归入user | gitgiter |
| v4.2 | 2019-06-08 | 增加status说明 | gitgiter |

### 备注

1. 由于微信小程序不支持 patch 方法，api中的 patch 方法在实现的时候均视为 put。

2. 请求的时候注意 content type 的要求，表单要以 application/x-www-form-urlencoded 的格式，application/json 表示以 json 格式传递数据。

3. 某些字段如有注明 in json format，则该字段也要以 json 格式传递，如 acceptance 的 answer 字段。

4. 数据模型的基本格式及其字段含义，可以在 api 文档最下面的 schemas 部分中对应查看。

5. 注明有 cookie needed 的 api 表示需要鉴权，请求的时候需要带上登录时返回的 cookie。
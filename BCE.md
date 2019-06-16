| 版本 |   日期    | 描述 |  作者   |
| :--: | :-------: | :--: | :-----: |
| v1.0 | 2019-06-16 | 完成文档编写 | gitgiter |
| v1.1 | 2019-06-16 | 修改小程序、后端项目结构 | gitgiter |

## 逻辑架构到应用程序映射指南(BCE)

### 1 逻辑架构
逻辑架构由三层模型（表示层、业务层、持久化层）构成

#### 1.1 表示层
客户端使用微信小程序作为表示层，提供用户信息管理子系统、用户任务管理子系统、问卷子系统、信息收集子系统、人员招募子系统。

#### 1.2 业务层
服务端作为业务层，为表示层的各个子系统提供相应的服务模块。

#### 1.3 持久化层
MySQL 提供了数据的持久化服务。
Redis 提供了会话、缓存的持久化服务。

### 2 框架目录设计

#### 2.1 小程序
```
miniProgram
├─components        # 自定义组件
│  └─my-card
├─dist              # ivew UI组件库
├─images
├─libs
├─miniprogram_npm   # npm 第三方包
│  └─vant-weapp     # vant UI组件库
├─pages             # 页面文件
│  ├─index
│  ├─login
│  ├─logs
│  ├─mine
│  ├─newtask
│  ├─register
│  └─task
├─style             # weui官方样式库
└─utils             # 工具函数
```

#### 2.2 后端
```
Server
├─config            # 读取并解析配置文件
├─controllers       # 路由处理函数
│  ├─ad
│  ├─resource
│  ├─task
│  └─user
├─database          # 数据库初始化
├─middlewares       # 中间件
│  ├─auth           # 鉴权
│  ├─cache
│  ├─logger
│  └─session
├─models            # 数据模型
│  ├─ad
│  ├─campus
│  ├─common
│  ├─school
│  ├─tag
│  ├─task
│  └─user
├─modules           # 功能模块
│  ├─gredis
│  ├─log
│  └─util
├─router            # 路由
└─storage           # 存储
    └─logs
    └─upload
```

### 3. BCE

- Boundary：与用户的接口，如：界面、网关、代理等。用来隔离系统，通常负责接收并响应系统内外的消息。参与者只能与边界对象互动，不能直接发送消息给控制对象或实体对象。
- Controller：在 Boundary 和 Entity 中衔接的媒介，处理来自 Boundary 的交互请求。
- Entity：代表系统数据，如：用户、任务、资源等。用来保存问题领域的重要信息，封装了跟数据结构和数据存储有关的变化。


---

Boundary 包含：

- 客户端小程序用户界面
- 服务端 Nginx 反向代理服务器

Controller 包含：

- 负责用户管理的 Controller。
- 负责任务管理的 Controller。
- 负责资源管理的 Controller。
- 负责广告管理的 Controller。

Entity 包含：

- 用户数据模型。
- 任务数据模型。
- 广告数据模型。
- 资源类数据模型（如校区、学院等）。
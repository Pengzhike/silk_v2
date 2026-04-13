# CI 快速验证功能树

```text
Silk
├─ 工程与产物
│  ├─ Gradle 根工程可配置
│  ├─ backend JVM 编译 / 单测 / shadowJar 打包
│  ├─ webApp 生产编译产物
│  ├─ desktopApp 编译
│  ├─ androidApp Debug 编译
│  ├─ harmonyApp HAP 构建
│  ├─ backend/static 承接 Web / APK / HAP 产物
│  └─ nginx 同源静态部署配置生成
├─ 用户与设置
│  ├─ 注册
│  ├─ 登录
│  ├─ 用户有效性校验
│  ├─ 会话恢复与重新校验（Web / Android）
│  ├─ 用户语言设置读取
│  ├─ 用户语言设置更新
│  └─ 默认 Agent 指令读取 / 更新
├─ 群组与联系人
│  ├─ 创建群组
│  ├─ 通过邀请码加入群组
│  ├─ 获取用户群组列表
│  ├─ 获取群详情
│  ├─ 获取群成员
│  ├─ 邀请信息生成与复制（邀请码 / 完整邀请文案 / APK 与 Web 链接）
│  ├─ 添加成员到群组
│  ├─ 退出群组
│  ├─ 群主删除群组
│  ├─ 群删除前聊天历史备份
│  ├─ 联系人列表与待处理请求
│  ├─ 通过手机号搜索用户
│  ├─ 通过手机号发起联系人请求
│  ├─ 通过用户 ID 发起联系人请求
│  ├─ 接受 / 拒绝联系人请求
│  ├─ 与联系人开启私聊会话
│  └─ 开启 [Silk] 专属私聊会话
├─ 实时聊天与消息语义
│  ├─ WebSocket 连接鉴权（非群成员禁止进入）
│  ├─ 进入会话时加载最近历史消息
│  ├─ 普通文本消息发送与广播
│  ├─ 客户端乐观发送与重复消息去重
│  ├─ 聊天历史持久化与重连恢复
│  ├─ 未读消息统计
│  ├─ 标记群组已读
│  ├─ 单条消息复制
│  ├─ 单条消息转发到其他群
│  ├─ 单条消息转发到联系人私聊
│  ├─ 批量消息合并复制 / 转发（Harmony）
│  ├─ 撤回本人消息
│  ├─ 撤回 @silk 消息时连带撤回 AI 回复
│  ├─ 转发消息卡片解析与展示
│  └─ 跨天时间显示
├─ AI / Silk / Claude Code
│  ├─ 普通群仅 @Silk / @silk 触发 AI
│  ├─ [Silk] 专属私聊中直接触发 AI
│  ├─ 空 @silk 帮助提示
│  ├─ 角色设定写入
│  ├─ 角色重置
│  ├─ 流式增量输出
│  ├─ 最终消息落库
│  ├─ Agent 状态消息广播与清空
│  ├─ 普通群上下文隔离（仅当前群）
│  ├─ [Silk] 私聊跨用户所属群上下文
│  ├─ 群成员信息注入 AI 上下文
│  ├─ AI 工具：search_context
│  ├─ AI 工具：search_files
│  ├─ AI 工具：search_web
│  ├─ AI 工具：read_file
│  ├─ AI 工具：execute_command
│  ├─ AI 工具：get_group_stats
│  ├─ AI 工具策略加载 / 权限校验 / 审计
│  ├─ OpenAI-compatible tool_call 请求兼容与参数修复
│  ├─ Claude Code /cc 进入 / 退出
│  ├─ Claude Code 新会话 / 恢复会话 / cd / queue / cancel / status
│  ├─ Claude Code 会话持久化与按用户隔离
│  └─ Claude Code stream-json 解析（text / tool_use / tool_result / compact / result）
├─ 文件 / URL / 索引 / APK
│  ├─ 文件上传
│  ├─ 重名文件自动改名
│  ├─ 上传后广播文件消息到群
│  ├─ 文件下载
│  ├─ 文件列表与文件夹浏览
│  ├─ 文件删除
│  ├─ URL 自动识别
│  ├─ 网页 / PDF 下载抽取
│  ├─ processed_urls 去重缓存
│  ├─ 文件索引状态广播
│  ├─ Weaviate 就绪检查
│  ├─ 聊天消息索引到 Weaviate
│  ├─ 上传文档索引到 Weaviate
│  ├─ Weaviate Schema 初始化（search/schema.py）
│  ├─ chat_history 增量索引（search/indexer.py）
│  ├─ 文件重建索引（backend/reindex-files.sh / search/reindex_files.py）
│  ├─ PDF 重建索引（backend/reindex-pdf.py）
│  ├─ APK 版本信息接口
│  ├─ APK 下载接口
│  ├─ Web 拖拽上传 / 文件上传 / 文件夹上传
│  └─ Android 文件上传 / 文件浏览 / 外部打开下载文件
├─ 待办 / 日历 / Harmony 专属执行链路
│  ├─ 获取用户待办
│  ├─ 同步刷新跨群待办
│  ├─ 异步刷新启动
│  ├─ 异步刷新状态查询
│  ├─ 待办抽取诊断信息
│  ├─ 更新待办
│  ├─ 删除待办
│  ├─ 聊天记录抽取待办
│  ├─ 待办去重（逻辑键合并）
│  ├─ 长期模板 / 短期实例生命周期
│  ├─ 周期模板实例化
│  ├─ 已完成 / 已取消 / 延后待办重开规则
│  ├─ 工作日查询
│  ├─ Harmony 待办页缓存加载 + 后台轮询刷新
│  ├─ Harmony 待办执行为系统闹钟
│  ├─ Harmony 待办执行为周期闹钟
│  ├─ Harmony 待办执行为日历事件
│  ├─ Harmony 待办撤销执行
│  ├─ Harmony 系统侧对账恢复待办状态
│  └─ Harmony 购物意图解析与外部搜索拉起
├─ 多端客户端表现
│  ├─ Web 登录 / 群组 / 联系人 / 设置 / 聊天场景切换
│  ├─ Web Markdown / 表格 / 代码高亮 / KaTeX 渲染
│  ├─ Android 登录 / 群组 / 设置 / 聊天场景切换
│  ├─ Android WebSocket 前台服务保活
│  ├─ Android Markdown WebView + KaTeX 渲染
│  ├─ Android 版本检查 / APK 下载 / 安装拉起
│  ├─ Harmony 登录注册 / 快捷登录 / 群组 / 设置 / 聊天 / Todo 场景切换
│  ├─ Harmony MarkdownLite / MarkdownWeb / 离线 KaTeX 渲染
│  └─ Desktop 登录 / 群组 / 设置 / 邀请对话框基础编译守护
├─ 部署与运维脚本
│  ├─ .env 加载与端口推导
│  ├─ 本地 / 远程 Weaviate 模式判断
│  ├─ silk.sh build / build-apk / build-hap / build-all
│  ├─ silk.sh start / stop / restart / status / logs
│  ├─ silk.sh weaviate start / stop / status / schema
│  ├─ nginx 配置生成与同源代理
│  └─ APK / Web / HAP 产物发布到 backend/static
└─ 最适合优先落入 CI 的快检基线
   ├─ :backend:test
   ├─ :frontend:webApp:compileProductionExecutableKotlinJs
   ├─ :frontend:desktopApp:compileKotlin
   ├─ :frontend:androidApp:compileDebugKotlin
   ├─ Harmony HAP build
   ├─ backend 核心 HTTP 合同测试
   ├─ WebSocket 消息语义测试
   ├─ AI 工具与作用域测试
   ├─ Claude Code 解析 / 会话存储单测
   ├─ Todo 存储 / 去重 / 生命周期单测
   └─ silk.sh 脚本级 smoke test
```

## CI 落地进度（2026-04-13）

已新增 GitHub Actions workflow：`.github/workflows/ci-fast-validation.yml`

触发器：
- `push`
- `pull_request`
- `merge_group`
- `workflow_dispatch`

本次已落地：
- [x] `:backend:test`
- [x] `:frontend:webApp:compileProductionExecutableKotlinJs`
- [x] `:frontend:desktopApp:compileKotlin`
- [x] `:frontend:androidApp:compileDebugKotlin`
- [x] Claude Code 解析 / 会话存储单测

本次明确未覆盖：
- [ ] Harmony HAP build
- [ ] backend 核心 HTTP 合同测试
- [ ] WebSocket 消息语义测试
- [ ] AI 工具与作用域测试
- [ ] Todo 存储 / 去重 / 生命周期单测
- [ ] `silk.sh` 脚本级 smoke test

备注：
- `:backend:test` 当前覆盖的现有单测主要是消息复制 / 转发 / 撤回，以及 Claude Code 的 stream parser / session store；还不是 backend HTTP / WebSocket 的合同级验证。
- Android 这条在无 SDK 环境下会直接失败，CI 已显式准备 Android SDK 并生成 `local.properties`。
- Gradle wrapper 当前仓库配置使用腾讯镜像；CI 在 GitHub-hosted runner 上会临时改用 `services.gradle.org`，避免外网可达性导致的非业务失败。
- Harmony HAP 构建依赖 DevEco / hvigor / ohpm，更适合下一步放到自托管 runner 或预置 Harmony 环境的 runner。

## 下次继续的起点

建议按这个顺序继续补：

1. backend 核心 HTTP 合同测试
2. WebSocket 消息语义测试
3. AI 工具与作用域测试
4. Todo 存储 / 去重 / 生命周期单测
5. `silk.sh` 脚本级 smoke test
6. Harmony HAP CI 方案（大概率需要单独 runner）

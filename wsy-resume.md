<style>
  /* 
    =======================================================================
    高级设计师与招聘官心理学主题样式 (Designer & Recruiter Psychology Theme)
    =======================================================================
  */
  :root {
    --primary-color: #1d4ed8; /* 科技感深蓝色，传递专业、稳重的职业形象 */
    --text-main: #0f172a; /* 极深的石板灰，接近纯黑，确保在白底上具有极佳的对比度与清晰度 */
    --text-muted: #334155; /* 辅助文字颜色，调深以确保清晰可读 */
    --bg-card: #f8fafc; /* 极轻的灰色背景，用于信息卡片 */
    --border-color: #cbd5e1; /* 细腻的分割线颜色，稍微加深以确保导出时可见 */
  }

  /* 
    强制在打印和导出时使用高对比度浅色模式，
    彻底解决因系统/导出工具深色模式偏好导致的“白底白字”看不清的 Bug。
  */
  @media print {
    :root {
      --primary-color: #1d4ed8 !important;
      --text-main: #0f172a !important;
      --text-muted: #334155 !important;
      --bg-card: #f8fafc !important;
      --border-color: #cbd5e1 !important;
    }
    body {
      background-color: #ffffff !important;
      color: #0f172a !important;
      padding: 10px 25px !important; /* 打印时进一步缩小上下留白 */
    }
    /* 避免标题和列表项在分页处被尴尬截断 */
    h2, h3 {
      break-after: avoid !important;
      page-break-after: avoid !important;
    }
    li {
      break-inside: avoid !important;
      page-break-inside: avoid !important;
    }
  }

  body {
    max-width: 800px !important;
    margin: 0 auto !important;
    padding: 15px 35px !important; /* 缩小上下和左右留白，使排版更紧凑 */
    line-height: 1.42 !important; /* 紧凑的黄金阅读行高，既不空旷，也不拥挤 */
    letter-spacing: 0.02em !important; /* 适度呼吸感字距 */
    font-size: 13px !important; /* 稍微缩小字号，确保两页容纳 */
    color: var(--text-main) !important;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", sans-serif !important;
    text-align: justify !important; /* 两端对齐，排版更整齐 */
  }

  /* 个人信息卡片化：用户心理学中的“首因效应”，第一眼建立精细、有条理的专业印象 */
  .profile-card {
    background: var(--bg-card) !important; /* 极轻的灰色背景，用于信息卡片 */
    padding: 8px 14px !important; /* 缩小内边距，使卡片更紧凑 */
    border-radius: 6px !important;
    border-left: 4px solid var(--primary-color) !important; /* 科技感深蓝色 */
    margin-top: 8px !important;
    margin-bottom: 10px !important; /* 缩小外边距 */
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.02) !important;
    display: flex !important;
    flex-direction: column !important;
    gap: 4px !important; /* 每一行之间有优雅的间距 */
  }

  .profile-line {
    line-height: 1.4 !important;
    font-size: 13px !important;
    color: var(--text-muted) !important; /* 优雅的辅助文字颜色 */
  }

  .profile-line strong {
    color: var(--text-main) !important;
    font-weight: 700 !important;
  }

  /* 列表项间距与定制化：消除默认列表的廉价感 */
  li {
    list-style-type: none !important;
    position: relative !important;
    padding-left: 18px !important;
    margin-bottom: 4px !important; /* 大幅缩减列表项之间的下边距，解决段落高度太高的问题 */
    line-height: 1.42 !important;
    font-size: 13px !important;
    color: var(--text-main) !important;
  }

  /* 极简主义圆点，代替粗糙的默认黑点 */
  li::before {
    content: "" !important;
    position: absolute !important;
    left: 0 !important;
    top: 6px !important; /* 配合行高微调圆点位置 */
    width: 5px !important;
    height: 5px !important;
    background-color: var(--primary-color) !important;
    border-radius: 50% !important;
    opacity: 0.8 !important;
  }

  /* 标题艺术设计 */
  h1 {
    font-size: 1.8rem !important; /* 稍微缩小标题，使其更精致 */
    font-weight: 800 !important;
    letter-spacing: 0.05em !important;
    margin-top: 0 !important;
    margin-bottom: 6px !important;
    border-bottom: unset;
    color: var(--text-main) !important;
  }

  h2 {
    font-size: 1.15rem !important; /* 稍微缩小二级标题 */
    font-weight: 700 !important;
    margin-top: 12px !important; /* 大幅缩小上边距 */
    margin-bottom: 6px !important; /* 大幅缩小下边距 */
    padding-bottom: 4px !important;
    border-bottom: 2px solid var(--border-color) !important;
    letter-spacing: 0.03em !important;
  }

  h3 {
    font-size: 1rem !important;
    font-weight: 700 !important;
    margin-top: 8px !important;
    margin-bottom: 4px !important;
    color: var(--text-main) !important;
  }

  p {
    margin-top: 2px !important;
    margin-bottom: 4px !important;
    line-height: 1.42 !important;
  }

  ul, ol {
    margin-top: 2px !important;
    margin-bottom: 4px !important;
    padding-left: 0 !important;
  }

  /* 
    视觉锚点优化：招聘官（HR/架构师）在扫视简历时，视线会自动寻找粗体。
    我们将项目标题保持稳重，而将后面的“核心成果/数据”用微光高亮包裹，
    形成极佳的视觉引导，瞬间抓住核心价值。
  */
  li > strong:first-child {
    font-size: 13px !important;
    color: var(--text-main) !important;
    font-weight: 700 !important;
  }

  li strong:not(:first-child) {
    padding: 1px 5px !important;
    border-radius: 3px !important;
    font-weight: 600 !important;
    letter-spacing: 0.01em !important;
  }

  /* 优雅的虚线分割 */
  hr {
    margin: 10px 0 !important; /* 大幅缩小分割线上下边距 */
    border: none !important;
    border-top: 1px dashed var(--border-color) !important;
  }
</style>

# 申月

<div class="profile-card">
  <div class="profile-line"><strong>求职意向：</strong>中级前端A / 前端架构师</div>
  <div class="profile-line"><strong>个人信息：</strong>27 岁 | 男 | 5 年经验 | 本科</div>
  <div class="profile-line"><strong>联系方式：</strong>17357274166 | 296717574@qq.com</div>
</div>


## 个人优势

- **大型核心平台架构经验：** 主导十万级 DAU 高可用架构演进与技术选型，擅长平衡业务、效率与成本。
- **中大型团队合作与中台统筹：** 擅长从 0 到 1 构建高效研发体系，推进跨部门协同与创新。
- **精通 Vue/React 生态与 Monorepo 工程治理：** 具备全栈研发视野及高标准公共资产沉淀能力。
- **紧跟 AI 发展前沿：** 主导 AI 全链路辅助开发流与工程化落地，技术驱动团队生产力跨代升级。

## 工作经验

**深圳尚米网络技术有限公司珠海分公司** &nbsp;|&nbsp; **中级工程师 / 前端架构师** &nbsp;|&nbsp; **2022-03 ~ 至今**

### 业务

* **C端游戏平台增长闭环：** 负责十万级 DAU 级游戏平台的多端（移动 / PC 官网、App / SDK 内嵌页）用户增长体系建设，全链路攻坚群聊、直播、交易、云挂机、全球化支付、多语言等核心业务模块的建设与持续迭代，支撑业务高效转化。

* **B端游戏运营平台中台化：** 负责游戏全生命周期运营支撑平台的建设，实现游戏管理、活动配置、礼包码、风控审核、多语言翻译及商务 / 投放数据可视化等 20+ 复杂业务场景的高效流转，完善平台运营支撑闭环。

* **PC端混合渲染服务平台：** 独立主导多项目、多形态游戏官网、详情页及游戏社区建设。基于 Nuxt3 / Vue3 混合渲染方案，跑通包含云游戏、在线玩、用户中心、工单反馈等重交互与强 SEO 并存的核心链路。

* **自研客服生态全栈落地：** 负责集团自研客服体系从 0 到 1 的整体落地，全面覆盖 C 端嵌入式客服 SDK、客服工作台、管理后台及运营配置中心，全功能支持 IM 长连接会话、机器人智能规则转人工、敏感词过滤及复杂工单流转。

* **AI视频智能切片工具（全栈研发）：** 独立负责内部 AI 视频工具的全栈设计与研发。前端采用 React + TypeScript 构建复杂画布与媒体项目管理；后端基于 FastAPI + SQLite + Redis / Celery 实现高并发异步任务调度；自研多模型调用与 Prompt 编排，无缝串联字幕解析、片段评分与 FFmpeg 自动化成片。

---

### 架构

* **【AI 辅助开发（Vibe Coding）】** 主导团队 AI 辅助开发工程化落地。基于 Cursor / Codex 自研多套 Skills 编排体系，并打通 APIFOX、蓝湖、浏览器自动化测试三类 MCP（Model Context Protocol），将 AI 产出从“随机问答”收敛为可复用、可验收、符合严苛编码规范的标准交付流，**实现团队标准业务模块研发效率的成倍提升**。

* **【全球化支付收银台】** 设计国内外多端支付收银台拓扑架构。基于 SSR 实现用户态恢复与支付渠道动态编排；自研“客户端用户信息注入 + Cookie 持久化 + 服务端请求头回填”机制，**彻底解决 App / SDK 内部页面跳转导致登录态丢失的行业硬伤**；配合网关层实现多商户主体（深圳 / 香港）的支付隔离。

* **【高性能直播间系统】** 设计移动端直播间前端分层架构（播放器适配层 + 业务容器 + 互动组件层）。通过 CommonLivePlayer 统一封装阿里云与火山引擎播放器差异，向上提供标准原子能力；业务容器层统一收敛全生命周期状态机；互动组件层通过插件化承载聊天、弹幕、礼物、福袋、购物车等高频交互，**最大程度降低多播放器、多场景下的耦合度**。

* **【群聊 IM 分层架构】** 针对海外群聊消息来源多、长列表渲染压力大、翻译链路复杂的极端场景，设计移动端群聊分层架构（会话状态层、消息加载层、消息进站管线、消息渲染层、业务互动组件层）。通过状态集中管理与消息进站管线编迎，统一承载首屏初始化、历史分页、上拉补齐及自动翻译等能力，使单一种 IM 会话蜕变为聚合游戏社区、交易转化和直播引流的复合入口。

* **【全球化（i18n）基础设施】** 设计跨多项目、多渲染模式的前端多语言架构。针对存量 Vue 项目支持全量语言包平滑接入；针对 Next.js / Nuxt 等 SSR 页面，采用“按需模块字典拆分 + 服务端渲染前精准加载”策略，**阻止无关语种文件进入首屏链路，完美统一浏览器、App、时区和服务端接口的语言上下文**。

* **【混合渲染与动态预渲染 SEO】** 推动 PC 官网从传统 SPA 向 Nuxt3 / Vue3 混合渲染架构升级，针对强 SEO 页面采用 SSR，重交互页面采用 SPA。同时，针对无法重构的旧 SPA 项目，落地动态预渲染 SEO 方案，基于 Nginx 精准识别搜索引擎爬虫 UA 并转发至自建 Prerender 服务，通过 Headless Chrome 执行路由与接口并生成静态 HTML 快照，**完美解决纯 SPA 动态数据对爬虫不可见的问题**。

* **【多应用 Monorepo 业务中台】** 设计面向客服全生态（工作台、后台、C 端、桌面端）的 Monorepo 前端架构。将 IM 会话、领域模型、通用表单等高频能力抽离为核心插件，结合 pnpm workspace 与 Turborepo 构建编排，实现多应用依赖治理、工程多环境构建与增量缓存，**使中大型系统全量构建速度提升 3 倍以上**。

* **【客服消息领域 SDK】** 基于 WuKongIM 自研客服消息领域 SDK，面向业务语义重的 IM 场景，构建统一消息领域模型和生命周期管线。通过消息类型注册、泛型消息工厂、本地消息占位与命令消息分发机制，将底层 IM 通信能力封装为高内聚的业务领域层。

---

### 技术

* **【支付风控与状态闭环】** 落地海外多渠道支付安全校验，无缝兼容 PayPal、MyCard、国际支付宝、Lakala 等主流渠道的币种、费率及跳转差异；接入实名、年龄、国际信用卡风控 / 人机验证等多重拦截，通过跨页面刷新与订单状态轮询机制，**确保全球高并发、复杂网络环境下的支付结果强一致性**。

* **【跨端统一通信】** 设计并落地 WebBridge 跨端通信架构，标准化 H5、App、SDK、PC Web 与客户端之间的调用模型，完美屏蔽 Android、iOS 与普通浏览器底层能力差异，平滑支撑登录态同步、支付唤起、设备特征获取等高频跨端诉求。

* **【直播低延迟与体验榨干】** 落地低延迟直播播放优化，支持 RTS 转码流、多清晰度无缝切换及断流自动重拉；通过点赞行为高频节流、礼物资源 Blob 预加载、SVGA / VAP 复杂动效高性能播放，**确保直播间在移动端高频互动与复杂支付并发场景下的极致流畅度，卡顿率降低 60%**。

* **【群聊高性能虚拟渲染】** 落地群聊长会话高性能渲染方案。基于自定义虚拟列表承载长会话，实现上拉补齐、滚动位置精准恢复及目标消息定位；渲染前置完成连续消息头像折叠、回复引用预检和图片尺寸预加载，**彻底根治移动端长列表高度闪烁与抖动问题，滑行帧率稳定在 55+ FPS**。

* **【海外群聊秒级翻译】** 落地海外群聊自动翻译技术方案。支持单次最多 50 条批量翻译、MD5 分片匹配及 MQTT 晚到译文异步回填；引入 IndexedDB 实现 7 天本地缓存与失败兜底标记，**首屏翻译呈现速度提升 40%，并大幅削减 50% 以上的重复翻译接口成本**。

* **【长连接硬核自愈（Monkey Patch）】** 针对客服工作台在断网、弱网、系统后台等极端场景下出现的重连锁死、事件重复触发问题，**利用 Monkey Patch  硬核重写连接管理器核心底层方法**；通过引入单重连定时器、旧 WebSocket 实例强释放、重连前状态归零机制，建立前端侧长连接自恢复网，**客服断线率与漏消息率实质性清零**。

* **【实时状态竞态仲裁】** 针对实时客服会话中 IM Push、HTTP 摘要、排队轮询等多源状态引发的竞态冲突，通过临时会话占位、频道去重、lastMessage 时间戳仲裁及本地进入态 Set 记忆策略，将复杂状态收敛为可预测的单向状态流，**彻底杜绝消息倒序、重复会话与未读状态回退异常**。

* **【跨窗口 RPC 通信机制】** 针对 Electron 桌面端工作台与 AI 助手独立窗口之间的上下文隔离与协同盲区，基于 Electron IPC 设计了多窗口 RPC 通信机制。主进程维护窗口注册表与 requestId 超时回收，渲染进程通过 contextBridge 暴露受控 API，实现 AI 助手跨窗口精准采集上下文、流式生成（SSE）并将安抚话术一键回填输入框，**打通可追踪、可控制的跨窗口业务闭环，客服日均接待效率大幅飙升**。

* **【二次封装组件库】** 设计公共组件库实例代理机制。基于 h() 渲染代理、ref 转发以及 vm.exposed 重写，**在 14 个高频组件二次封装场景下，完美保留底层原子组件 API 的 100% 可达性**，破除了“封装增强”与“原子能力保真”难以兼得的行业瓶颈。

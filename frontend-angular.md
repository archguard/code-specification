### 前端代码分层

- 分层设计
   - API 层：以 ng 的 Service 体现，根据后端的 API 划分，负责发送 Socket 消息、Rest 请求。以后可以根据 swagger 生成该层。
   - Business 层: 以 ng 的 Service 体现，根据领域资源或者独立的职责划分, 处理具体业务逻辑，与场景无关，提供通用的方法和全局状态。
      - 全局的兜底错误处理
   - Page 层：以 ng 的 Component 体现，复杂业务可以增加 PageServcie，负责当前业务逻辑和当前路由的局部状态。PageService 可选和 PageComponent 一一对应，如果简单业务可以直接将 PageService 和 PageComponent 合并。
      - 局部的错误处理
      - 数据整理，如格式化过滤等

- 组件设计，组件分为：**Page 组件、业务组件、UI 组件**

   - Page 组件负责承载路由，每个路由必须对应一个 Page 组件
   - 当 Page 组件过大时，可以拆分为业务组件，例如弹窗，业务组件的数据输入必须来自于 Page 组件。业务组件最多两层。避免依赖 service 和其中的数据。
   - UI 组件为无状态、可复用的纯交互组件，通过事件和 input 做数据通信。**禁止依赖 service 和其中的数据。**

- 路由设计
   - 路由层级不超过 3 层
- Rxjs
   - 不使用 promise
   - 及时取消订阅

### 命名和风格

- 文件夹必须使用中横线命名，不使用驼峰
- svg 文件需要使用 svgo 做处理，然后修改 fill 属性为 currentColor 满足 css 颜色要求
- 避免在 targetUri 中使用 %

### 样式规范

- 所有颜色必须使用设计系统中的值
- 不使用 important
- 不使用行内样式
- 嵌套层次不超过 3 层
- 字重 `font-weight` 先不要用纯数字，直接使用 `bold` or `normal`

### 其他规范

- 无用代码应该直接删除,不要直接注释后提交到代码库

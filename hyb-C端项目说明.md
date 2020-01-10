# 前端整体功能

[中文] / [English]

- :speech_balloon: 多语言
- :warning: 表单验证
- :truck: vuex
- :link: 路由器（部分登录验证服务，需要跟后端api对接）
- :ok_hand: API服务 (正在开发)
- :fax: SSR nuxt 服务器端渲染 (接下去需要完成)

## 开发环境

- 系统 : Nodejs
- 依赖管理: NPM


## 项目结构

```
.
├── build                           # 自动构建模块
│   ├── webpack.prod.conf.js        # webpack 生产环境设定
│   ├── webpack.dev.conf.js         # webpack 开发环境设定
│   └── build.js                    # 生产流程
├── config                          # 自动构建设定模块
├── src                             # 程序入口
│   ├── assets                      # 资源文件
│   │   ├── fonts/                  # 文字
│   │   └── images/                 # 图片
│   ├── i18n                        # 多语言模块
│   ├── routes                      # 总路由器 (所有路由都在这里引入)
│   ├── services                    # 业务服务模块
│   ├── stores                      # vuex模块 (所有页面及部件store模块都在这里引入)
│   ├── stylesheet                  # 样式模块 (公共样式)
│   ├── utils                       # 其他工具
│   ├── view                        # 程序页面
│   │   ├── Global                  # 公共页面
│   │   │   └── Component           # 页面模块 - 包含以下
│   │   │       ├── i18n            # 多语言内容
│   │   │       ├── route           # 路由设定
│   │   │       ├── store           # 数据store模块
│   │   │       ├── **              # 其他内容
│   │   │       └── index.vue       # 模块入口
│   │   └── Pages                   # 程序主页面
│   │       └── Component/**        # 页面模块(参考公共页面)
└── static                          # 静态文档
└── test                            # 测试模块文件 - 分单元测试与端测试
```


## 构建命令

``` bash
# 安装依赖
npm install

# 在开发环境下运行程序 localhost:8080
npm run dev

# 程序生产
npm run build

# 程序测试, 也可以单独运行npm run unit 或者 npm run e2e
npm run test

# 程序生产，并生产程序打包报告
npm run build --report
```

## 证书
This project is licensed under the MIT License


[中文]: https://bitbucket.org/yellowrush888/demo/src/master/README.md "中文"

[English]: https://bitbucket.org/yellowrush888/demo/src/master/README_en.md "English"


# noah 组件名
- TopUp   充值
- DrawMoney 提现
- FindPass  找回密码
- InternationalCode  选择国际区号
- SuccessPopUp    成功提现的弹窗 
- AddCard     新增银行卡
- RetrieveTradingPassword 找回交易密码
- transfer 转账
- credits exchange 弘币兑换
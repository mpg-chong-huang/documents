## 功能

```
- 登录 / 注销

- 权限验证
  - 页面权限
  - 指令权限
  - 二步登录

- 多环境
  - dev 开发环境
  - sit 测试打包
  - stage
  - prod 生产打包

- 全局功能
  - 多语言 (虽然好像不是很需要的样子)
  - 多种动态换肤
  - 动态侧边栏 (支持多级路由嵌套)
  - 动态当前页面链接
  - 快捷导航 (有标签可以切换，感觉说不定会加上)
  - Svg Sprite 图标 (之前的webfont管理起来比较麻烦，想着想着就换这个了)
  - 本地mock数据 (这个不会用可以先不管，在vue里面绑数据
  - Screenfull全屏
  - 自适应收缩侧边栏

- 编辑器
  - 文本
  - Markdown
  - JSON 等多格式

- Excel
  - 导出excel
  - 导出zip
  - 导入excel
  - 前端可视化excel

- 表格
  - 动态表格
  - 拖拽表格
  - 树形表格
  - 内联编辑

- 错误页面 (这两个都是偷别人的，拿到后可以尽快改图片)
  - 401
  - 404

- 組件
  - 头像上传
  - 返回顶部
  - 拖拽Dialog
  - 拖拽Select
  - 拖拽看板
  - 列表拖拽
  - SplitPane
  - Dropzone
  - Sticky
  - CountTo

- 编辑文章
- 错误日志 (错误抓取部分还正在开发中)
- Dashboard
- 引导页
- ECharts 图表
- Clipboard (剪贴复制)
- Markdown2html
- 这里如果有想到其他的功能再加
- ...
```

## 开发环境

- 系统 : win10 pro,  Nodejs 版本v8.9.1
- 依赖管理: NPM 版本 5.6.0
- 备份资料请记得不要保存在项目内！备份资料请记得不要保存在项目内！备份资料请记得不要保存在项目内！

## 项目结构

対応中

## 构建命令

``` bash
# 安装依赖
npm install

# 在开发环境下运行程序 localhost:9527
npm run dev

```

## 发布命令

```bash
# 构建测试环境
npm run build:sit

# 构建生产环境
npm run build:prod
```

## 分析命令

```bash
# --report to build with bundle size analytics
npm run build:prod

# --generate a bundle size analytics. default: bundle-report.html
npm run build:prod --generate_report

# --preview to start a server in local to preview
npm run build:prod --preview
```

## 证书

This project is licensed under the MIT License

## api对接模块

- http通信模块

所在路径: .src/api/里面

参考文件: role.js ----- 基础方法get post put delete

参考格式: 

```bash
// 公共request模块，封装好的http请求模块
import request from '@/utils/request'
// 如果需要post application/x-www-form-urlencoded类型需要引用qs库
import qs from 'qs'

// application/json请求（默认）
export function JSON方式函数名(data) {
  return request({
    url: '/请求路径',
    method: '请求方式',
    data // 传参
  })
}
* 备注此处的data不用进行json化，直接传递对象object类型都可以比如
{
  username: 'abc',
  password: '123123'
}

// form-data请求
let data = new FormData();
data.append('username','abc');
data.append('password','123');
* 备注以上的赋值之类的操作在元件内部获取然后传参给下面的函数·

export function FORM方式函数名(data) {
  return request({
    url: '/请求路径',
    method: '请求方式',
    data // 传参
  })
}

// application/x-www-form-urlencoded请求
export function URLENCODE方式函数名(data) {
  return request({
    url: '/请求路径',
    method: '请求方式',
    qs.stringify({ data }) // 传参，请确保qs库引用
  })
}

```


- 数据初始化

所在路径: .src/store/module/里面

全局引入: .src/store/index.js    * 备注在module里面初始化完之后需要引入到这里的index.js

参考文件: errorLog.js

state - 实际数据

getter - 可供全局访问的数据

action - 全局声明函数

mutation - 根据声明函数来相应的做state实际数据更新

参考格式: 

```bash
  namespace: false(默认) / true, //这里是一个命名空间化的标识，当为true的时候可以防止state里面的数据名冲突，让整体带有命名空间
  state: {
    data: 1  // 这里初始一个数据 1
  },
  getters: {
    getData: state => {
      return state.data  // 这里通过getData的函数获取数据 data
    }
  },
  actions: {
    addToData({ commit }, 2) {
      commit('ADD_TO_DATA', 2) // 这里初始化addToData的声明函数，并传递2给这个声明函数
    }
  },
  mutations: {
    ADD_TO_DATA: (state, res) => {
      state.data += res // 声明函数的处理函数，接受到来自声明函数的addToData的参数之后，如何更新data的数据，在这里就单纯的加上去
    }
  }

```

- 数据绑定

所在路径: .src/里面所有需要引用数据的元件

参考格式: 

以下是vue元件内部的script标签，需要访问数据的地方
```bash
<script>
import { mapGetters } from 'vuex';
export default {
  
  // 单纯需要获取数据
  computed: {
    // 没有命名空间的引用方式
    ...mapGetters([
      'data',
    ]),
    // 带初始化命名空间的引用方式
    ...mapGetters('命名空间名称', [
      'data',
    ]),
  },
  
  // 需要调用action的声明函数addToData
  methods: {
    add2ActionData() {
      this.$store.dispatch('addToData', 2)
    },
  },
  
}
```


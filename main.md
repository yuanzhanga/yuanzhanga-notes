import App from './App.vue';              // 根组件
import store from './store';              // Vuex状态管理
import router from './router';            // Vue Router路由
import './permission';                    // *权限控制模块

样式导入
ssc-ui-vue

import {
  WmsTable,      // WMS表格组件
  SFilter,       // 筛选组件
  WmsButton,     // WMS按钮组件
  CustomHooks,   // 自定义Hooks组件
  CreateForm,    // 表单创建组件
  Action,        // 操作组件
} from '@/components/index';//公共组件导入
用于注册组件

工具和指令导入
utils//全局方法挂载
directives//用于注册指令

国际化导入
i18n
import { gt } from './i18n';// 翻译函数

国际化插件
SSC UI组件配置

监控集成: 集成链路追踪、覆盖率报告等监控服务
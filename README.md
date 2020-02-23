初始化vue项目

vue create demo

安装组件库

yarn add ly-ui

全局导入

import LyUI from 'ly-ui' 
import 'ly-ui/lib/ly.css'

Vue.use(LyUI)

使用组件

显示登录框 男 女 登录 取消
常见组件封装

button组件


参数名 参数描述 参数类型 默认值
type 按钮类型(primary / success / warning / danger / info) string default plain 是否是朴素按钮 boolean false
round 是否是圆角按钮 boolean false
circle 是否是圆形按钮 boolean false
disabled 是否禁用按钮 boolean false
icon 图标类名 string 无

事件支持

事件名 事件描述 click 点击事件
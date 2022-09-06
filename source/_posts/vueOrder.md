---
title: VUE 常用命令
date: 2022-09-06 10:31:18
tags:
- VUE 命令
categories: 
- VUE
top_img: /img/cover3.jpg
cover: /img/cover3.jpg
---
## start cmd
vue create+名称   //创建新的vue项目
npm run serve //运行Vue项目

## axios
npm install --save axios vue-axios  //npm窗口运行 下载axios
引入main.js文件 
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios, axios)

## 下载element
npm i element-ui -S npm窗口运行
引入main.js文件
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
Vue.use(ElementUI);

## vue全屏组件screenfull
npm install --save screenfull@4.2.1 npm窗口运行
安装node_modules模块
npm install npm窗口运行

## 卸载依赖
npm uninstall 依赖名称 -dev

## vuex状态管理模式
集中式存储管理应用的所有组件的状态
npm install vuex --save npm窗口运行
引入main.js文件
import Vue from 'vue'
import Vuex from 'vuex'

## Vue.use(Vuex)
五大状态
state           状态数据
getters    获取数据
mutations   提交改变 同步
actions    异步提交数据
modules    模块化
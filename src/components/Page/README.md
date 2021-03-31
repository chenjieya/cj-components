# 分页组件
```
整理代码
npm run lint
```

```
运行测试（快速原型开发）
npm install -g @vue/cli-service-global
npm run test:page
```

```

传递参数：
1. cjLimt       每一页有多少条数据（默认10）        Number
2. cjIsborder   是否显示边框（默认true）             Boolean
3. cjTotal      总数据                   Number
4. cjCurrent    当前的页码               Number
5. cjPage       页面中显示多少个数字      Number
6. cjContainerWidth 页面容器的宽度（默认600）       Number

事件：
changePage     接受一个参数（新的页码数）  fucnction(newPage){}
```


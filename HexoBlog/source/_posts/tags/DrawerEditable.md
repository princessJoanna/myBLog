---
title: DrawerEditable
date: 2019-07-08 14:09:17
tags: 组件
---
改组件使用场景，是带表身的订单的整单编辑，点击当前单元格可以编辑，失去焦点只读，记录每一行的新增，删除或者修改属性，
行号有业务规则，数据库里有的行号不能编辑，行号不能重复。
使用该组件的模块有检验项目右侧抽屉表身
![avatar](http://chuantu.xyz/t6/702/1563454056x2728278714.jpg)
销售订单详情表身
![avatar](http://chuantu.xyz/t6/702/1563454120x2073530529.jpg)
```
 import DrawerEditable from '@/components/Editable/DrawerEditable'
      <DrawerEditable
        readonly={readonly.readOnly} //只读属性
        dataSource={datalist} //列表数据源
        drawerListChange={(data) => {
            // 表格数据改变回调函数
        }}
        scroll={{x: 1000}} //超过多上滚动
        columns={columns} // 列名
      />
 ```script


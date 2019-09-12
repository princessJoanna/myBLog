---
title: Order
date: 2019-07-19 14:09:17
tags: 组件
type: "categories"
---
该组件是点击新开tab的列表详情页面，多用于单据类页面（销售订单，采购订单...）

```
import Order from '@/components/TabsEdit/Order'
import TableHead form './TableHead'

      <Order
        urls={this.urls}
        columns={this.columns}
        TableHead={TableHead} // 详情页面表头组件
        wrappedComponentRef={(tableRef) => this.tableRef = tableRef}
      />


```script
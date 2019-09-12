---
title: TabsEdit
date: 2019-07-19 14:09:17
tags: 组件
type: "categories"
---
该组件是点击新开tab的列表页面组件，多用于单据类页面（销售订单，采购订单...）

```
import React, { Component } from 'react'
import {
  Form
} from 'antd'
import BtnGroup from '@/components/BtnGroup'
import TabsEdit from '@/components/TabsEdit'
import SearchForm from './SearchForm';
import AdvancedSearch from '@/components/AdvancedSearch'
class Orders extends Component {
  static title = '订单';
  constructor(props) {
    super(props)
    this.state = {
    }
    this.columns = [
      {
        title: '序号',
        dataIndex: 'index',
        editable: true,
        width:60,
        fixed: 'left',
      }...

    ]

  }



  // 组件挂载后
  componentDidMount() { }
  urls = {
    update: '/api/com/scm/updateSaleOrder',
    delete: '/api/com/scm/deleteSaleOrder',
    query: '/api/com/scm/querySaleOrder',
    fuzzyQuery: '/api/com/scm/querySaleOrder',
  }

  render() {
    return <div>
      <AdvancedSearch
        form={this.props.form}
        quickQuery={(values) => {
          this.tableRef.fuzzyQuery({billNo:values.fuzzyName,pageNum: 1})
        }}
        labelCol={{ span: 6 }}
        wrapperCol={{ span: 18 }}
        advancedQuery={(values) => {
          this.tableRef.query(values)
        }}
      >
        <BtnGroup
          btnList={['add', 'del', 'allDel']}
          addCallback={() => {
            this.tableRef.add()
          }}
          allDelCallback={() => {
            this.tableRef.allDelete()
          }}
          delCallback={() => {
            this.tableRef.delete()
          }}
        >
        </BtnGroup>
        <SearchForm form={this.props.form} />
      </AdvancedSearch>
      
      <TabsEdit 
        urls={this.urls} //请求接口参数
        columns={this.columns} // 自定义接口参数
        wrappedComponentRef={(tableRef) => this.tableRef = tableRef}
        parentPage={{
            parentName:'SaleOrder', //当前页面的code
            title:'销售订单',   //当前页面的标题
            pageName:'SaleOrderDetails'，//新开页面，详情页面的code
            pageTitleKey:'billNo', //如果订单编号需要调取接口，需要定义订单编号的key
            }}
      />
    </div>
  }
}
// eslint-disable-next-line no-class-assign
Orders = Form.create()(Orders)
export default Orders
```script
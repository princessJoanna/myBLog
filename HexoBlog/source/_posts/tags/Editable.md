---
title: Editable
date: 2019-07-08 14:09:17
tags: 组件
---
该组件是所有基础表格的组件，交互有当前表格的行编辑，右侧抽屉交互的页面
当前行编辑
![avatar](http://chuantu.xyz/t6/702/1563452483x2073530529.png)

右侧抽屉编辑
![avatar](http://chuantu.xyz/t6/702/1563452290x2073530529.png)

```
基础表格组件，当前整行编辑
/**
 * 客户类别
 **/
import React, { Component } from 'react'
import BtnGroup from '@/components/BtnGroup'  // 按钮组
import Editable from '@/components/Editable'  // 基础表格组件


class CustomeType extends Component {
  static title = '客户类别'
  constructor(props) {
    super(props)
    this.state = {
    }
  }
// 当前页面自定义列属性
  columns = [{
    title: '序号',
    dataIndex: 'index',
    width: '80px',
  }, {
    title: '客户类别编码',
    dataIndex: 'customerTypeCode',
    editable: true,
    width: '300px',
    maxLength: 16,
  }, {
    title: '客户类别名称',
    dataIndex: 'customerTypeName',
    editable: true,
    maxLength: 32,
  }]
// 接口定义，新增，修改，删除，查询和复制的key，必须是insert,update,delete,query,copy
  
  urls = {
    insert: '/api/com/scm/insertComCustomerType', 
    update: '/api/com/scm/updateComCustomerType',  
    delete: '/api/com/scm/deleteComCustomerType',
    query: '/api/com/scm/queryComCustomerType', 
    copy: '/api/com/scm/copyUnitGroup',
  }  

  render() {
    return (
      <div>
        <BtnGroup
          addCallback={() => {
            this.tableRef.add()
          }}
          allDelCallback={() => {
            this.tableRef.allDelete()
          }}
          delCallback={() => {
            this.tableRef.delete()
          }}    
        ></BtnGroup>
        <Editable
          columns={this.columns}
          showPagination={false}
          urls={this.urls}
          wrappedComponentRef={(tableRef) => this.tableRef = tableRef}
        />
      </div>
    )
  }
}

export default CustomeType

右侧抽屉交互类型的页面，Editable组件引入方式一样，例外需要传入自定义的抽屉组件
/**
* 人员
**/
import React, { Component } from 'react'
import {
  Form
} from 'antd'
import BtnGroup from '@/components/BtnGroup' // 按钮组
import Editable from '@/components/Editable' //基础表格组件
import Edit from './Edit';                   // 自定义抽屉组件
import SearchForm from './SearchForm';       //自定义搜索框
import AdvancedSearch from '@/components/AdvancedSearch' //高级组件公共属性
class Custome extends Component {
  static title = '人员';
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
      },
      {
        title: "人员编号",
        dataIndex: "personCode",
        editable: true,
      },
      {
        title: "人员名称",
        dataIndex: "personName",
        editable: true,
      },
      {
        title: "部门编码",
        dataIndex: "bm_number",
        editable: true,

      },
      {
        title: "部门",
        dataIndex: "deptCode",
        editable: true,
      },
      {
        title: "产线卡号",
        dataIndex: "cardNo",
        editable: true,
      },
      {
        title: "身份证",
        dataIndex: "identityCard",
        editable: true,
      },
      {
        title: "电话",
        dataIndex: "phoneNo",
        editable: true,
      },
      {
        title: "初始密码",
        dataIndex: "password",
        editable: true,
      },
      {
        title: "邮箱",
        dataIndex: "email",
        editable: true,
      },
      {
        title: "住址",
        dataIndex: "homeAddress",
        editable: true,
      }

    ]

  }



  // 组件挂载后
  componentDidMount() { }
  urls = {
    insert: '/api/com/scmPerson/insertScmPerson',
    update: '/api/com/scmPerson/updateScmPerson',
    delete: '/api/com/scmPerson/deleteScmPerson',
    query: '/api/com/scmPerson/queryScmPerson',
    copy: '/api/com/scmPerson/copyScmPerson',
    fuzzyQuery: '/api/com/scmPerson/fuzzyScmPerson',
  }
  search(values) {
    this.tableRef.query(values)
  }
  // 抽屉传入方法
  drawerContent = (props, params = {},editType) => {
    return (
      <Edit params={params} {...props} editType={editType} />
    )
  }
  render() {
    return <div>
      <AdvancedSearch
        form={this.props.form}
        quickQuery={(values) => {
          this.tableRef.fuzzyQuery(values)
        }}
        labelCol={{ span: 6 }}
        wrapperCol={{ span: 18 }}
        advancedQuery={(values) => {
          this.tableRef.query(values)
        }}
      >
        <BtnGroup
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
      <Editable
        columns={this.columns}
        drawerContent={this.drawerContent}
        drawerTtile="人员详情"
        operation={{ fixed: 'right' }}
        scroll={{ x: 2000 }}
        urls={this.urls}
        wrappedComponentRef={(tableRef) => this.tableRef = tableRef}
      />
    </div>
  }
}
// eslint-disable-next-line no-class-assign
Custome = Form.create()(Custome)
export default Custome

```script




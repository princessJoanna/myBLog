---
title: AdvanceDSearch
date: 2019-07-08 14:09:17
tags: 组件
---
![avatar](http://chuantu.xyz/t6/702/1563450311x2073530529.jpg)

使用场景，列表页面带查询的表头，（人员、销售订单、销售发货单、采购订单等搜索模块）
/**
* 高级搜索组件
**/
“` javascript 
import AdvancedSearch from '@/components/AdvancedSearch'
    <AdvancedSearch
          form={this.props.form}
          quickQuery={(values) => {
            this.tableRef.fuzzyQuery(values)
          }}
          advancedQuery={(values) =>{
            this.tableRef.query(values)
          }}
          labelCol={{ span: 6 }}
          wrapperCol={{ span: 18 }}
          labelAlign="right"
        >
        <!--按钮组，可选-->
            <BtnGroup
              addCallback={() => {
                this.tableRef.add()
              }}
              delCallback={() => {
                this.tableRef.delete()
              }}
              allDelCallback={() => {
                this.tableRef.allDelete()
              }}
            />
          <!--按钮组，可选-->
          <!--自定义搜索内容，页面传入-->
            { advancedSearchContent(this.props) }
          <!--自定义搜索内容，页面传入-->
        </AdvancedSearch>
“` 
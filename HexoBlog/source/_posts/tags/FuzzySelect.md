---
title: FuzzySelect
date: 2019-07-08 14:09:17
tags: 组件
type: "categories"
---
该组件是下拉模糊匹配组件
![avatar](http://chuantu.xyz/t6/702/1563506304x1033347913.jpg)

```
    import FuzzySelect from '@/components/FuzzySelect'
    <FuzzySelect

        labelCol={{ span: 4 }}
        wrapperCol={{ span: 20 }}
        initValues={{  //初始值选项，可选
        idValue: queryDetails.deptId, //初始化传入值Id
        codeValue: queryDetails.deptCode, //初始化传入值Code
        nameValue: queryDetails.deptName    //初始化传入Name
        }}
        rules={[{ //校验，可选
        required: true, message: '请输选择部门'
        }]}
        {...readonly}  // 是否可编辑，可选
        aliasMaps={{ idAlias: 'deptId', codeAlias: 'deptCode', nameAlias: 'deptName' }}   // 对应的key，必传
        form={this.props.form}
        label="部门名称"  
        url="/api/com/scmDept/fuzzyScmDept"  // 模糊匹配的接口必传
        />
```script
---
title: RangePicker
date: 2017-07-08 14:09:17
tags: 组件
---
使用场景，开始时间和结束时间，显示时，转化成时间格式，保存后转化成字符串格式。
判断开始时间不能大于结束时间
![avatar](http://chuantu.xyz/t6/702/1563516485x992245975.png)

```
import RangePicker from '@/components/RangePicker'


    <RangePicker
        defaultValues={{
        startValue: queryDetails.entryDate,
        startKey: 'entryDate',
        endValue: queryDetails.dimissionDate,
        endKey: 'dimissionDate',
        placeholderStart: '入职时间',
        placeholderEnd: '离职时间',
        width:'100%'
        }}
        {...readonly}
        form={this.props.form}
        />
```script
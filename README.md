# 2017-08-16 新增功能
1. 将现有`meeting`模块降级为2级菜单  
2. 增加`代码审查`模块，具体需求如下  
* /users
> 编辑分组：新增分组，删除分组，修改分组  
> 编辑组员：新增组员，删除组员，修改组员  

* /codeview  
>* 列表代码审查日期，格式为2017-08-16  
>* 点击`开启新评审`按钮后（每日只能开启一次），新增代码审查日期；随机排序组内用户  
>* 点击相应的代码审查记录 进入/codeview/2017-08-16  

* /codeview/2017-08-16  
>* 2栏设计，左侧使用tree，展示分组和用户列表，高亮已经`被审查`的用户；右侧默认展示本次审查记录所有情况
>* 点击用户名称，右侧展示或编辑当前用户的`被审查`记录  

3. 数据结构设计
维护json文档即可，同`会议系统`
* www/data/codeview/users.json  
```javascript
[
  {"group": "前端组",
  "users": [
      "鹿丹",
      "杨利龙",
      "刘悦",
      "安晓凯",
      "田永新",
  ]},
]
```
* www/data/codeview/details/2017-08-16.json  
点击`开启新评审`按钮后，如果已经存在当天的json文件，则不再创建；否则按照yyyy-MM-dd的格式创建新的json文件
```javascript
[
{"owner":"刘悦",
  "reviewer":["安晓凯","田永新"],
  "codes":[
      {
        "description" :"一句话描述当前代码",
        "url":"code url",
        "comment":"审查记录"
      }
  ]},
]
```

# BackStageManagement


#### 网站技术

```
vue全家桶：vue+vuex+vue+router
element-ui： 常用的后台管理模块
axios 
less

命令： cnpm install axios element-ui --save
```

#### 脚手架安装

> 1. vue create BackStageManagement  开始安装项目
>
>    ![](ReadmeImage\1.png)
>
>    ![](ReadmeImage\2.png)
>
>    ![](ReadmeImage\3.png)
>
>    ![](ReadmeImage\4.png)
>
>    ![](ReadmeImage\5.png)
>
>    ![](ReadmeImage\6.png)
>
>    ![](ReadmeImage\7.png)
>
>    ![](ReadmeImage\8.png)
>
>    #### 完整的配置项目
>
>    ![](ReadmeImage\9.png)





## 接口规范

#### (1) 注册接口

> **简要描述：**
>
> - 用户注册接口
>
> **请求URL：**
>
> - `http://xx.com/api/user/register`
>
> **请求方式：**
>
> - POST
>
> **参数：**
>
> | 参数名   | 必选 | 类型   | 说明   |
> | :------- | :--- | :----- | ------ |
> | username | 是   | string | 用户名 |
> | password | 是   | string | 密码   |
> | name     | 否   | string | 昵称   |
>
> **返回示例**
>
> ```
>   {    "error_code": 0,    "data": {      "uid": "1",      "username": "12154545",      "name": "吴系挂",      "groupid": 2 ,      "reg_time": "1436864169",      "last_login_time": "0",    }  }
> ```
>
> **返回参数说明**
>
> | 参数名  | 类型 | 说明                                 |
> | :------ | :--- | ------------------------------------ |
> | groupid | int  | 用户组id，1：超级管理员；2：普通用户 |

#### (2) 用户登录

> **简要描述：**
>
> - 用户登录接口
>
> **请求URL：**
>
> - `http://xx.com/api/user/login`
>
> **请求方式：**
>
> - POST
>
> **参数：**
>
> | 参数名   | 必选 | 类型   | 说明   |
> | :------- | :--- | :----- | ------ |
> | username | 是   | string | 用户名 |
> | password | 是   | string | 密码   |
>
> **返回示例**
>
> ```
>   {    "error_code": 0,    "data": {      "uid": "1",      "username": "12154545",      "name": "吴系挂",      "groupid": 2 ,      "reg_time": "1436864169",      "last_login_time": "0",    }  }
> ```
>
> **返回参数说明**
>
> | 参数名  | 类型 | 说明                                 |
> | :------ | :--- | ------------------------------------ |
> | groupid | int  | 用户组id，1：超级管理员；2：普通用户 |

#### (3) 全局错误码

> | 错误码 | 错误解释     |
> | ------ | ------------ |
> | 1001   | 接口认证失败 |
> | 1002   | 授权过期     |
> | 1003   | 缺失参数     |

#### （4）user的数据字典

- 用户表，储存用户信息

> | 字段            | 类型         | 空   | 默认 | 注释                   |
> | :-------------- | :----------- | :--- | ---- | ---------------------- |
> | uid             | int(10)      | 否   |      |                        |
> | username        | varchar(20)  | 否   |      | 用户名                 |
> | groupid         | tinyint(2)   | 否   | 2    | 1为管理员，2为普通用户 |
> | password        | varchar(50)  | 否   |      | 密码                   |
> | avatar          | varchar(200) | 是   |      | 头像                   |
> | avatar_small    | varchar(200) | 是   |      | 小头像                 |
> | email           | varchar(50)  | 否   |      | 邮箱                   |
> | name            | varchar(15)  | 是   |      | 昵称                   |
> | reg_time        | int(11)      | 否   | 0    | 注册时间               |
> | last_login_time | int(11)      | 否   | 0    | 最后一次登录时间       |

#### （5）页面表，保存编辑的页面内容

> | 字段            | 类型        | 空   | 默认 | 注释                   |
> | :-------------- | :---------- | :--- | ---- | ---------------------- |
> | page_id         | int(10)     | 否   | 0    | 页面自增id             |
> | author_uid      | int(10)     | 否   | 0    | 页面作者uid            |
> | author_username | varchar(50) | 否   |      | 页面作者用户名         |
> | item_id         | int(10)     | 否   | 0    | 项目id                 |
> | cat_id          | int(10)     | 否   | 0    | 父目录id               |
> | page_title      | varchar(50) | 否   |      | 页面标题               |
> | page_content    | text        | 否   |      | 页面内容               |
> | order           | int(10)     | 否   | 99   | 顺序号。数字越小越靠前 |
> | addtime         | int(11)     | 否   | 0    | 该记录添加的时间       |

#### （6）项目表，储存项目信息

> | 字段             | 类型         | 空   | 默认 | 注释                   |
> | :--------------- | :----------- | :--- | ---- | ---------------------- |
> | item_id          | int(10)      | 否   |      | 项目id、自增id         |
> | item_name        | varchar(50)  | 否   |      | 项目名                 |
> | item_description | varchar(225) | 否   |      | 项目描述               |
> | uid              | int(10)      | 是   |      | 创建人uid              |
> | username         | varchar(50)  | 否   |      | 创建人用户名           |
> | password         | varchar(50)  | 否   |      | 项目密码。可为空       |
> | addtime          | int(11)      | 否   |      | 项目添加的时间，时间戳 |
# 接口划分
[TOC]
## 1 配置联合上线部署（共5个接口）
### 1.1 获取产品线列表[GET]
- 是否有此功能：有
- 请求 URL: http://172.17.5.109/api/app/productline/select
- 参数：无
- 返回结果
``` json
    {
        "info": "操作成功！",
        "data": [
            {
                "id": "5000",
                "name": "OPENSRVC,USASTRAN"
            },
            {
                "id": "5105",
                "name": "OPENTKT"
            }
        ], 
        "success": true,
        "level": "info"
    }
```

### 1.2 获取业务列表[GET]
- 是否有此功能：有
- 请求 URL: http://172.17.5.109/api/app/applications/{id}/select_by_pl
- 参数：id 产品线ID
- 返回结果
```json
{
    "info": "操作成功！",
    "data": [
        {
            "id": "5000",
            "name": "OPENSRVC,USASTRAN"
        }
    ],
    "success": true,
    "level": "info"
}
```

### 1.3 获取实例列表[GET]
- 是否有此功能：有
- 请求 URL: http://172.17.5.109/api/app/jobinstance/jobi_list_one?product_line_id=750&application_id=5093&name=&unfiltered=true
- 参数：product_line_id 产品线ID  ，application_id业务ID
- 返回结果
```json
{
    "info": "操作成功！",
    "data": [
        {
            "status": "init",
            "product_line_name": "服务整合平台",
            "update_time": "2019-01-07 17:06:56",
            "application_id": "5093",
            "name": "asdasd1111rr",
            "mender": null,
            "job_template_name": "apache2",
            "creator": "liupeng",
            "remark": "asdasdasd",
            "product_line_id": "750",
            "env_name": "内测环境M",
            "create_time": "2019-01-07 17:06:56",
            "job_template_id": "eb331a404dd611e8b19ffa163ec53c3b",
            "module_name": "TUMS",
            "application_name": "消息总线(TUMS)",
            "module_id": "1460",
            "env_id": "11ace0bb1dc211e8a9ad4845204d5bd4",
            "id": "9540d98e125b11e9b213005056b361cd",
            "deploy_type": "install"
        }
    ],
    "success": true,
    "level": "info"
}
```

### 1.4 提交（返回联合上线ID）[POST]
- 是否有此功能：有
- 请求 URL: http://172.17.5.109/api/app/jointline/save/
- 参数：无
- 请求数据
```json
{
    "id":"d8f159c8130611e99060005056b361cd",
    "joint":[
        {
            "jobi_id":"81f83a0c08e711e98b8f005056b361cd",
            "sequence":0,
            "parent":[

            ],
            "top":125,
            "left":256.99998474121093
        },
        {
            "jobi_id":"2369613408e511e98381005056b361cd",
            "sequence":1,
            "parent":[
                0
            ],
            "top":155,
            "left":558.0000152587891
        }
    ]
}
```
- 返回结果[需要修改]
```json
{
    "info":"操作成功！",
    "data":{"id":"sdasadwqdwq231435134"},
    "success":true,
    "level":"info"
}
```

### 1.5 反显（提供联合上线ID，返回具体编排顺序）[GET]
- 是否有此功能：有
- 请求 URL: http://172.17.5.109/api/app/jointline/get_structure/{id}/
- 参数: id 联合上线ID
- 返回结果
``` json
{
    "info": "操作成功！",
    "data": {
        "joint": [
            {
                "status": "init",
                "jobi_name": "asda",
                "parent": [
                    ""
                ],
                "sequence": 0,
                "top": 125,
                "jobi_id": "81f83a0c08e711e98b8f005056b361cd",
                "left": 257
            },
            {
                "status": "init",
                "jobi_name": "pppp",
                "parent": [
                    "0"
                ],
                "sequence": 1,
                "top": 155,
                "jobi_id": "2369613408e511e98381005056b361cd",
                "left": 559
            }
        ],
        "id": "d8f159c8130611e99060005056b361cd",
        "name": "dddd"
    },
    "success": true,
    "level": "info"
}
```

### 1.6 查询联合上线[GET]
- 是否有此功能：有
- 请求 URL: http://172.17.5.109/api/app/jointline/aos_json?&name=test&productline_id=4
- 参数: name:查询的名字，prodoctline:产品线id
- 返回结果
``` json
{
    "count": 12,
    "page": 1,
    "results": [
        {
            "update_time": "2018-07-18 14:28:10",
            "name": "test001",
            "creator": "test21",
            "mender": null,
            "remark": "",
            "create_time": "2018-07-18 14:28:10",
            "id": "bd81dd668a5311e89c0d005056b361cd"
        }
    ]
}
```

### 1.7 创建联合上线[POST]
- 是否有此功能：有
- 请求 URL: http://172.17.5.109/api/app/jointline/create/
- 参数: name:查询的名字，prodoctline:产品线id
- 请求数据
``` json
{"name":"test20190121","remark":"","productline_id":"4"}
```
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":"8397efc61d4911e9a4d1005056b361cd",
    "success":true,
    "level":"info"
}
```
---
## 2 联合上线部署（共1个接口）
### 2.1 提交联合上线ID[POST][新]
- 是否有此功能：无，需要开发

## 3 配置业务（共2个接口）
### 3.1 获取产品线列表[GET]（同1.1）
### 3.2 获取业务列表[GET]（同1.2）

## 4 配置部署模板(共5个接口)
### 4.1 查询模板[GET]
- 请求 URL: http://172.17.5.109/api/app/jobtemplate/aos_json?name=sss&application_id=4 
- 参数：name:模板名字,application_id:应用id
- 请求数据
``` json
{
    "count":3,
    "page":1,
    "results":[
        {
            "status":"available",
            "update_time":"2018-05-24 14:08:51",
            "name":"assssss",
            "mender":"liupeng",
            "creator":"test11",
            "remark":"sss",
            "create_time":"2018-05-18 16:18:48",
            "jobt_rollback_name":null,
            "jobt_rollback_id":null,
            "type":"public",
            "id":"1729c6405a7411e8b8390021cc698915",
            "deploy_type":"install"
        }
    ]
}
```
### 4.2 提交模板[POST]
- 请求 URL: http://172.17.5.109/api/app/jobtemplate/6610aade0e5211e9bd44005056b361cd/graded
- 参数：id模板ID
- 请求数据
``` json
{
    "method":[
        {
            "component_id":"custom",
            "method_id":"cu1",
            "sequence":0
        },
        {
            "component_id":"custom",
            "method_id":"cu1",
            "sequence":1
        }
    ]
}
```
- 返回结果[需要修改]
```json
{
    "info":"操作成功！",
    "data":{
        "id":"sdasdsadwqdd323",
        "is_rollback":false
    }
    ,
    "success":true,
    "level":"info"
}
```
### 4.3 反显模板内编排数据[GET]
- 请求 URL: http://172.17.5.109/api/app/jobtemplate/{id}/graded_content
- 参数：id 模板ID
- 返回结果
```json
{
    "info": "操作成功！",
    "data": [
        {
            "remark": "自定义脚本执行",
            "component_id": "custom",
            "name": "custom-script",
            "sequence": 0,
            "path": "http://172.17.5.108:8081/artifactory/component/custom/custom-script.tar.gz",
            "id": "cu1",
            "component_name": "custom"
        },
        {
            "remark": "自定义脚本执行",
            "component_id": "custom",
            "name": "custom-script",
            "sequence": 1,
            "path": "http://172.17.5.108:8081/artifactory/component/custom/custom-script.tar.gz",
            "id": "cu1",
            "component_name": "custom"
        }
    ],
    "success": true,
    "level": "info"
}
```
### 4.4 获取组件方法列表[GET]
- 请求 URL: http://172.17.5.109/api/component/select
- 参数：无
- 返回结果
``` json
{
    "info": "操作成功！",
    "data": [
        {
            "method": [
                {
                    "path": "http://10.221.195.91:8081/artifactory/component/apache/apache-staticfile.tar.gz",
                    "remark": "apache静态文件更新方法",
                    "config": null,
                    "id": "apa2",
                    "name": "staticfile"
                },
                {
                    "path": "http://10.221.195.91:8081/artifactory/component/apache/apache-virtualhost.tar.gz",
                    "remark": "apache虚拟主机相关方法",
                    "config": null,
                    "id": "apa3",
                    "name": "virtualhost"
                },
                {
                    "path": "http://10.221.195.91:8081/artifactory/component/apache/apache-port.tar.gz",
                    "remark": "apache监听端口方法",
                    "config": null,
                    "id": "apa1",
                    "name": "port"
                }
            ],
            "remark": "apache组件",
            "id": "apa",
            "name": "apache"
        },
        {
            "method": [
                {
                    "path": "http://10.221.195.91:8081/artifactory/component/jboss/jboss-war-update.tar.gz",
                    "remark": "jboss包更新方法",
                    "config": null,
                    "id": "jb1",
                    "name": "war_update"
                },
                {
                    "path": "http://10.221.195.91:8081/artifactory/component/jboss/jboss-db-update.tar.gz",
                    "remark": "jboss数据源更新方法",
                    "config": null,
                    "id": "jb3",
                    "name": "db_update"
                },
                {
                    "path": "http://10.221.195.91:8081/artifactory/component/jboss/jboss-war-delete.tar.gz",
                    "remark": "jboss-包删除方法",
                    "config": null,
                    "id": "jb5",
                    "name": "war_delete"
                },
                {
                    "path": "http://10.221.195.91:8081/artifactory/component/jboss/jboss-file-update.tar.gz",
                    "remark": "jboss-文件或者脚本上传",
                    "config": null,
                    "id": "jb6",
                    "name": "file_update"
                }
            ],
            "remark": "jboss组件",
            "id": "jb",
            "name": "jboss"
        },
    ],
    "success": true,
    "level": "info"
}
```
### 4.5 删除模板[PSOT]
- 请求 URL：http://172.17.5.109/api/app/jobtemplate/{id}
- 参数：id:模板ID
- 请求数据
``` json
{"info":"操作成功！","data":true,"success":true,"level":"info"}
```
----
## 5 配置部署实例(共9个接口)
### 5.1 获取（查询）环境列表[同8.1.2]
----
### 5.2 选择模板创建任务实例[PSOT][需修改]
- 请求 URL：http://172.17.5.109/api/app/jobinstance/create
- 参数：无
- 请求数据
``` json
{
    "name":"wwwws",
    "env_id":"cbdedcd0772911e792bd005056b361cd",
    "application_id":"4",
    "job_template_id":"8c5eb9802e8b11e8b66b4845204d5bd4",
    "remark":"ss"
}
```
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
        "id":"ce883e08148611e9a448005056b361cd",
    },
    "success":true,
    "level":"info"
}
```
### 5.3 获取（查询）模板列表[GET]
- 请求 URL：http://172.17.5.109/api/app/jobtemplate/ordinary/select
- 参数：无
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":[
        {
            "id":"0d75fc862e6411e8a2f1005056b361cd",
            "creator":"44a8594854a211e791c1005056b361cd",
            "mender":"06e783c80ef511e890a7005056b361cd",
            "create_time":"2018-03-23 14:33:09",
            "update_time":"2018-04-10 14:18:03",
            "remark":"sadf",
            "name":"0323test",
            "type":"public",
            "status":"available",
            "deploy_type":"install"
        },
        {
            "id":"c35cc66c2e6c11e89e5f005056b361cd",
            "creator":"ff068a6645e411e7b4061002b5caccd6",
            "mender":"3c9968922e3a11e89e5f005056b361cd",
            "create_time":"2018-03-23 15:35:30",
            "update_time":"2018-04-17 11:17:58",
            "remark":null,
            "name":"111",
            "type":"public",
            "status":"available",
            "deploy_type":"install"
        },
    "success":true,
    "level":"info"
}
```

### 5.4 获取（查询）集群列表[GET]
- 请求 URL: http://172.17.5.109/api/resource/clusters/{id1}/{id2}/select/envapp
- 参数：id1：任务实例ID，id2：业务ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":[
        {
            "remark":null,
            "id":"322",
            "name":"redis234A"
        },
        {
            "remark":"",
            "id":"6c48210413b911e993c6005056b361cd",
            "name":"aos_test2"
        }
    ],
    "success":true,
    "level":"info"
}
```
### 5.5 查询按钮[GET]
- 请求 URL： http://172.17.5.109/api/app/jobinstance/aos_json?name=&application_id=4
- 参数： name:实例名 application_id：业务ID
- 返回结果
``` json
{
    "count":1,
    "page":1,
    "results":[
        {
            "status":"ready",
            "product_line_name":"apache产品线",
            "update_time":"2018-09-07 16:46:39",
            "application_id":"4",
            "name":"workflow_test1",
            "mender":"test23",
            "job_template_name":"apache-port",
            "creator":"test23",
            "remark":"",
            "product_line_id":"4",
            "env_name":"内测环境N",
            "create_time":"2018-09-05 14:24:56",
            "job_template_id":"a998420c41f411e7b969005056b361cd",
            "module_name":"apache模块",
            "application_name":"apache应用",
            "module_id":"4",
            "env_id":"11ace0ba1dc211e8a9ad4845204d5bd4",
            "id":"68726af0b0d411e8adf9005056b361cd",
            "deploy_type":"install"
        }
    "success":true,
    "level":"info"
}
```

### 5.6 保存接口
#### 5.6.1 保存接口 合并[POST]
- 请求 URL： http://172.17.5.109/api/app/jobinstance/{id}/{cpm_id}/{sequence}/relation/alldata
- 参数：id :任务实例ID，cpm_id：组件方法ID，sequence：顺序，cluster_id:集群ID
- 请求数据
``` json
{
  "cluster":{"cluster_id":"bfc2bb10e7e411e8b7eb0021cc698915"},
 "artifacts":[{
            "file_id":"33642c1edc1111e89290005056b361cd",
            "dest":"ss",
            "host_IP":["10.5.91.37"]
        }],
  "actemplates":{
           "file_id":"9445a964429211e78da9005056b361cd",
           "groups":[{
                    "dest":"kk",
                    "host_IP":["172.17.5.102"],
                    "configs":{
                        "94df2fbc429211e7950c005056b361cd":[{
                            "94e5257a429211e7950c005056b361cd":"默认"
                            }],
                        "94ec69ca429211e7950c005056b361cd":[{
                                "94f05850429211e7950c005056b361cd":"默认"
                            }],
                        "94f6b4fc429211e7950c005056b361cd":[{
                                "94fbccf8429211e7950c005056b361cd":"默认"
                            }],
                        "9503e4e2429211e7950c005056b361cd":"/opt/app/apache2",
                        "950a020a429211e7950c005056b361cd":"172.17.5.102:80",
                        "950f6286429211e7950c005056b361cd":"/webdocs",
                        "95154b74429211e7950c005056b361cd":"you@example.com",
                        "951bbe46429211e7950c005056b361cd":"logs/error_log",
                        "95224dba429211e7950c005056b361cd":"warn",
                        "9528b880429211e7950c005056b361cd":"true"
                    },
                    "targetname":"httpd.conf"
                }]
			},
    "config":{"config_value":{
        "apa101":[{
                "apa10101":"8087"
            	}]
    		}},
    "scripts":{
              "scripts_data":[{
                      "id":"9ca49206bbb911e8ac4f000c2949f037",
                      "dest":"dddd",
                      "host_IP":["172.17.5.103"],
                      "parameter":"ddd",
                      "execute_type":"shell"
                  }]
             }
```
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":true,
    "success":true,
    "level":"info"
}
```

#### 5.6.2 保存接口参考：
##### 5.6.2.1 保存集群[POST]
- 请求 URL： http://172.17.5.109/api/app/jobinstance/{id}/{cpm_id}/{sequence}/{cluster_id}/relation/cluster?format=json
- 参数：id :任务实例ID，cpm_id：组件方法ID，sequence：顺序，cluster_id:集群ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":true,
    "success":true,
    "level":"info"
}
```
##### 5.6.2.2 保存关联软件包[POST]
- 请求URL：http://172.17.5.109/api/app/jobinstance/{id}/{cpm_id}/{sequence}/relation/artifact
- 参数：id：任务实例ID，cpm_id组件方法ID，sequence:顺序ID
- 请求数据
``` json
{
    "artifacts":[
        {
            "file_id":"33642c1edc1111e89290005056b361cd",
            "dest":"ss",
            "host_IP":[
                "10.5.91.37"
            ]
        }
    ]
}
```
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":[
        true,
        {
            "id":"e055908013c911e98608005056b361cd",
            "name":"testxss"
        }
    ],
    "success":true,
    "level":"info"
}
```
##### 5.6.2.3 保存关联应用配置[POST]
- 请求URL：http://172.17.5.109/api/app/jobinstance/{id}/{cpm_id}/{sequence}/relation/actemplate
- 参数：id：任务实例ID，cpm_id组件方法ID，sequence:顺序ID
- 请求数据
``` json
{
    "file_id":"9445a964429211e78da9005056b361cd",
    "groups":[
        {
            "dest":"kk",
            "host_IP":[
                "172.17.5.102"
            ],
            "configs":{
                "94df2fbc429211e7950c005056b361cd":[
                    {
                        "94e5257a429211e7950c005056b361cd":"默认"
                    }
                ],
                "94ec69ca429211e7950c005056b361cd":[
                    {
                        "94f05850429211e7950c005056b361cd":"默认"
                    }
                ],
                "94f6b4fc429211e7950c005056b361cd":[
                    {
                        "94fbccf8429211e7950c005056b361cd":"默认"
                    }
                ],
                "9503e4e2429211e7950c005056b361cd":"/opt/app/apache2",
                "950a020a429211e7950c005056b361cd":"172.17.5.102:80",
                "950f6286429211e7950c005056b361cd":"/webdocs",
                "95154b74429211e7950c005056b361cd":"you@example.com",
                "951bbe46429211e7950c005056b361cd":"logs/error_log",
                "95224dba429211e7950c005056b361cd":"warn",
                "9528b880429211e7950c005056b361cd":"true"
            },
            "targetname":"httpd.conf"
        }
    ]
}
```
- 返回结果
``` json
{"info":"操作成功！","data":true,"success":true,"level":"info"}
```
##### 5.6.2.4 保存参数列表[POST]
- 请求URL：http://172.17.5.109/api/app/jobinstance/{id}/{cpm_id}/{sequence}/config/update
- 参数：id：任务实例ID，cpm_id组件方法ID，sequence:顺序ID
- 请求数据
``` json
{
    "config_value":{
        "apa101":[
            {
                "apa10101":"8087"
            }
        ]
    }
}
```
- 返回结果
``` json
{"info":"操作成功！","data":true,"success":true,"level":"info"}
```
##### 5.6.2.5 保存关联脚本[POST]
- 请求URL：http://172.17.5.109/api/app/jobinstance/{id}/{cpm_id}/{sequence}/relation/script
- 参数：id：任务实例ID，cpm_id组件方法ID，sequence:顺序ID
- 请求数据
``` json
{
    "script_id":"",
    "scripts_data":[
        {
            "id":"9ca49206bbb911e8ac4f000c2949f037",
            "dest":"dddd",
            "host_IP":[
                "172.17.5.103"
            ],
            "parameter":"ddd",
            "execute_type":"shell"
        }
    ]
}
```
- 返回结果
``` json
{"info":"操作成功！","data":true,"success":true,"level":"info"}
```
### 5.7 另存为（复制）接口[POST]
- 请求URL: http://172.17.5.109/api/app/jobinstance/{id}/copy
- 参数：id任务实例ID
- 请求数据
``` json
{
    "id":"6d2a7361f6cc11e89fde38378beebca7",
    "name":"ppp_backup",
    "env_id":"11ace0ba1dc211e8a9ad4845204d5bd4",
    "product_line_id":"4",
    "module_id":"4",
    "application_id":"4",
    "job_template_id":"7ec94961f6be11e8ae8238378beebca7",
    "remark":"ssss"
}
```
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
        "new_name":"ppp_backup",
        "new_id":"a1c8f13613ce11e996ff005056b361cd"
    },
    "success":true,
    "level":"info"
}
```
### 5.8 反显参数列表
#### 5.8.1 反显全部数据[POST]
- 请求 URL：http://172.17.5.109/api/jobinstance/{id}/{cpm_id}/{sequence}/出
- 参数：id：任务实例ID，cpm_id组件方法ID，sequence:顺序ID,应用权限:jurisdiction
- 请求数据

```json
{
    "env_id" : "",
    "app_id" :"",
    "file_id":"",#文件id
    "jurisdiction":[""]
}
```



- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
    	"clusters":[
                {
                    "remark":"",
                    "id":"47e0b2559fa611e8bf26484522225bd4",
                    "name":"ceshMM"
                },
		{
                    "remark":"",
                    "id":"47e0b2559fa611e8bf26484522225bd4",
                    "name":"ceshMM"
                }
	],
        "artifact":[{
            "file_id":"33642c1edc1111e89290005056b361cd",
            "dest":"ss",
            "host_IP":["10.5.91.37"]
        }],
        "actemplate_desc":"同上",
        "actemplate_value":"同上",
        "config_desc":"同上",
        "config_value":"同上",
        "script":"同上",
    },
    "success":true,
    "level":"info"
}
```
---------------------------------------------------------
#### 5.8.2 反显数据接口参考：
##### 5.8.2.1 获取已保存的集群反显[GET]
- 请求 URL：http://172.17.5.109/api/resource/clusters/{id}/{app_id}/select/envapp
- 参数：id：集群ID，app_id:业务ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":[
        {
            "remark":"",
            "id":"47e0b2559fa611e8bf26484522225bd4",
            "name":"ceshMM"
        }
    ],
    "success":true,
    "level":"info"
}
```
##### 5.8.2.2 获取软件包反显[GET][需修改]
- 请求 URL:http://172.17.5.109/api/app/jobinstance/{id}/{cpm_id}/{sequence}/artifact/json
- 参数：id：任务实例ID，cpm_id组件方法ID，sequence:顺序ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":[
        {
            "status":"Flash.zip",
            "artifact_name":"workflow",
            "artifact_version_name":"0.0.0.1",
            "download_path":"Flash.zip",
            "dest":"\tmp",
            "artifact_id":"210a4824b66811e8b94c005056b361cd",
            "host_IP":[
                "172.17.5.102"
            ],
            "filename":"Flash.zip",
            "version":"0.0.0.1",
            "file_id":"2eb3e9a8b66811e89b9f005056b361cd",
            "artifact_version_id":"2eb20ff2b66811e89b9f005056b361cd",
            "md5":"Flash.zip"
        }
    ],
    "success":true,
    "level":"info"
}
```
##### 5.8.2.3 获取应用配置模板-数据结构[GET]
- 请求 URL:http://172.17.5.109/api/app/jobinstance/{id}/{cpm_id}/{sequence}/actemplate/config/desc
- 参数：id：任务实例ID，cpm_id组件方法ID，sequence:顺序ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":[
        {
            "remark":"描述list",
            "default":"默认list",
            "has_subitem":true,
            "require":true,
            "rule":"",
            "children":[
                {
                    "remark":"描述",
                    "default":"默认",
                    "has_subitem":false,
                    "require":true,
                    "rule":"",
                    "children":null,
                    "key":"port",
                    "parentId":"94df2fbc429211e7950c005056b361cd",
                    "policy":"most",
                    "type":"other",
                    "id":"94e5257a429211e7950c005056b361cd"
                }
            ],
            "key":"ports",
            "parentId":"",
            "policy":"mostlist",
            "type":"list-map",
            "id":"94df2fbc429211e7950c005056b361cd"
        },
        {
            "remark":"描述list",
            "default":"默认list",
            "has_subitem":true,
            "require":true,
            "rule":"",
            "children":[
                {
                    "remark":"描述",
                    "default":"默认",
                    "has_subitem":false,
                    "require":true,
                    "rule":"",
                    "children":null,
                    "key":"modulename",
                    "parentId":"94ec69ca429211e7950c005056b361cd",
                    "policy":"most",
                    "type":"other",
                    "id":"94f05850429211e7950c005056b361cd"
                }
            ],
            "key":"Modules",
            "parentId":"",
            "policy":"mostlist",
            "type":"list-map",
            "id":"94ec69ca429211e7950c005056b361cd"
        }
    ],
    "success":true,
    "level":"info"
}
```
##### 5.8.2.4 获取应用配置模板-数据值[GET]
- 请求 URL:http://172.17.5.109/api/app/jobinstance/{id}/{cpm_id}/{sequence}/actemplate/{file_id}/config/value
- 参数：id：任务实例ID，cpm_id组件方法ID，sequence:顺序ID file_id:文件ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":[
        {
            "950a020a429211e7950c005056b361cd":"172.17.5.102:80",
            "94df2fbc429211e7950c005056b361cd":[
                {
                    "94e5257a429211e7950c005056b361cd":"默认"
                }
            ],
            "951bbe46429211e7950c005056b361cd":"logs/error_log",
            "9503e4e2429211e7950c005056b361cd":"/opt/app/apache2",
            "94f6b4fc429211e7950c005056b361cd":[
                {
                    "94fbccf8429211e7950c005056b361cd":"默认"
                }
            ],
        }
    ],
    "success":true,
    "level":"info"
}
```
##### 5.8.2.5 获取参数列表-数据结构[GET]
- 请求 URL:http://172.17.5.109/api/app/jobinstance/{cpm_id}/config/desc
- 参数：cpm_id组件方法ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":[
        {
            "remark":"待添加端口信息",
            "default":"",
            "has_subitem":true,
            "require":true,
            "rule":"",
            "children":[
                {
                    "remark":"端口号",
                    "default":"",
                    "has_subitem":false,
                    "require":true,
                    "rule":"",
                    "key":"port",
                    "parentId":"apa101",
                    "policy":"不变",
                    "type":"other",
                    "id":"apa10101"
                }
            ],
            "key":"ports",
            "parentId":"",
            "policy":"不变",
            "type":"list-map",
            "id":"apa101"
        }
    ],
    "success":true,
    "level":"info"
}
```
##### 5.8.2.6 获取参数列表-数据值[GET]
- 请求 URL:http://172.17.5.109/api/app/jobinstance/{id}/{cpm_id}/{sequence}/config/value
- 参数：id：任务实例ID，cpm_id组件方法ID，sequence:顺序ID file_id:文件ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
        "histor_data":false,
        "apa101":[
            {
                "apa10101":"8087"
            }
        ]
    },
    "success":true,
    "level":"info"
}
```
##### 5.8.2.7 获取脚本反显[GET]
- 请求 http://172.17.5.109/api/app/jobinstance/{id}/{cpm_id}/{sequence}/script/json
- 参数：id：任务实例ID，cpm_id组件方法ID，sequence:顺序ID file_id:文件ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":[
        {
            "execute_type":"shell",
            "dest":"dddd",
            "script_file_name":"nexus.py",
            "host_IP":[
                "172.17.5.103"
            ],
            "script_name":"nexus",
            "script_file_id":"9ca49206bbb911e8ac4f000c2949f037",
            "script_id":"9ca49204bbb911e8ac4f000c2949f037",
            "parameter":"ddd"
        }
    ],
    "success":true,
    "level":"info"
}
```
### 5.9 删除任务实例[DELETE]
- 请求 http://172.17.5.109/api/app/jobinstance/{id}?
- 参数：id：任务实例ID
- 返回结果
``` json
{"info":"操作成功！","data":null,"success":true,"level":"info"}
```
### 5.10 获取实例组件方法[GET]

- 请求 http://172.17.5.109/api/app/jobinstance/{id}/details 
- 参数：id：任务实例ID
- 返回结果

```json
{
    "info":"操作成功！",
 	"data":{
        "status":"generate",
        "product_line_name":"apache产品线",
        "update_time":"2019-01-22 16:52:36",
        "application_id":"4",
        "name":"eee",
        "mender":"liupeng",
        "job_template_name":"0323test",
        "creator":"test11",
        "remark":"",
        "product_line_id":"4",
        "env_name":"a",
        "create_time":"2019-01-17 11:04:55",
        "job_template_id":"0d75fc862e6411e8a2f1005056b361cd"
        "methods":[
        	{
        		"comp_id":"apa",
        		"cluster_name":"testtest222",
        		"cpm_name":"apache监听端口方法",
       	 		"sequence":0,
        		"cpm_id":"apa1",
        		"cluster_remark":"asdasd",
        		"comp_name":"apache",
        		"status":null,
        		"cluster_id":"2144fed0a44b11e89518005056b361cd",
        		"path":null,
        		"is_display_script":false
    		}],
    	"module_name":"apache模块",
    	"application_name":"apache应用",
    	"module_id":"4",
    	"env_id":"a3aafa00822d11e7aedef8a963203905",
    	"id":"aab578281a0411e9818c005056b361cd",
    	"deploy_type":"install"
},
	"success":true,
	"level":"info"
}
```

### 5.11 脚本审核

#### 5.11.1 获取脚本列表[GET]

- 请求 URL: http://172.17.5.109/api/script/index/aos_list?&application_id=4&name= 
- 参数：无
- 返回结果

```json
{
    "info": "操作成功！",
    "data": [
        {
            "id": "4d47dfe130e911e98cd52c56dc1edda1",
            "name": "qwekshjd"
        },
        {
            "id": "a1cc906230e211e98471005056b361cd",
            "name": "asdo"
        },
    ],
    "success": true,
    "level": "info"
}
```

#### 5.11.1 获取组件列表[GET]

- 请求 URL: http://172.17.5.109/api/artifact/filter/name/aos/?format=json&product_line_id={}&application_id={}&type={}
- 参数：type 组件类型(configure 应用配置,package 软件包) ,product_line_id 产品线ID,application_id 应用ID
- 返回结果

```json
{
    "info": "操作成功！",
    "data": [
        {
            "id": "bda6f39a402511e7b65e005056b361cd",
            "name": "apache_config"
        },
        {
            "id": "a0003b66072211e88f54005056b361cd",
            "name": "ruanjianbao"
        },
    ],
    "success": true,
    "level": "info"
}
```

#### 5.11.2 脚本审核权限[GET]

- 请求 URL: http://172.17.5.109/api/script/index/urole_script
- 参数：无
- 返回结果

```json
{"info":"操作成功！",
 "data":true
 "success":true,
 "level":"info"
}
```

#### 5.11.3 脚本审核[POST]

- 请求 URL: http://172.17.5.109/api/script/index/examine/{id}
- 参数：id 脚本ID
- 请求数据

```jaon
{method_id: "a1cc906230e211e98471005056b361cd", status: "able"/"disable"}
```

- 返回结果

```json
{
    "info":"操作成功！",
 	"data":{"name":"asdo","id":"a1cc906230e211e98471005056b361cd"},
    "success":true,
    "level":"info"
}
```

#### 5.11.4 脚本文件内容[GET]

- 请求 URL: http://172.17.5.109/api/script/index/detail_data/filedata/{id}
- 参数：id 脚本文件ID
- 返回结果

```jaon
{
	"info":"操作成功！",
	"data":{
		"file_data":"#coding:utf-8\r\nimport paramiko\r\nimport re\r\nimport socket\r\n\r\nclass SSHConnect(object):\r\n    def __init__(self,sip,spawd,suser,sport):\r\n"},
	"success":true,
	"level":"info"
	}
```

## 6 部署原子项暂定为1个接口（一键部署）

- 部署流程：AOS发起部署创建长连接，TAD接受后等待部署结果返回，如果部署动作完成，无论是否成功则返回部署状态给长连接返回到AOS平台
### 6.1 一键部署[POST]
- 请求 URL: http://172.17.5.109/api/app/jobinstance/{id}/executionall
- 参数：id 任务实例ID
- 请求数据
``` jaon
{"use_tad_host":false}
```
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
        "msg":null,
        "result":true
    },
    "success":true,
    "level":"info"
}
```
### 6.2 单步部署[POST]
- 请求 URL: http://172.17.5.109/api/app/jobinstance/{id}/setp_execution
- 参数：id 任务实例ID
- 请求数据
``` jaon
{"use_tad_host":false}
```
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
        "msg":null,
        "result":true
    },
    "success":true,
    "level":"info"
}
```
### 6.3 终止部署[POST]
- 请求 URL: http://172.17.5.109/api/app/jobinstance/{id}/stop_execution
- 参数：id 任务实例ID
- 请求数据
``` jaon
{"use_tad_host":false}
```
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
        "msg":null,
        "result":true
    },
    "success":true,
    "level":"info"
}
```
## 7 上线工单共3个接口
### 7.1 获取（任务实例）列表 无分页[GET]
- 请求 URL: http://172.17.5.109/api/app/jobinstance/jobi_list_one
- 返回结果
``` json
{
    "info": "操作成功！",
    "data": [
        {
            "status": "generate",
            "product_line_name": "apache产品线",
            "update_time": "2019-01-09 13:28:32",
            "application_id": "4",
            "name": "ppp_backup",
            "mender": "liupeng",
            "job_template_name": "z_test",
            "creator": "liupeng",
            "remark": "ssss",
            "product_line_id": "4",
            "env_name": "内测环境N",
            "create_time": "2019-01-09 13:23:01",
            "job_template_id": "7ec94961f6be11e8ae8238378beebca7",
            "module_name": "apache模块",
            "application_name": "apache应用",
            "module_id": "4",
            "env_id": "11ace0ba1dc211e8a9ad4845204d5bd4",
            "id": "a1c8f13613ce11e996ff005056b361cd",
            "deploy_type": "install"
        },
    "success":true,
    "level":"info"
}
```
### 7.2 反显数据[GET]
- 请求 URL: http://172.17.5.109/api/app/jobinstance/{id}/details
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
        "current_flow_node":null,
        "process_status":"未同步",
        "online_date":null,
        "halt_time":"2019-1-09 12:48",
        "excel_data":{
            "ONLINE_OPERATION_PROCESS":[
                {
                    "OPERATION_CONTENT":"...",
                    "REMARKS":"自定义脚本执行",
                    "USER_NAME":"errt",
                    "SERVICE_IP":"10.5.91.37",
                    "HALT_TIME":""
                }
            ],
            "SERVICE_CODE":"5093",
            "SERVICE_NAME":"消息总线(TUMS)",
            "CONTACTS":"sss",
            "CHANGE_MODE":"上线",
            "halt_time":"2019-1-09 12:48",
            "TYPE_PRODUCTION":"业务投产",
            "EXECUTOR":"luanheng",
            "CONTACTS_EMAIL":"s@w.com",
            "regain_time":"2019-1-09 12:48",
            "SERVICE_ROLE":"系统负责人",
            "TYPES":[
                {
                    "STATUS":false,
                    "RESOURCE_DETAILS":"10.5.91.37",
                    "JCF_CONSOLE":"不使用",
                    "RESOURCE_ID":"81712",
                    "JCF_CHOICE":"",
                    "SUBTYPE":"独立应用服务器",
                    "STATE":"已分配",
                    "SERVICE_IP_PROTECT":"",
                    "REGAIN_TIME":"",
                    "PURPOSE":"生产",
                    "TYPES":"S3HOST",
                    "HOST_NAME":"vm-vmw43980-app"
                }
            ]
        },
        "regain_time":"2019-1-09 12:48",
        "work_number":null,
        "doc_id":"cb6f53b613c611e993c6005056b361cd"
    },
    "success":true,
    "level":"info"
}
```
### 7.3 保存[POST]
- 请求 URL: http://172.17.5.109/api/app/jobinstance/online/process/save
- 请求数据
``` json
{
    "job_instance_id":"e684b7d8131a11e99060005056b361cd",
    "doc_id":"",
    "excel_data":{
        "SERVICE_NAME":"消息总线(TUMS)",
        "CHANGE_MODE":"上线",
        "TYPE_PRODUCTION":"业务投产",
        "CONTACTS":"sss",
        "CONTACTS_EMAIL":"s@w.com",
        "regain_time":"2019-1-09 12:48",
        "halt_time":"2019-1-09 12:48"
    },
    "app_id":"5093"
}
```
- 返回结果
``` json
{
    "info":"æä½æåï¼",
    "data":{
        "current_flow_node":null,
        "doc_id":"cb6f53b613c611e993c6005056b361cd",
        "process_status":"æªåæ­¥"
    },
    "success":true,
    "level":"info"
}
```
---
## 8 配置部署资源（集群共9个接口、主机共5个接口）
### 8.1 集群（共8个接口）
#### 8.1.1 获取集群类型[GET]
- 请求 URL: http://172.17.5.109/api/resource/clusters/cmdb_type
- 参数：无
- 返回结果
``` json
{
    "info": "操作成功！",
    "data": [
        {
            "value": "ApacheCluster",
            "key": "ApacheCluster"
        },
        {
            "value": "CDSCluster",
            "key": "CDSCluster"
        }
    ],
    "success": true,
    "level": "info"
}
```
#### 8.1.2 获取环境列表[GET]
- 请求 URL: http://172.17.5.109/api/resource/envs/select
- 参数：无
- 返回结果
``` json
{
    "info": "操作成功！",
    "data": [
        {
            "remark": "",
            "creator": "admin",
            "create_time": "2017-08-02 10:09:41",
            "id": "b2fa4164776a11e79ae8005056b361cd",
            "name": "预投产环境"
        },
        {
            "remark": "UAT",
            "creator": "admin",
            "create_time": "2018-03-01 13:21:07",
            "id": "11ace0c01dc211e8a9ad4845204d5bd4",
            "name": "预投产环境L"
        },
        {
            "remark": "预投产",
            "creator": "admin",
            "create_time": "2018-03-01 13:21:07",
            "id": "11ace0c31dc211e8a9ad4845204d5bd4",
            "name": "预投产环境P"
        }
    ],
    "success": true,
    "level": "info"
}
```
#### 8.1.3 查询提交按钮[GET]
- 请求 URL: http://172.17.5.109/api/resource/clusters/aos_json?format=json&app=4&name=ceshi
- 参数：app:业务id， name:集群名
- 返回结果
``` json
{
    "count": 2,
    "page": 1,
    "results": [
        {
            "remark": "",
            "name": "ceshiPPP",
            "creator": "02ef286a75c611e8bff6005056b361cd",
            "env_name": "预投产环境P",
            "apps": "apache应用",
            "update_time": "2018-08-14 18:35:59",
            "create_time": "2018-08-14 18:35:59",
            "env_id": "11ace0c31dc211e8a9ad4845204d5bd4",
            "type": "其它",
            "id": "d5b664fb9fad11e8bf26484522225bd4"
        }
    ]
}
```
#### 8.1.4 新建提交按钮[POST]
- 请求 URL: http://172.17.5.109/api/resource/clusters/aos_create
- 参数：无
- 请求值
``` json
{
    "name":"ceshi12",
    "remark":"描述",
    "type":"TodeMPCluster",
    "env_id":"11ace0c21dc211e8a9ad4845204d5bd4",
    "app_id":"4"
}
```
- 返回值
``` json
{
    "info":"操作成功！",
    "data":{
        "remark":"æè¿°",
        "name":"ceshi12",
        "creator":"0c2f7a7e623011e792a0005056b361cd",
        "env_name":"çäº§ç¯å¢",
        "apps":"apacheåºç¨",
        "update_time":"2019-01-09 09:25:52",
        "create_time":"2019-01-09 09:25:52",
        "env_id":"11ace0c21dc211e8a9ad4845204d5bd4",
        "type":"TodeMPCluster",
        "id":"80fcfa9a13ad11e99060005056b361cd"
    },
    "success":true,
    "level":"info"
}
```
#### 8.1.5 待绑定主机列表[GET]
- 请求 URL: http://172.17.5.109/api/resource/clusters/{id}/hosts/select/pl?format=json
- 参数：id：集群ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":[
        {
            "ssh_port":"22",
            "host_IP":"172.17.5.104",
            "ssh_user":"root",
            "host_name":"autodeploy3",
            "wait_bind":"True",
            "id":"fbc289083f9111e7a575005056b361cd"
        }
    ],
    "success":true,
    "level":"info"
}
```
#### 8.1.6 集群绑定主机详情[GET]
- 请求 URL: http://172.17.5.109/api/resource/clusters/{id}/hosts?format=json
- 参数：id：集群ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":[
        {
            "ssh_port":"22",
            "host_IP":"172.17.5.104",
            "ssh_user":"root",
            "host_name":"autodeploy3",
            "wait_bind":"False",
            "id":"fbc289083f9111e7a575005056b361cd"
        }
    ],
    "success":true,
    "level":"info"
}
```
#### 8.1.7 绑定主机[POST]
- 请求 URL: http://172.17.5.109/api/resource/clusters/d5b664fb9fad11e8bf26484522225bd4/aos_bind
- 参数：id：集群id
- 请求数据
``` json
{"hosts":["fbc289083f9111e7a575005056b361cd"]}
```
- 返回结果
``` json
{"info":"操作成功！","data":true,"success":true,"level":"info"}
```
#### 8.1.8 解绑主机[POST]
- 请求 URL: http://172.17.5.109/api/resource/clusters/{id}/unbind
- 参数：id：集群ID
- 请求数据
``` json
{"hosts":["fbc289083f9111e7a575005056b361cd"]}
```
- 返回结果
``` json
{"info":"操作成功！","data":true,"success":true,"level":"info"}
```
#### 8.1.9 删除集群[DELETE]
如果删除的是AOS平台和手动创建的集群则允许删除，如果为CMDB同步过来的集群则报错
- 请求 URL: http://172.17.5.109/api/resource/clusters/aos_deletes/{id}?format=json
- 参数：id：集群ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
        "id":"80fcfa9a13ad11e99060005056b361cd",
        "name":"ceshi12"
    },
    "success":true,
    "level":"info"
}
```

#### 8.1.10 编辑集群[POST]
- 请求 URL: http://172.17.5.109/api/resource/clusters/{id}/update
- 参数：id：集群ID
- 请求数据
``` json
{
    "id":"3f6c56711d4e11e99cdb005056c00008",
    "name":"connor0666",
    "remark":"描述",
    "type":"TodeMPCluster",
    "env_id":"11ace0c21dc211e8a9ad4845204d5bd4",
    "app_id":"4"
}
```
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
        "remark":"描述",
        "name":"connor0666",
        "env_name":"生产环境",
        "apps":"apache应用",
        "update_time":null,
        "create_time":null,
        "env_id":"11ace0c21dc211e8a9ad4845204d5bd4",
        "type":"TodeMPCluster",
        "id":"3f6c56711d4e11e99cdb005056c00008"
    },
    "success":true,
    "level":"info"
}
```

-------------------
### 8.2 主机：
#### 8.2.1 获取环境列表[同8.1.2]

#### 8.2.2 获取集群列表[GET]
- 请求 URL: http://172.17.5.109/api/resource/clusters/list_4_select?format=json
- 参数：无
- 返回结果
``` json
{
    "info":"操作成功！",
    "data": [{
            "remark": null,
            "id": "d781053b-8a2e-4cc5-be49-40b826f5d361",
            "name": "TODE-468B"
        },
        {
            "remark": null,
            "id": "512",
            "name": "TODE-479A"
        }]
    "success":true,
    "level":"info"
}
```

#### 8.2.3 新建提交按钮[POST]
- 请求 URL: http://172.17.5.109/api/resource/hosts/aos_create
- 请求数据
``` json
{
    "id":0,
    "host_IP":"1.1.1.1",
    "host_name":"dwadw",
    "remark":"dad",
    "ssh_user":"root",
    "ssh_passwd":"ewew",
    "productLine_id":"4",
    "env_id":"11ace0c21dc211e8a9ad4845204d5bd4"
}
```
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
        "remark":"dad",
        "name":"1.1.1.1",
        "creator":"",
        "ssh_port":"22",
        "env_name":"çäº§ç¯å¢",
        "app":[
        ],
        "productLine_name":"apacheäº§åçº¿",
        "host_IP":"1.1.1.1",
        "create_time":"2019-01-09 10:43:53",
        "ssh_user":"root",
        "host_name":"dwadw",
        "productLine_id":"4",
        "clusters":[

        ],
        "env_id":"11ace0c21dc211e8a9ad4845204d5bd4",
        "id":"66c5cbd813b811e98ffb005056b361cd"
    },
    "success":true,
    "level":"info"
}
```

#### 8.2.4查询提交按钮[GET]
- 请求 URL: http://172.17.5.109/api/resource/hosts/aos_json?format=json&host_name=aa&productLine=4
- 参数：host_name:主机名，productLine:产品线
- 返回结果
``` json
{
    "count": 2,
    "page": 1,
    "results": [
        {
            "remark": "aa",
            "name": "127.0.1.2",
            "creator": "",
            "ssh_port": "22",
            "env_name": "内测环境N",
            "app": [],
            "productLine_name": "apache产品线",
            "host_IP": "127.0.1.2",
            "create_time": "2018-11-14 16:10:49",
            "ssh_user": "aa",
            "host_name": "aa",
            "productLine_id": "4",
            "clusters": [
                {
                    "id": "bfc2bb10e7e411e8b7eb0021cc698915",
                    "name": "ceshi3"
                }
            ],
            "env_id": "11ace0ba1dc211e8a9ad4845204d5bd4",
            "id": "cbb2c2cfe7e411e89abc0021cc698915"
        },
        {
            "remark": "aaa",
            "name": "127.0.1.5",
            "creator": "",
            "ssh_port": "22",
            "env_name": "内测环境N",
            "app": [],
            "productLine_name": "apache产品线",
            "host_IP": "127.0.1.5",
            "create_time": "2018-11-14 16:08:09",
            "ssh_user": "aa",
            "host_name": "aa",
            "productLine_id": "4",
            "clusters": [],
            "env_id": "11ace0ba1dc211e8a9ad4845204d5bd4",
            "id": "6c4a2b80e7e411e89a9d0021cc698915"
        }
    ]
}
```

#### 8.2.5 删除主机[DELETE]
如果删除的是AOS平台和手动创建的主机则允许删除，如果为CMDB同步过来的主机则报错
- 请求 URL: http://172.17.5.109/api/resource/hosts/aos_deletes/{id}?format=json
- 参数：id:主机ID
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
        "id":null,
        "name":"1.1.1.1"
    },
    "success":true,
    "level":"info"
}
```

#### 8.2.6 编辑主机[POST]
- 请求 URL: http://172.17.5.109/api/resource/hosts/{id}/update
- 参数：id:主机ID
- 请求数据
``` json
{
    "id":"e919bc001a0411e98691005056c00008",
    "host_name":"dwadw",
    "remark":"dad",
    "host_IP":"1.1.1.1",
    "ssh_user":"root",
    "productLine_id":"4",
    "env_id":"11ace0c21dc211e8a9ad4845204d5bd4"
}
```
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":{
        "remark":"dad",
        "name":"1.1.1.1",
        "creator":"",
        "ssh_port":"22",
        "env_name":"生产环境",
        "app":[

        ],
        "productLine_name":"apache产品线",
        "host_IP":"1.1.1.1",
        "create_time":null,
        "ssh_user":"root",
        "host_name":"dwadw",
        "productLine_id":"4",
        "clusters":[

        ],
        "env_id":"11ace0c21dc211e8a9ad4845204d5bd4",
        "id":"e919bc001a0411e98691005056c00008"
    },
    "success":true,
    "level":"info"
}
```
----------
#### 8.2.7主机验证[GET]

- 请求 URL: 请求 URL: http://172.17.5.109/api/resource/hosts/validate/{ssh_ip}/{ssh_user}/ssh
- 参数：ssh_ip:主机IP ,ssh_user:系统用户
- 返回结果

```json
{
    "info":"操作成功！",
    "data":false/true,
    "success":true,
    "level":"info"
}
```





## 9 软件包同步[POST]

- 描述：AOS平台只有一个产出物，以压缩包的形式推送给TAD。TAD需要进行解压后遍历全部文件(除了yml、j2)文件全部入库。其中yml，j2。按照TAD现有的功能将其一一匹配后入库，和入仓库
- 请求 URL: http://172.17.5.109/api/artifact/version/aos?app_id={app_id}&version={version}&username={username}&name={name}&md5={md5}
- 参数：app_id:业务ID，version：版本号 name:软件包名字,md5：md5值
- 请求数据(multipart/form-data)
``` json
文件数据
request.args.get
```
- 返回结果
``` json
{
    "info":"操作成功！",
    "data":
        {
            "file_name":"文件名",
            "file_path":"文件路径",
            "md5":"ssewwews232rfsdf",
            "file_id":"文件ID",
            "version_id":"版本ID",
        },
    "success":true,
    "level":"info"
}
```
#### 5.11.1 脚本actifact上传[POST]

- 请求 URL: http://172.17.5.109/api/artifact/script/aos_upload
- 参数 app_id 应用ID，file_md5 每个文件MD5，name脚本版本名
- 请求数据(multipart/form-data)

```json
{
    文件名: (binary)
	app_id: 4
	file_md5: {文件名:文件MD5,文件名:文件MD5}
	name: poiulk
}
```

- 返回结果

```json
{
    "info": "操作成功！",
    "data": [
       {
            "file_name":"文件名",
            "file_path":"文件路径",
            "md5":"ssewwews232rfsdf",
            "file_id":"文件ID",
            "version_id":"版本ID",
        }
    ],
    "success": true,
    "level": "info"
}
```



#### 5.11.1 应用配置actifact上传[POST]

- 请求 URL: http://172.17.5.109/api/artifact/configure/aos_upload
- 参数 app_id 应用ID，file_md5 每个文件MD5，name脚本版本名 ,version版本号
- 请求数据(multipart/form-data)

```json
{
    文件名:(binary)
    文件名:(binary）
	app_id: 4
	file_md5: {文件名:文件MD5,文件名:文件MD5}
	name: poiulkle
	version：版本号
}
```

- 返回结果

```json
{
    "info": "操作成功！",
    "data": [
        {
            "download_path": "http://172.17.5.108:8081/artifactory/configure/d5380000359f11e9b3e12c56dc1edda1/char.j2",（下载路径）
            "md5": "74001ff50947794ff27f6a9680b60a4b",
            "id": "6952bbde35a011e9bacf2c56dc1edda1",（文件ID）
            "artifact_version_id": "d53d301e359f11e9b2b02c56dc1edda1",（版本ID）
            "filename": "char.j2"
        }
    ],
    "success": true,
    "level": "info"
}
```


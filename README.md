# 项目介绍



本系统的使用角色可以被分为管理员、教师和学生

管理员登录进入本系统操作的功能包括查看成绩统计报表信息，管理课题信息，管理课题任务，管理选题申请信息，管理最终成绩信息等。

教师登录进入本系统操作的功能包括查看学生信息，新增课题信息，新增课题任务信息，审核学生上传的阶段性文档，审核选题申请信息，管理最终成绩信息等。

学生登录进入本系统操作的功能包括对课题进行申请，查看课题任务并上传阶段性文档，查看最终成绩信息等。





# 环境要求



1.运行环境：最好是java jdk1.8,我们在这个平台上运行的。其他版本理论上也可以。 

2.IDE环境：IDEA,Eclipse,Myeclipse都可以。推荐IDEA; 

3.tomcat环境：Tomcat7.x,8.X,9.x版本均可 

4.硬件环境：windows7/8/10 4G内存以上；或者Mac OS; 

5.是否Maven项目：是；查看源码目录中是否包含pom.xml;若包含，则为maven项目，否则为非maven.项目 

6.数据库：MySql5.7/8.0等版本均可；





# 技术栈



运行环境：jdk8 + tomcat9 + mysql5.7 + windows10

服务端技术：SpringBoot + MyBatis + Vue + Bootstrap + jQuery





# 使用说明





1.使用Navicati或者其它工具，在mysql中创建对应sq文件名称的数据库，并导入项目的sql文件； 

2.使用IDEA/Eclipse/MyEclipse导入项目，修改配置，运行项目； 

3.将项目中config-propertiesi配置文件中的数据库配置改为自己的配置，然后运行；





# 运行指导

idea导入源码空间站顶目教程说明(Vindows版)-ssm篇：

http://mtw.so/5MHvZq 

源码地址：[http://www.codegym.top](http://www.codegym.top/)





# 运行截图![springboot197基于springboot的毕业设计系统的开发0](https://img-blog.csdnimg.cn/img_convert/e62ed8f72d3eb9d8d397fb5f96d01a7f.png)

![springboot197基于springboot的毕业设计系统的开发1](https://img-blog.csdnimg.cn/img_convert/7947787a1b4fb6da9d65b616d797cc03.png)

![springboot197基于springboot的毕业设计系统的开发2](https://img-blog.csdnimg.cn/img_convert/bb8539db63afc58d3082f4ff475872e7.png)

![springboot197基于springboot的毕业设计系统的开发3](https://img-blog.csdnimg.cn/img_convert/2bf1efd16562ad906ac1237c136c4518.png)

![springboot197基于springboot的毕业设计系统的开发5](https://img-blog.csdnimg.cn/img_convert/a18d5d741f0bd79c75e70bce8845c2bd.png)

![springboot197基于springboot的毕业设计系统的开发6](https://img-blog.csdnimg.cn/img_convert/e73e49b2b9d7134329951be720e29322.png)

![springboot197基于springboot的毕业设计系统的开发7](https://img-blog.csdnimg.cn/img_convert/a85e8086937228e92cbafd958d2f3146.png)

![springboot197基于springboot的毕业设计系统的开发8](https://img-blog.csdnimg.cn/img_convert/8b3c9124b8559716efa5ee16fdd12668.png)

![springboot197基于springboot的毕业设计系统的开发9](https://img-blog.csdnimg.cn/img_convert/d1bb2658e8cefefd7365b785dd67dc07.png)

![springboot197基于springboot的毕业设计系统的开发10](https://img-blog.csdnimg.cn/img_convert/929679136f124b66b7caf90bd43d8661.png)




### 代码

```java

    /**
     * 后端列表
     */
    @RequestMapping("/page")
    public R page(@RequestParam Map<String, Object> params,CaipinxinxiEntity caipinxinxi,
		HttpServletRequest request){
        EntityWrapper<CaipinxinxiEntity> ew = new EntityWrapper<CaipinxinxiEntity>();
		PageUtils page = caipinxinxiService.queryPage(params, MPUtil.sort(MPUtil.between(MPUtil.likeOrEq(ew, caipinxinxi), params), params));

        return R.ok().put("data", page);
    }
    
    /**
     * 前端列表
     */
	@IgnoreAuth
    @RequestMapping("/list")
    public R list(@RequestParam Map<String, Object> params,CaipinxinxiEntity caipinxinxi, HttpServletRequest request){
        EntityWrapper<CaipinxinxiEntity> ew = new EntityWrapper<CaipinxinxiEntity>();
		PageUtils page = caipinxinxiService.queryPage(params, MPUtil.sort(MPUtil.between(MPUtil.likeOrEq(ew, caipinxinxi), params), params));
        return R.ok().put("data", page);
    }

	/**
     * 列表
     */
    @RequestMapping("/lists")
    public R list( CaipinxinxiEntity caipinxinxi){
       	EntityWrapper<CaipinxinxiEntity> ew = new EntityWrapper<CaipinxinxiEntity>();
      	ew.allEq(MPUtil.allEQMapPre( caipinxinxi, "caipinxinxi")); 
        return R.ok().put("data", caipinxinxiService.selectListView(ew));
    }
```




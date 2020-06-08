<!--
 * @Author: joker.zhang
 * @Date: 2020-04-16 15:49:59
 * @LastEditors: joker.zhang
 * @LastEditTime: 2020-06-08 11:29:14
 * @Description: For Automation
 -->

PythonWeb接口开发与测试学习笔记

# Django开发模式MTV模式 
Django的开发模式是MTV模式，想了解MTV模式，我们需要先了解MVC模式。
MVC模式是把数据存取逻辑、 业务逻辑和表现逻辑组合在一起的概念有时被称为软件架构的 Model-View-Controller(MVC)模式的概念有时被称为软件架构的 Model-View-Controller(MVC)模式

* Model 代表数据存取层
* View 负责系统中选择显示什么/如何显示的功能
* Controller 指的是系统中根据用户输入并视需要访问模型， 以决定使用哪个视图的那部分

在Django里面，C由Django框架自行处理，Django框架根据URLconf设置，对给定URL调用适当的Python函数。
* M代表模型（Model） ， 即数据存取层。 该层处理与数据相关的所有事务： 如何存取、 如何验证有效
* T代表模板(Template)， 即表现层。 该层处理与表现相关的决定： 如何在页面或其他类型文档中进行显示
* V代表视图（View） ， 即业务逻辑层。 该层包含存取模型及调取恰当模板的相关逻辑。 你可以把它看作模型与模板之间的桥梁作模型与模板之间的桥梁作模型与模板之间的桥梁

# Django流程

![django流程](..\images\django流程.png
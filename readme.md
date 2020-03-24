## 个人信息
- 刘程源/男/1991
- 专/软件技术
- 工龄始于: 2011年
- Github: http://github.com/glimis 
- 母语: java
- 期望岗位: 前端

## 经历简述
- 大学+高中期间
  
  建立并维护地方论坛网站,拿来万岁
- 2011年
  
  在广州做java/asp开发, ssh + ext

    技术:
    ssh + ext

    详情:
    1. sql调优 【sqlserver/oracle】
    2. spring 【自行研发sbring,提供更轻的方式】
    3. 浏览器兼容 【ie6-8,ext】
    4. 开发框架Call 【调用存储过程,减少业务代码,提供热更新】
    5. 开发框架CallSql 【通过ajax,新增或修改存储过程】
    6. 基于Call与CallSql 配合工作流引擎,开发元数据开发平台

- 2013

  原公司破产,到北京,国企性质,大型项目,工作重心主要在第三方插件/厂商的对接与开发

    1. highchair 
    2. FineRepor/帆软 报表
    3. petrel 三维地质建模 
    4. silverlight  富前端
   
  在首次使用bootstrap,快速搭建项目介绍页面后,工作重心逐渐转向重构页面

    1. 使用avalon,而非静态资源的彻底分离js提供前端mvvm【兼容ie6】
    2. 重构首页 【原来由iframe拼接各个项目组的首页实现】
    3. 主导js的彻底分离 【css已经分离,但js依赖i18n文本,初始化数据,需要提供解决方案】
    4. 提供mvvm组件 
    5. 开发loader系列,解决新按需加载问题 【参考easy/ext-loader】
    6. 开发Max,用于进行统计 【js版与java版,针对前端包含元数据,但自定义统计的情况】
    7. 开发towcat,深度学习jsp,以针对前端优化       

- 2015
  
  创业团队,包含独立的前端团队
  
  技术:
    handlebars + backbone + seajs + 自定义组件
      
  详情:
    1. 基于easyui,快速搭建工作台
    2. 基于angular,搭建教师录题  【用于技术尝试】
    3. 基于react,开发公司首页  【用于技术尝试】
    4. 开发教师端  【handlebars + backbone】
    5. 开发Formula  【初高中数学公式的词法分析器,旨在前端canvs绘制公式】
    6. 开发scanpy 【基于python的爬虫】
    7. 开发wordExport 【基于word进行题目的导入】
    8. 开发clean 【对爬虫与导入的题库,进行防伪的删除】

- 2016
  
  用友云彩项目组

    技术:
      knockout + iuap[集团库]

    详情:

    1. 开发i18n  【临时解决中英文切换】
    2. chrome 插件 解决项目交互

- 2018
  
  在家带娃,接项目

    技术:
      gen [根据模型,创建代码生成器]

- 2019 
  
    回北京,第一家公司,第一个月解决公司从0.5到1的项目无法上线和使用的问题,第二个月实现线上开发任务,包括

    集中卡顿与白屏
      
    问题 
      
    1. 静态资源无压缩
    2. 图片gif
    3. 服务器东京
    4. api新老混用,无文档
    5. 同一个接口加载多次

    首屏资源加载完,需要2min,10++s后才退出白屏,资源超过2M,调用接口76个

    解决

    1. webpack重构
    2. oss加速   【调整上线流程】
    3. api 缓存
    4. 关键代码 重构


    首屏加载3 - 5s 【东京服务器】,10s 加载完毕

    盘口/交易中心 卡顿
    
    原因

    1. socket,1s接受100条返回  
    2. 1条数据 8k
    3. socket 没有 abort,对于切换,会产生乱序

    解决
    
    1. 前端防抖
    2. 增加node服务,提供socket abort,修改socket结构 【arraybuffer】


    国际化方案
    
    1800个字段,增加繁,英,日,俄,韩

    问题:

    1. 大面积没有使用标签站位  【webpack自动替换】
    2. 翻译文档混乱   【修改流程】
    3. 标签可能没有使用模板  【指语义,文案中间有数字等情况,手改】
    
    解决:
    重构i18n流程

    1. 前端通过提供excel
    
    包含字典路径,key,中文模板[带{},后续翻译也需要带]]

    2. 文件上传到公共平台

    3. pm修改文案,但不修改路径/KEY/模板{}内容

    4. 下载后,更新

    

## 个人项目
- sbring [2012]
  
  用来研究spring,并提供更简单的配置方式

  项目组有很多需求需要打成jar包的服务【如运行期增加的定时任务,数据转移,提供固定的第三方服务】,需求是copy后可立即执行【自带依赖】,依赖spring会使jar过大【有些代码可以copy】,最终根据spring的风格和所需要的特性,产生了该项目
 
- Call [2013]
  
  项目组项目比较分散,每个季度都会开新项目,新项目为基于基础项目工程进行开发,技术架构保持不变
  
  维护痛点是actions爆炸【包括数量与文件大小】,根源是弱service思想,即service只是代理dao的一层,目的是减少复用,减少一个业务跳转的长度,在面对维护和业务更新时,不会照成大规模破坏

  Call符合了原有的开发模式,将具体的业务,完全交给了`存储过程`,思路如下
  
  1. 一个超级接口actions 
  2. 根据参数,选择并执行存储过程
  3. 业务实现在存储过程中

  这种高耦合的反模式,在需求不明确,模型不明确时,可以提供更快的对接开发效果,也可以提供一定的热更新的能力
  
  另外,更快的业务开发,提供了大量时间,用于关注前端【ext】

- CallSql [2013]

  通过后台管理的页面,维护整个数据库的存储过程

  为所有人提供了简单热部署的能力,而非通过运维/dba【没有服务器密码】,进行存储过程的修改

- loader [2014]

  解决内部组件,依赖的问题,组件风格参考easyui,loader参考ext/easyui

- Max [2014]

  提供前端元数据统计的计算能力【highchair有相同的能力】,主要针对动态table设置统计的所依赖的库

- Towcat [2014]

  深度了解tomcat,以优化前端,此时,前端依然是jsp+avalon,而非静态资源的彻底分离,了解tomcat后,实施以下工作

    1. js的彻底分离  【js加速】
    2. input隐藏框存储初始化数据,替代将数据存储在js中 【提供试图数据与js分离的方式,且初始化数据存在试图中,减少ajax交互】
    3. 提供前端i18n工具,解决后端i18n问题 
        i18n的字典有两类,一类为组件库提供,如easyui ,在js与html分离前,国际化标签直接写在js中,要求分离后,将需要的字典,注入到隐藏的input中,前端通过i18n工具,代替原来的占位符
    4. 提供java命令的压缩方案 【ant,grunt无法普及】
    5. 提供cookie库 【解决cookie冲突的问题】

- Formula [2015]

  教师录题时的公式,使用截图的方式进行快速处理,包含以下问题
    1. 通常白底而非透明
    2. 大小与清晰度受限,难以调节
    3. 换行
  此处希望产生统一标准的透明底色图片,在换行时,可以缩写,点击后放大图片
  第一版时,使用公式编辑器【使用UEditor/KityFormula】,可以解决上述问题,但录入过慢,此项目希望使用Formula的公式,直接生成图片或canvs
  结构上分两部分,第一部分分析器【词法Formula的公式】,分析公式,第二部分解释器,根据ast,绘制canvs
  词法分析已完成,生成canvs时,花费时间过多
  第二版计划使用MathML 【由词法直接产生对应的tag,兼容性暂定】
  第三版通过api【java生成图片】的方式解决 【Formula的公式为标准公式】


- ext [2016]

  https://github.com/Glimis/ext  

  ext普及/教程

- discard-react-demo [2016]

  https://github.com/Glimis/discard-react-demo

  react0.13 技术选型时的记录,开发的一些小工具

- discard-chrome [2016]

  https://github.com/Glimis/discard-chrome

  chrome插件

  1. jd爬虫

    项目组需要选择行的获取jd的数据,1000条,每人手填50条,写爬虫没有必要,此处使用chrome插件,抓取选中的jd页面数据,而后填写如云彩数据页面中,进行录入
  
  2. bug导航

    通过chrome插件,第一时间获取bug数 【chrome插件,启动后10min抓取一次Jira数据做推送】
    后续包括,通过chrome自动提交解决描述,发送部署邮件,发送日报等

- jq-modal [2017]

  https://github.com/Glimis/jq-modal

  组内有很多模态框,分散在个个业务文件夹内,在业务拓展时,要求对模态框进行复用 [通过工程,而非重构来解决]

  特点
    1. 包括layer,bootstrap/jq,iuap三类
    2. 分散在不同工程或文件夹内
    3. 可能并非单独的组件
    4. 可能有样式/属性冲突
    5. webpack还没有普及
    6. 组件化没有普及
   
  解决
    1. 提供全局配置,读取需要共享的模态框依赖 [针对并非单独的情况,必须提取,对于配置,默认使用绝对路径]
    2. 提供通用的加载器,统一三类调用方式
    3. 提供iframe加载方式,解决样式或属性污染
    4. 提供动态模态框开发流程,包括vue/knockout
        针对vue,动态加载依赖文件后,动态加入body内,重新生成vue实例,copy主vue实例的vuex属性


- i18n [2016]

  https://github.com/Glimis/discard-translate
    有道翻译
  https://github.com/Glimis/discard-i18n
    根据字典,进行中英文替换
  https://github.com/Glimis/discard-webpack-i18n
    通过webpack,生成en.js/en.html

  临时的需求,要在一周内,对组内所有页面提供大范围的前端中英文转换功能 
  
  问题
    1. 页面多,前端中文涉及到js/html页面 [涉及文件500+]
    2. 待翻译内容多 [不限制翻译,突破有道一小时翻译上限]
    3. 使用的组件多,且大多不提供国际化的支持 [包括jq系列插件,自定义插件以及iuap插件]
    4. 部分静态资源必须通过api获取 [指城市,国家等静态信息]

  解决思路
    1. 第一阶段 - 全面覆盖
      对所有js,html提供zh/en版
    2. 第二阶段 - 针对特殊组件与接口,单独优化
      如国家/城市,改为静态资源包的格式
    3. 第三阶段 - 抽出字典
      效果通过后,抽出字典,将原来中文转换为占位符
      对每一个js/html提供相应的语言包
    4. 第四阶段 - 字典文件合并,减少http请求
      对较小文件的字典,直接生成在组件内部
  

- 云彩前端 [2017]

  https://github.com/Glimis/books
  前端普及

- gen [2018]

  https://github.com/Glimis/gen
  快速生成初始化代码

- vue 资料

  https://github.com/Glimis/vue-doc
  
- webpack4 资料

  https://github.com/Glimis/webpack4

- Compiler

  https://github.com/Glimis/Compiler

  编译原理相关

  ast用的比较多,比如Max 【练手】,Formula,gen

- 浏览器/http协议相关
  
  https://github.com/Glimis/Brower


  

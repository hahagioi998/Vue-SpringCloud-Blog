## 基于Vue+SpringCloud博客的设计与实现---微服务基础版本组件1.0版本
博客采用Vue+SpringCloud前后分离的方式。博客采用了高可用Eureka（可以替换成其他微服务组件）以及高可用Zuul，使用以Es搜索引擎作为Zpkin的存储方式去跟踪定位博客的微服务的Api指标，微服务之间负载均衡使用Feign接口，整个项目均写了回退不会发生级联效应。
***
## 项目的亮点
所有互联网常用的代表中间件均涉及使用，基本是一个完整的全栈项目，整个博客用的是微服务架构设计与分布式部署方式，整体代码均有注释，并且扩展方便，最终部署的方式需要采用Docker方式。
***
## 博客的功能介绍
* 用户的个人中心：用户的登录与注册的Token验证，前后拦截器拦截Token。拼图，阿里云智能验证，动态加载JS，控制Token也可以在Zuul路由上操作。
* 用户安全中心：SMTP邮箱注册邮箱，阿里云短信API注册手机以及其他个人安全信息和调用安全认证服务的接口，安全完成度最全。
* 用户文件头像上传中心：博客所用到的所有的图片和用户的图片均用阿里云OSS文件服务器，外网url，也可以采用本地机器存储。
* 用户签到中心：持续签到和累计签到奖励机制，以及会员导致经验值增益不同的机制，博客每日任务，排名特权，基本按照贴吧写的。
* 用户会员中心：SVIP与VIP，定时任务/RabbitMQ延迟队列/登录验证三种判定会员截止时间到期用邮箱去提醒
* 用户支付中心：我的钱包和支付宝支付以及打印我的账单，内网穿透获得异步通知作为结果判定标志，原始支付的普通会员，二维码支付的超级会员，账单分页，Csv定制，消费图，优惠券，基于RabbitMQ/Redis两种实现的延迟队列
* 用户博客中心：发布，更新，删除，评论，点赞，收藏，转发，排行榜已经完成。博客中心是博客的核心，分页和轮滑加载均实现，用Redisson来实现分布式锁控制文章
* 搜索引擎中心：文章提示信息的增删改查，分页，高亮模糊排序查询
* 用户的消息中心：websocket聊天与用户的所有个人消息
* 用户的个人空间：这个会涉及到个人博客空间与博客好友，博客云会控制上传和下载文件，会员会有速度特权，类似百度云，后续会完成上传。
## 项目涉及到的技术
*  前端：node+npm+vue+axios+三个常用的UI组件+v-charts图表
*  后端：Java+SpringCloud（微服务工具集）+SpringBoot
*  数据库： Mysql，任意选择数据库导入相应的连接包即可。
*  中间件：Mybatis（分页插件）+Redis（缓存缓解流量）+Redisson（分布式锁）+RabbitMQ（延迟队列）+Elasticsearch（高亮分页排序）+websocket（监听连接传送数据）
*  支付：写了支付宝，后续有时间会完善微信，一共有支付宝原始支付与二维码支付
*  跟踪：Zipkin（分布式跟踪）+Elasticsearch存储，也可以使用SQL数据库存储。
#  项目的总结
1. 整体的完成度相对高，但是后续有时间还会继续完善，扩展补充好的创意。
2. 会把整体的版本包迭代到最新的微服务组件。

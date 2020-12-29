# 艺术平台
前端采用vue框架搭建<https://github.com/MJLee00/PlatFormForArtist>
后端使用 **SSM* , *Rocket MQ*  *Spring Security Oauth 2.0* *Redis*, *Msql* ,*Elastic Search*
# 需求分析
现传统艺术的传承，艺术品鉴定很困难，本项目开发一个线上教学平台，学生老师可以互动展示自己的作品，老师可以发布招募令
学生可以进行拜师申请从而进行双选，教师通过线上教学待学生完成教学要求后可以颁发传承令牌完成艺术传承人的认定。
用户也可以通过此艺术平台上传艺术品照片进行人工智能鉴定。
管理员可以对教师资格审批，用户管理，首页轮播图管理等等。
#技术总体架构图
![image](https://note.youdao.com/yws/api/personal/file/41D47FBFCFF24E85874D96CF0578364C?method=download&shareKey=32b9ce949f841750f998bdfa10e72fae)




#服务功能
|  服务名称  | 端口号 | 功能 |
|  ----  | ----  |  ----|
|  pp-service-oauth | 40400      | 用户登录认证返回cookie和token，第一次获取短令牌和cookie，进行第二次访问redis获取长令牌|
|  pp-govern-gateway  |  60201     | 用户进行后端微服务访问，RPC调用微服务 |
|  pp-service-source  |  8888/9999     |  资源服务器，可以根据长令牌中的权限进行过滤|
| pp-govern-center|40401/40402|微服务注册中心，用于监听各个微服务的状态，使得各个服务之间可以进行互相调用|
| pp-service-ucenter| 40300|用于获取从pp-service-oauth服务中进行的远程调用请求，返回用户信息，给oauth进行验证|


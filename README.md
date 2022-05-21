# ManagementBackgroundInterface
### 管理后台界面
- 开发环境：java1.8,node16.14,npm8.6,@vue/cli5.0,idea2019.3,mysqlserver8.0
- 实现技术：vue3,vuerouter,vuex,element-plus,springboot,mysql,mybatisplus,axios,hutool
- Spring Boot模块：Spring Web,MySQL Driver,Lombok,MyBatis Framework
- 实现功能：前后端分离实现后台管理页面及操作
- 前端端口为8080，后端端口为9090

##### 数据库准备
- 创建一个新的数据库命名为"springboot-vue"(或为其他名称，若为其他名称需要手动修改spring.datasource.url),字符集utf8mb4,排序规则unf8mb4_unicode_ci
- 新建表user:id(int,主键,非空,自增),username(varchar,255),password(varchar,255),nick_name(varchar,255),age(int),sex(varchar,255),address(varchar,255)
- 修改spring.datasource.password为你的数据库密码

##### 运行在本地
- 后端：使用idea导入springboot目录，初始化maven，运行即可
- 前端：npm i后使用npm run serve启动即可

By：tyza66(洮羱芝闇)

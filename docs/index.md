# Welcome to JH

[Getting Started with JHipster on OS X](https://dzone.com/articles/getting-started-jhipster-os-x)

## 初级

### 确定版本

    ➜  ~ rm '/usr/local/bin/jhipster'
    ➜  ~ brew link --overwrite jhipster
    Linking /usr/local/Cellar/jhipster/4.14.3... 1 symlinks created
    ➜  ~ jhipster --version
    Using JHipster version installed globally
    4.14.3

#### (一)升级到4.14.4版本

    brew upgrade jhipster
    jhipster --version
    Using JHipster version installed globally
    4.14.4   

#### (二)原有项目从4.14.3升级到4.14.4

```
rm -rf node_modules
rm yarn.lock

jhipster
overrite package.json(选择覆盖此文件)
overrite DatabaseConfiguration.java(选择覆盖此文件)
根据提示选择性的覆盖原有文件 如 pom.xml等文件

jhipster --version
Using JHipster version installed locally in current project's node_modules
4.14.4
注意:此步骤是确定项目中的版本
```

  



### 加速三步骤

#### pom.xml

  [阿里云代理](https://www.cnblogs.com/xinhudong/p/7804968.html)

#### nodejs 代理

  [npm 淘宝](https://npm.taobao.org/)

#### pathmanjs 迅雷下载

    yarn start 过程中 会下载 phantomjs-2.1.1-macosx.zip包，该包体积较大，国内仅能从迅雷下载，然后拷贝到对应目录中

[参考图片](https://github.com/StayHungryStayFoolish/Images-Blog/blob/master/jhipster/1522214654527.jpg)

## 中级

### 简单JPA生成代码

#### 根据表 生成实体

  jhipster entity <entityName> --[options]

### 一个较为复杂的例子

* 1、创建此 dsl 文件 [complex_jdl.jdl](https://github.com/jnuc093/jhipster-sample-app/blob/master/src/main/resources/dsl/complex_jdl.jdl)

* 2、jhipster import-jdl  complex_jdl.jh

[jdl-studio](https://start.jhipster.tech/jdl-studio/)

### 目录命名规则

### 增量开发流程

[database-updates-with-the-maven-liquibasediff-goal](http://www.jhipster.tech/development/#database-updates-with-the-maven-liquibasediff-goal)

#### 数据库更新 三种工作方式

#### 1、以entity sub-generator方式

#### 2、以liquibase:diff goal方式

#### 3、以编辑change log文件(修改字段...)方式

* 修改JPA实体(添加字段、修改关系)

* 新建 "change log"文件 如:20141006152300_added_price_to_product.xml

* 将上一步文件放到 master.xml文件中，重启生效。

#### profile的使用方式

### 角色与授权

[add ROLE_MANAGER](https://stackoverflow.com/questions/32436745/using-roles-in-jhipster)

[Spring Data REST + Spring Security](https://github.com/spring-projects/spring-data-examples/tree/master/rest/security)

## 高级

### docker启动

### kafka

* 程序启动报错

    Parameter 0 of constructor in com.sgcc.syn.messaging.ProducerResource required a bean of type 'com.sgcc.syn.messaging.ProducerChannel' that could not be found.

在 MessagingConfiguration 类里

    @EnableBinding(value = {Source.class, ProducerChannel.class, ConsumerChannel.class})
    public class MessagingConfiguration {
    
    }

* 消息未订阅成功

配置文件 application-dev.yml 添加以下内容

    bindings:
                messageChannel:
                    destination: greetings
                    content-type: application/json
                subscribableChannel:
                    destination: greetings


### websocket

#### 例子

    访问http://127.0.0.1:9000/#/jhi-tracker,在另一个浏览器进行登录或者退出观察前一个浏览器变化。

### cache缓存

## 升级

### 已有项目升级 生成器从从4.14.1升级到 4.14.3

    * rm -rf nodemodule
    * yarn install

For full documentation visit [mkdocs.org](http://mkdocs.org).

### gateway 网关 eureka

mac:

  bootstrap.yml 文件中修改 eureka地址为 192.168.99.100
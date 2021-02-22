# 一、前言

学习技术的方法

掌握用法；深入理解；不断实践；反复总结；再次深入理解与实践。

官方网站：https://spring.io/

# 二、概述

## 1、Spring是什么

Spring是一个开源框架，为了解决企业应用开发的复杂性而创建的，现在已经不止应用于企业应用。

* Spring是一个轻量级的控制反转（IOC）和面向切面（AOP）的容器框架
  * 从大小与开销两方面而言Spring都是轻量的
  * 通过控制反转（IOC）的技术达到松耦合的目的
  * 提供了面向切面编程的丰富支持，允许通过分离应用的业务逻辑与系统级服务进行内聚性的开发
  * 包含bean管理应用对象的配置和生命周期，这个意义上是一种容器
  * 将简单的组件配置、组合成为复杂的应用，这个意义上是框架

## 2、为什么用Spring

* 在Spring上开发应用简单
  * 把对象创建、销毁以及整个生命周期都交给spring管理
* 在Spring上开发应用方便
  * 对象管理交给spring，使用的时候只需要告诉spring需要用什么实例，spring返回对应的实例。
* 在Spring上开发应用快捷
  * spring管理对象（bean），省去了创建、销毁等过程。

## 3、spring作用

* 容器
* 提供了对多种技术的支持
  * JMS
  * MQ支持
  * UnitTest
  * 。。。
* AOP（事务管理、日志）等
* 提供了众多方便应用的辅助类（JDBC Template等）
* 对主流应用框架（Hibernate等）提供了良好的支持

## 4、适用范围

* 构建企业应用（SpringMVC+Spring+Hibernate/ibatis）
* 单独使用Bean容器（Bean管理）
* 单独使用AOP进行切面管理
* 其他的Spring功能，如：对消息的支持等。

# 三、IOC

##  1、接口及面向接口编程

接口是对外的声明，说明会提供哪些功能，内部实现对外不公开；

接口、抽象类、普通类。接口只能有声明，不能有实现；抽象类既可以有声明也可以有实现。

面向接口编程：各层间仅依赖接口而非实现类，这样可以保证接口实现的变动不影响各层间的调用。

## 2、什么是IOC

IOC（Inverse of Control)：控制反转，

* 控制权的转移，应用程序本身不负责依赖对象的创建和维护，而是由外部容器（Spring）负责创建和维护。
* 获得依赖对象的过程由自身管理变为了由IOC容器主动注入。

DI（Dependency injection）：依赖注入

* 是IOC的一种实现方式。
* 就是由IOC容器在运行期间，动态地将某种依赖关系注入到对象之中

目的是 创建对象并且组装对象之间的关系。

IOC中将所有对象都称为bean。

## 3、Spring的Bean配置

spring配置有两种方式：

* 对xml文件的配置；

  * 在xml文件中配置，一般叫applicationContext.xml，格式如下：

  * ```<xml></xml>
    <beans>
    <bean id="" class=""></bean>
    </beans>
    ```

  * 其中，id是对bean的唯一标识，class指要应用的类。

* 注解

## 4、Bean的初始化

bean容器初始化

* 基础：两个包
  * org.springframework.beans  --加入依赖 pom.xml
  * org.springframework.context  --pom.xml
  * BeanFactory提供配置结构和基本功能，加载并初始化Bean
  * ApplicationContext保存了Bean对象并在Spring中被广泛使用 --applicationContext.xml
* 初始化ApplicationContext方式
  * 本地文件 FileSystemXmlApplicationContext
  * Classpath  ClassPathXmlApplicationContext
  * Web应用中依赖servlet（ContextLoaderServlet）或Listener（ContextLoaderListerner）--web.xml

## 5、Spring的常用注入方式

* spring注入是指在启动spring容器加载bean配置的时候，完成对变量的赋值行为

  IOC负责加载bean，并实例化；注入是在创建过程中完成赋值；

* 常用的两种注入方式：

  * 设值注入（set方式注入）

    * ```xml
      <bean id="injectionService" class="com.imooc.ioc.injection.service.InjectionServiceImpl"> 
               	<property name="injectionDAO" ref="injectionDAO"></property> 
      </bean> 
      <bean id="injectionDAO" class="com.imooc.ioc.injection.dao.InjectionDAOImpl"></bean>
      ```

    * injectionService对应的类是InjectionServiceImpl，在这个方法中有一个属性是injectionDAO，injectionDAO对应InjectionDAOImpl类。InjectionDAOImpl对injectionDAO进行实例化赋值，自动调用类的set方法，对属性赋值。

    * serviceImpl中需要定义injectionDAO这个变量，并写对应的set方法。

  * 构造注入（构造方式注入）

    * ```xml
      <bean id="injectionService" class="com.imooc.ioc.injection.service.InjectionServiceImpl">
             <constructor-arg name="injectionDAO" ref="injectionDAO"></constructor-arg>
      </bean>
      <bean id="injectionDAO" class="com.imooc.ioc.injection.dao.InjectionDAOImpl"></bean>
      ```

    * InjectionServiceImpl中有injectionDAO的构造方法

    * serviceImpl中需要定义构造方法，参数为injectionDAO

DAO负责数据库访问；service完成业务逻辑处理，调用dao把最终的数据保存到数据库。

# 四、Spring Bean装配

## 1、Bean配置项

* Id
  * IOC容器中bean的唯一标识
* Class
  * 具体要实例化的哪个类
* Scope
  * 范围，作用域
* Constructor arguments
  * 构造器参数  --Spring注入：构造器注入
* Properties
  * Spring注入：设值注入
* Autowiring mode
  * 自动装配模式
* Lazy-initialization mode
  * 懒加载模式
* Initialization/destruction method
  * 初始化/销毁的方法

## 2、Bean的作用域

* singleton：单例，指一个Bean容器中只存在一份
* prototype：每次请求（每次使用）创建新的实例。
* request
* session：
* global session：

例子：

```xml
 <bean id="beanScope" class="com.imooc.bean.BeanScope" scope="singleton"></bean>
 <bean id="beanScope" class="com.imooc.bean.BeanScope" scope="prototype"></bean>
```

## 3、Bean的生命周期

* 定义  xml文件

  ```xml
  <!-- beans里定义的是全局的，默认的，需要类中定义这两个defautInit、defaultDestroy方法 -->
  <beans xmlns="http://www.springframework.org/schema/beans"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.springframework.org/schema/beans
          http://www.springframework.org/schema/beans/spring-beans.xsd" 
          default-init-method="defautInit" default-destroy-method="defaultDestroy">
          
  <!-- 针对单个bean定义，类中需要定义start和stop方法
          <bean id="beanLifeCycle" class="com.imooc.lifecycle.BeanLifeCycle"  init-method="start" destroy-method="stop"></bean>
  -->
    <!-- 实现初始化和销毁的接口：InitializingBean, DisposableBean-->
      <bean id="beanLifeCycle" class="com.imooc.lifecycle.BeanLifeCycle"></bean>
  
   </beans>
  ```

  

* 初始化

  ```java
  public class BeanLifeCycle implements InitializingBean, DisposableBean {
  	
  	/*public void defautInit() {
  		System.out.println("Bean defautInit.");
  	}
  	
  	public void defaultDestroy() {
  		System.out.println("Bean defaultDestroy.");
  	}*/
  
  	@Override
  	public void destroy() throws Exception {
  		System.out.println("Bean destroy.");
  	}
  
  	@Override
  	public void afterPropertiesSet() throws Exception {
  		System.out.println("Bean afterPropertiesSet.");
  	}
  	
  /*	public void start() {
  		System.out.println("Bean start .");
  	}
  	
  	public void stop() {
  		System.out.println("Bean stop.");
  	}*/
  	
  }
  ```

* 使用

  ```java
  @RunWith(BlockJUnit4ClassRunner.class)
  public class TestBeanLifecycle extends UnitTestBase {
  	
  	public TestBeanLifecycle() {
  		super("classpath:spring-lifecycle.xml");
  	}
  	
  	@Test
  	public void test1() {
  		super.getBean("beanLifeCycle");
  	}
  	
  }
  ```

* 销毁

@before->@test->@after

```
@before中是执行前要执行的方法，加载xml文件，创建上下文。启动之后，会查找配置文件中配置的信息，并把bean信息解析装载到spring的上下文（context）。
```

## 4、SpringBean装配之Aware接口

* ApplictionContexAware

  ```xml
  <bean id="moocApplicationContext" class="com.imooc.aware.MoocApplicationContext" ></bean> 
  ```

  ```java
  public class MoocApplicationContext implements ApplicationContextAware  {
  	
  	@Override
  	public void setApplicationContext(ApplicationContext applicationContext)
  			throws BeansException {
  		System.out.println("MoocApplicationContext : " + applicationContext.getBean("moocApplicationContext").hashCode());
  	}
  	
  }
  ```

* BeanNameAware

  ```xml
  <bean id="moocBeanName" class="com.imooc.aware.MoocBeanName" ></bean>
  ```

  ```java
  public class MoocBeanName implements BeanNameAware, ApplicationContextAware {
  
  	private String beanName;
  	
  	@Override
  	public void setBeanName(String name) {
  		this.beanName = name;
  		System.out.println("MoocBeanName : " + name);
  	}
  }
  ```

## 5、SpringBean装配之自动装配

* No：不做任何操作
* ByName：根据属性名自动装配  --和id有关
* ByType：根据属性类型自动装配 --和class有关
* Constructor：应用于构造器参数  --和class有关

在beans中有个属性为autowire，属性值可以为：byName，byType，Constructor

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd" 
        default-autowire="byName">
        <bean id="autoWiringService" class="com.imooc.autowiring.AutoWiringService" ></bean>        
        <bean id="autoWiringDAO" class="com.imooc.autowiring.AutoWiringDAO" ></bean>	
 </beans>
```

在dao的类中定义方法，比如say()，service中定义dao，生成set方法，定义say方法  --ByName/ByType。

```java
public class AutoWiringService {
	
	private AutoWiringDAO autoWiringDAO;
	
  // Constructor
	/*public AutoWiringService(AutoWiringDAO autoWiringDAO) {
		System.out.println("AutoWiringService");
		this.autoWiringDAO = autoWiringDAO;
	}*/

	public void setAutoWiringDAO(AutoWiringDAO autoWiringDAO) {
		System.out.println("setAutoWiringDAO");
		this.autoWiringDAO = autoWiringDAO;
	}
	
	public void say(String word) {
		this.autoWiringDAO.say(word);
	}
}
```

##  6、Spring Bean装配之Resources

* Resources：针对于资源文件的统一接口
  * UrlResource
  * CalssPathResource
  * FileSystemResource
  * ServletContextResource
  * InputStreamResource
  * ByteArrayResource

* ResourceLoader：对Resource进行加载的类，所有ApplicationContext都实现了ResourceLoade这个接口，以下是前缀
  * classpath:
  * file:
  * http:
  * none

```xml
<bean  id="moocResource" class="com.imooc.resource.MoocResource" ></bean>
```

```java
public class MoocResource implements ApplicationContextAware  {
	
	private ApplicationContext applicationContext;
	
	@Override
	public void setApplicationContext(ApplicationContext applicationContext)
			throws BeansException {
		this.applicationContext = applicationContext;
	}
	
	public void resource() throws IOException {
//		Resource resource = applicationContext.getResource("classpath:config.txt");
//		Resource resource = applicationContext.getResource("file:/Users/xuleping/xlpitm/Spring/src/main/resources/config.txt");
//		Resource resource = applicationContext.getResource("url:https://spring.io/quickstart");
		Resource resource = applicationContext.getResource("config.txt");
		System.out.println(resource.getFilename());
		System.out.println(resource.contentLength());
	}

}
```

# 五、Spring Bean装配 --注解

## 1、Spring Bean装配之Bean的定义及作用域的注解实现

### 1）Bean管理的注解实现

* Classpth扫描与组件管理

  * 从Spring3.0开始，Spring JavaConfig项目提供了很多特性，包括使用java而不是XML定义bean，比如@Configuration,@Bean,@Import,@DependsOn 
  * Component是一个通用注解，可用于任何bean
  * @Repository，@Service，@Controller是更具有针对性的注解
    * @Repository  用于注解DAO类，即持久层
    * @Service  用于注解Service类，即服务层
    * @Controller  用于注解Controller类，即控制层（MVC）
  * 元注解

* 类的自动检测与注册Bean

  * Spring可以自动检测类并注册Bean到ApplicationContext中：需要注解注册到类上

  * 实现类的自动检测与Bean的注册需要以下内容：

    ```xml
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xmlns:context="http://www.springframework.org/schema/context"
        xsi:schemaLocation="http://www.springframework.org/schema/beans
            http://www.springframework.org/schema/beans/spring-beans.xsd
            http://www.springframework.org/schema/context
            http://www.springframework.org/schema/context/spring-context.xsd" >
            
      <context:component-scan base-package="com.imooc"/>
        
    </beans>
    ```

  * component-scan 组件扫描 ：完成组件的扫描，基于类注解的扫描，扫描到哪些类上注解了Spring相关的Reposity、Service等，把这些类注册到IOC容器中。
  * base-package  扫描包下的所有类
  * <context:component-scan>包含了<context:annotation-config/>，使用前者之后，不再使用后者。前者扫描类的注解；后者在完成了bean的注册之后，去处理bean中的方法或成员变量的注解。使用前者的时候，包含了后者的功能。

* <context:annotation-config/>

  * 通过在基于XML的Spring配置如下标签（注意添加 xmlns:context 命名空间）

* @Component,@Repository,@Service,@Controller

* @Required

* @Autowired

* @Qualifier

* @Resource

### 2）使用过滤器进行自定义扫描

* 默认情况下，类被自动发现并注册bean的条件是：使用@Componet，@Repository，@Service，@Controller或者使用@Component的自定义注解

* 通过过滤器修改上面的行为，比如

  ```xml
  <context:component-scan base-package="com.imooc.beanannotation">
              <context:include-filter type="regex" expression=".*Stub.*Repository"/>
              <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Repository"/>
          </context:component-scan>
  ```

* include-fliter 包含 以regex（通配符）的形式，
* exclude 指排除的注解，以 annotation（注解） 的形式

### 3）使用注解定义Bean

* 扫描过程中组件被自动检测，Bean名称是由BeanNameGenerator生成的（@Componet，@Repository，@Service，@Controller都会有个name属性用于显示设置Bean Name）

  * Component有个name属性，Component注解类时，可以显示指定类在注册到bean容器中，它所对应的id。如果未显示指定，则会根据BeanNameGenerator自动生成ID，通常生成规则是以类名为基础，并把类名的第一个字母小写，作为bean的id。
  * 自定义bean命名策略，实现BeanNameGenrator接口，并一定要包含一个无参数构造器。  --使用name-generator属性。

* 作用域（Scope）

  * 通常情况下，自动查找的Spring组件，其scope是singleton。
  * 也可以自定义scope策略，实现接口并提供一个参数构造器。

  ```java
  //@Component("bean")  //没有参数时，bean id默认为类名首字母小写；有参数时，bean id按参数来。
  //@Scope("prototype")  //每次都创建
  @Scope()  //默认为 singtolen 单例
  @Component
  public class BeanAnnotation {
  	
  	public void say(String arg) {
  		System.out.println("BeanAnnotation : " + arg);
  	}
  	
  	public void myHashCode() {
  		System.out.println("BeanAnnotation : " + this.hashCode());
  	}
  	
  }
  ```
  ```xml
  <context:component-scan base-package="com.imooc.beanannotation"/>
  ```

  ```java
  @RunWith(BlockJUnit4ClassRunner.class)
  public class TestBeanAnnotation extends UnitTestBase {
  	
  	public TestBeanAnnotation() {
  		super("classpath*:spring-beanannotation.xml");
  	}
  	
  	@Test
  	public void testSay() {
  		/*BeanAnnotation bean = super.getBean("beanAnnotation");   --参数默认
  		bean.say("This is test.");*/
  		
  		BeanAnnotation bean = super.getBean("bean");  //指定name为bean
  		bean.say("This is test.");
  	}
  	
  	@Test
  	public void testScpoe() {
  		BeanAnnotation bean = super.getBean("beanAnnotation");
  		bean.myHashCode();
  		
  		bean = super.getBean("beanAnnotation");
  		bean.myHashCode();
  	}
  	
  }
  ```

* 代理方式
  * 可以使用scoped-proxy属性指定代理，有三个值可选：no,interfaces,targetClass
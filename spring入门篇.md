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

DI（Dependency injection）：依赖注入  注入方式：set方式注入；构造器方式注入

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

## 5、Spring的常用注入方式--DI

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
  * Spring注入：设值注入（set注入）
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

* 使用 -- 测试

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
    * **@Repository  用于注解DAO类，即持久层**
    * **@Service  用于注解Service类，即服务层**
    * **@Controller  用于注解Controller类，即控制层（MVC）**
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

* 扫描过程中组件被自动检测，Bean名称是由BeanNameGenerator生成的（@Componet，@Repository，@Service，@Controller 都会有个name属性用于显示设置Bean Name）

  * Component有个name属性，Component注解类时，可以显示指定类在注册到bean容器中，它所对应的id。如果未显示指定，则会根据BeanNameGenerator自动生成ID，通常生成规则是以类名为基础，并把类名的第一个字母小写，作为bean的id。
  * 自定义bean命名策略，实现BeanNameGenrator接口，并一定要包含一个无参数构造器。  --使用name-generator属性。

* 作用域（Scope）

  * 通常情况下，自动查找的Spring组件，其scope是singleton。
  * 也可以自定义scope策略，实现接口并提供一个参数构造器。

  ```java
  //@Component("bean")  //没有参数时，bean id默认为类名首字母小写；有参数时，bean id按参数来。
  //@Scope("prototype")  //每次都创建
  @Scope  //默认为 singtolen 单例
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
  
* @Required  --不常用
  * @Required注解适用于bean属性的setter方法
  * 这个注解仅仅表示，受影响的bean属性必须在配置时被填充，通过在bean定义或通过自动装配一个明确的属性值

## 2、Spring Bean装配之Autowired注解说明

* @Autowired   --针对成员变量和构造器
  * 可以将@Autowired注解为“传统“的setter方法
  * 可用于构造器或成员变量
  * 默认情况下，如果因找不到合适的bean将会导致autowiring失败抛出异常，可以通过 @Autowired（required=false） 避免
  * 每个类只能有一个构造器被标记为 required=true
  * @Autowired的必要属性，建议使用@Required 注解

例子：注解使用

xml： 扫描 com.imooc.beanannotation 下的所有类

```xml
<context:component-scan base-package="com.imooc.beanannotation">
</context:component-scan>
```



Dao：

```java
public interface InjectionDAO {
	
	public void save(String arg);
	
}
```

DaoImp:  @Repository  用于注解DAO类，即持久层

```java
@Repository
public class InjectionDAOImpl implements InjectionDAO {
	
	public void save(String arg) {
		//模拟数据库保存操作
		System.out.println("保存数据：" + arg);
	}

}
```

service：

```java
public interface InjectionService {
	
	public void save(String arg);
	
}
```

serviceImpl: @Service  用于注解Service类，即服务层 ；

* set注入：若成员变量injectionDAO加@Autowired，则不用写set方法，否则需要写set方法
* 构造器注入：构造器中加入@Autowired

```java
@Service
public class InjectionServiceImpl implements InjectionService {

	//成员变量加了@Autowired，不用写set方法，否则需要写set方法
	//@Autowired
	private InjectionDAO injectionDAO;

	//构造器方式
//	@Autowired
//	public InjectionServiceImpl(InjectionDAO injectionDAO) {
//		this.injectionDAO = injectionDAO;
//	}
	
	@Autowired
	public void setInjectionDAO(InjectionDAO injectionDAO) {
		this.injectionDAO = injectionDAO;
	}



	public void save(String arg) {
		//模拟业务操作
		System.out.println("Service接收参数：" + arg);
		arg = arg + ":" + this.hashCode();
		injectionDAO.save(arg);
	}
	
}
```

test：bean id根据@Service默认类名首字母小写显示

```java
@RunWith(BlockJUnit4ClassRunner.class)
public class TestInjection extends UnitTestBase {
	
	public TestInjection() {
		super("classpath:spring-beanannotation.xml");
	}
	
	@Test
	public void testAutowired() {
		InjectionService service = super.getBean("injectionServiceImpl");
		service.save("This is autowired.");
	}
  
}
```

* @Autowired  --针对数组及Map的自动注入 自动装配多个bean

  * 可以使用@Autowired注解那些众所周知的解析依赖性接口，比如：BeanFactory,ApplicationContext,Environment,ResourceLoader,ApplicationEventPublisher,and MessageSource

    ```java
    @Autowired   // --得到ioc的上下文信息并使用
    private ApplicationContext context;
    ```

  * 可以注解到数组上  --注入的是该接口实现类的bean

    * 可以通过添加注解给需要该类型的数组的字段或方法，以提供ApplicationContext中的所有特定类型的bean

  * 可以注解到Map上  --注入的是该接口实现类的bean

    * 可以用于装配key为String的Map

  * 如果希望数组有序，可以让bean实现org.springframework.core.Ordered接口或使用@Order注解

  * @Autowired是由Spring beanPostProcessor处理的，所以不能在自己的beanPostProcessor或beanFactoryProcessor类型上应用这些注解，这些类型必须通过XML或者Spring的@Bean注解加载

  例子：

  BeanImplOne和BeanImplTwo都继承了BeanInterface接口，都标记为@Component，证明是一个bean对象

  ```java
  @Order(2)  //排序
  @Component
  public class BeanImplOne implements BeanInterface {
  
  }
  ```

  ```java
  @Order(1)
  @Component
  public class BeanImplTwo implements BeanInterface {
  
  }
  ```

  ```java
  @Component
  public class BeanInvoker {
  	
  	@Autowired  //注解到数组上，注入的是该接口实现类的bean，两个接口
  	private List<BeanInterface> list;
  	
  	@Autowired   //注解到map上，注入的是该接口实现类的bean，两个接口； Map<String, BeanInterface>对应bean id，BeanInterface 对应接口具体实现类
  	private Map<String, BeanInterface> map;
  	
  	@Autowired
  	@Qualifier("beanImplTwo")
  	private BeanInterface beanInterface;
  	
  	public void say() {
  		if (null != list && 0 != list.size()) {
  			System.out.println("list...");
  			for (BeanInterface bean : list) {
  				System.out.println(bean.getClass().getName());
  			}
  		} else {
  			System.out.println("List<BeanInterface> list is null !!!!!!!!!!");
  		}
  		
  		System.out.println();
  		
  		if (null != map && 0 != map.size()) {
  			System.out.println("map...");
  			for (Map.Entry<String, BeanInterface> entry : map.entrySet()) {
  				System.out.println(entry.getKey() + "      " + entry.getValue().getClass().getName());
  			}
  		} else {
  			System.out.println("Map<String, BeanInterface> map is null !!!!!!!!!!");
  		}		
  	}
  }
  ```

  ```java
  @Test
  	public void testMultiBean() {
  		BeanInvoker invoker = super.getBean("beanInvoker");
  		invoker.say();
  	}
  ```

* @Qualifier注解缩小范围，只显示某个bean

  ```java
  	@Autowired  //注解成员变量
  	@Qualifier("beanImplOne")
  	private BeanInterface beanInterface;
  ```

## 3、Spring Bean装配之基于Java的容器说明

### 1）@Bean

* @Bean标识一个用于配置和初始化一个由SpringIoC容器管理新对象的方法，类似于XML配置文件的<bean/>
* 通常使用@Configuration注解的类中使用@Bean注解任何方法
  * @Configuration表明是一个配置文件？ 

例子：@Configuration和

```java
@Configuration   //@Configuration 和 @Bean 结合使用
public class StoreConfig {
  @Bean(initMethod = "init",destroyMethod = "destroy")
	public StringStore stringStore() {
		return new StringStore();
	}
}
```

```java
	@Test
	public void test() {
		Store store = super.getBean("stringStore");
		System.out.println(store.getClass().getName());
	}
```

### 2）@ImportResource 和 @Value  --进行资源文件读取

* beans中指定 property-placeholder ，location对应一个资源文件存放位置；
* 整个作用是：为了加载配置文件，通过 ${key}，引用资源文件中的内容

xml：

```xml
<context:property-placeholder location="classpath:/config.properties"/>
```

config.properties:

```apl
jdbc.username=root
password=root
url=127.0.0.1
```

通过java注解实现 StoreConfig：

```java
@Configuration
@ImportResource("classpath:config.xml")  //引入资源文件
public class StoreConfig {
	
	@Value("${url}")  //对应资源文件 config.properties 中的key
	private String url;

	@Value("${jdbc.username}")
	private String username;

	@Value("${password}")
	private String password;

	@Bean
	public MyDriverManager myDriverManager() {
		return new MyDriverManager(url, username, password);
	}
}
```

```java
public class MyDriverManager {
   
   public MyDriverManager(String url, String userName, String password) {
      System.out.println("url : " + url);
      System.out.println("userName: " + userName);
      System.out.println("password: " + password);
   }

}
```

测试类：

```java
	@Test
	public void testMyDriverManager() {
		MyDriverManager manager = super.getBean("myDriverManager");
		System.out.println(manager.getClass().getName());
	}
```

输出结果：

```json
url : 127.0.0.1
userName: root
password: root
com.imooc.beanannotation.javabased.MyDriverManager
```

### 3）@Bean和@Scope

* 默认@Bean是单例的，使用@Scope可以指定bean的范围

```java
@Configuration
public class StoreConfig {
  @Bean(initMethod = "init",destroyMethod = "destroy")
	@Scope(value = "prototype")
	public StringStore stringStore() {
		return new StringStore();
}
```

测试：

```java
	@Test
	public void testScope() {
		Store store = super.getBean("stringStore");
		System.out.println(store.hashCode());
		
		store = super.getBean("stringStore");
		System.out.println(store.hashCode());
	}
```

### 4）基于范型的自动装配

StoreConfig:

```java
@Configuration
public class StoreConfig {
  @Autowired
	private Store<String> s1;

	@Autowired
	private Store<Integer> s2;

	@Bean(initMethod = "init",destroyMethod = "destroy")
	@Scope(value = "prototype")
	public StringStore stringStore() {
		return new StringStore();
	}

	@Bean
	public IntegerStore integerStore() {
		return new IntegerStore();
	}
	
	@Bean(name = "stringStoreTest")
	public Store stringStoreTest() {
		System.out.println("s1 : " + s1.getClass().getName());
		System.out.println("s2 : " + s2.getClass().getName());
		return new StringStore();
	}
}
```

Store<T>:

```java
public interface Store<T> {

}
```

StringStore:

```java
public class StringStore implements Store<String> {
	
	public void init() {
		System.out.println("This is init.");
	}
	
	public void destroy() {
		System.out.println("This is destroy.");
	}
	
}
```

IntegerStore:

```java
public class IntegerStore implements Store<Integer> {

}
```

测试：

```java
@Test
public void testG() {
   StringStore store = super.getBean("stringStoreTest");
}
```

## 4、Spring Bean装配之Spring对JSR支持的说明

Spring还支持使用JSR-250@Resource注解的变量或setter方法，这是一种在Java EE 5和6的通用模式，Spring管理的对象也支持这种模式。
@Resource有一个name属性，并且默认Spring解释该值作为被注入bean的名称。如果没有显式地指出@Resource的name，默认的名称是从属性名或者setter方法得出。

JsrDAO: Dao层对应 @Repository

```java
@Repository
public class JsrDAO {
	
	public void save() {
		System.out.println("JsrDAO invoked.");
	}
	
}
```

JsrServie：显示给DAO赋值，有两种办法都可以把DAO的实例注入到当前的实例中来，1:成员变量增加@Resource；2:set方法增加@Resource  能够被调用  

@PostConstruct：执行之前调用  --初始化回调；  @PreDestroy ：执行之后调用 --销毁回调

```java
@Service
public class JsrServie {
	
	@Resource
	private JsrDAO jsrDAO;
	
//	@Resource
	public void setJsrDAO(JsrDAO jsrDAO) { 
		this.jsrDAO = jsrDAO;
	}

	@PostConstruct
	public void init() {
		System.out.println("JsrServie init.");
	}
	
	@PreDestroy
	public void destroy() {
		System.out.println("JsrServie destroy.");
	}

	public void save() {
		jsrDAO.save();
	}	
}
```

测试方法：运行测试方法，会先输出JsrServie init.，再输出JsrDAO invoked.，最后输出JsrServie destroy.。这和xml文件配置init-method和destroy-method是一样的。

```java
	@Test
	public void testSave() {
		JsrServie service = getBean("jsrServie");
		service.save();
	}
```

### 2）使用JSR330标准注解

从Spring3.0开始支持JSR330标准注解（依赖注入注解），其扫描方式与Spring注解一致
使用JSR330需要依赖javax.inject包
使用Maven的一种引入方式

```xml
<dependency>
    <groupId>javax.inject</groupId>
    <artifactId>javax.inject</groupId>
    <version>1</version>
</dependency>
```

使用之前的例子

@Inject

* @Inject等效于@Autowired，可以使用于类、属性、方法、构造器

@Named    

* 如果想使用特定名称进行依赖注入，使用@Named。也就是说同一种类型的bean在IOC容器中有多个的话，如果想使用特定的那个bean，就可以使用这个注解。
* @Named于@Component是等效的。

一种方式是注解到类上，另一种方式是用来指定某一个名称的bean。

1)注解到类上：@Named 注解类，@Inject 注解到成员变量

```java
//@Service
@Named
public class JsrServie {
	
//	@Resource
	@Inject
	private JsrDAO jsrDAO;
  public void save() {
		jsrDAO.save();
	}
}
```

2)

```java
@Named
public class JsrServie {
	
//	@Resource
//	@Inject
	private JsrDAO jsrDAO;
	
//	@Resource
	@Inject
	public void setJsrDAO(@Named("jsrDAO") JsrDAO jsrDAO) { //@Named("jsrDAO") 
		this.jsrDAO = jsrDAO;
	}
  public void save() {
		jsrDAO.save();
	}
	
}
```

@Named("jsrDAO") 作用：假如这个JsrDAO类是一个接口，它有两个实现类，都注入到了当前的IOC容器中，就像前边例子中的StringStore和IntegerStore，那么就可以通过Named引用到底是哪一个。

测试：

```java
@Test
	public void testSave() {
		JsrServie service = getBean("jsrServie");
		service.save();
	}
```

# 五、Spring AOP基本概念

## 1、AOP基本概念及特点

* AOP(Aspect Oriented Programming)：面向切面编程，通过预编译方式和运行期动态代理实现程序功能的统一维护的一种技术。

* 主要的功能是：日志记录，性能统计，安全控制，事务处理，异常处理等。

* 切面
  * 模块一般是横向划分，比如用户管理、系统管理等；每个模块都有日志记录，性能统计等等，如果单独放每一个模块中，不好修改。但是这些可以通过切面维护，是纵向的，比如：日志系统对应所有模块。

### 1）AOP实现方式

* 预编译
  * AspectJ
* 运行期动态代理（JDK动态代理、CGLib动态代理）
  * SpringAOP、JbossAOP

### 2）AOP相关的概念

* 切面（Aspect）：一个关注点的模块化，这个关注点可能会横切多个对象
* 连接点（Joinpoint）：程序执行过程中的某个特定的点    比如，一个类中的某个方法执行开始
* 通知（Advice）：在切面的某个特定的连接点上执行的动作   比如：方法执行中的额外切面的动作
* 切入点（Pointcut）：匹配连接点的断言，在AOP中通知和一个切入点表达式关联
* 引入（Introduction）：在不修改类代码的前提下，为类添加新的方法和属性
* 目标对象（Target Object）：被一个或者多个切面所通知的对象  比如切面通知商品管理和订单管理；引入中所提到的目标类，即要通知的对象，也就是真正的业务逻辑。
* AOP代理（AOP Proxy）：AOP框架创建的对象，用来实现切面契约（aspect contract）（包括通知方法执行等功能）
* 织入（Weaving）：把切面连接到其它的应用程序类型或者对象上，并创建一个被通知的对象，分为：编译时织入、类加载时织入、执行时织入

Advice的类型

* 前置通知（Before advice）：在某个连接点之前执行的通知，但不能阻止连接点前的执行（除非它抛出一个异常）
* 返回后通知（After returning advice）：在某个连接点正常完成后执行的通知
* 抛出异常后通知（After throwing advice）：在方法抛出异常退出时执行的通知
* 后通知（After（finally）advice）：在某个连接点退出的时候执行的通知（不论是正常返回还是异常退出）
* 环绕通知（Around advice）：包围一个连接点的通知

### 3）Spring框架中AOP的用途

* 提供了声明式的企业服务，特别是EJB的替代服务的声明
* 允许用户定制自己的方面，已完成OOP与AOP的互补作用
  * OOP：面向对象编程，执行功能顺序
  * AOP：关注横切，在各个功能之间横切

### 4）Spring的AOP实现

* 纯java实现，无需特殊的编译过程，不需要控制类加载器层次
* 目前只支持方法执行连接点
* 不是为了提供最完整的AOP实现（尽管它非常强大）；而是侧重于一种AOP实现和Spring IOC容器之间的整合，用于帮助解决企业应用中的常见问题
* Spring AOP不会与AspectJ竞争，从而提供综合全面的AOP解决方案

### 5）有接口和无接口的Spring AOP实现区别

* Spring AOP默认使用标准的JavaSE动态代理作为AOP代理，这使得任何接口（或者接口集）都可以被代理
* Spring AOP中也可以使用CGLIB代理（如果一个业务对象并没有实现一个接口）

## 2、配置切面aspect  (基于Schema-based的AOP实现)

* Spring的所有切面和通知器都必须放在一个<aop:config>内（可以配置包含多个<aop:config>元素），每一个<aop:config>可以包含pointcut,advisor和aspect元素（它们必须按照这个顺序声明）
* <aop:config>风格的配置大量使用了Spring的自动代理机制

```xml
<bean id="moocAspect" class="com.imooc.aop.schema.advice.MoocAspect"></bean>
<bean id="aspectBiz" class="com.imooc.aop.schema.advice.biz.AspectBiz"></bean>
<aop:config>
		<aop:aspect id="moocAspectAOP" ref="moocAspect">
    </aop:aspect>
</aop:config>
```

## 3、配置切入点Pointcut

* 切入点表达式：
  * execution 用于匹配方法执行的连接点；
  * within 用于匹配指定类型内的方法执行
  * this 用于匹配当前AOP代理对象类型的执行方法
  * target 用于匹配当前执行的方法传入的参数为指定类型的执行方法

切入点的配置：在 aop:pointcut expression 下

```xml
<bean id="moocAspect" class="com.imooc.aop.schema.advice.MoocAspect"></bean>
<bean id="aspectBiz" class="com.imooc.aop.schema.advice.biz.AspectBiz"></bean>
<aop:config>
		<aop:aspect id="moocAspectAOP" ref="moocAspect">
      <!-- 匹配biz下以Biz结尾的类下所有的方法 -->
			<aop:pointcut expression="execution(* com.imooc.aop.schema.advice.biz.*Biz.*(..))" id="moocPiontcut"/>
     </aop:aspect>
</aop:config>
```

## 4、Advice应用

前置通知（Before advice）：

* MoocAspect为切面，对应着aspect中的引用；

* MoocAspect下有个method为before()方法

* 切入点 是biz包下的所有以Biz结尾的类名下的所有方法

* before方法执行在 切入点执行之前被触发  pointcut-ref为引入的切入点

* 测试结果：

  MoocAspect before.
  AspectBiz biz.

返回后通知（After returning advice）

* 找到切面的类 MoocAspect 在其下增加 afterReturning 方法

* after-returning 下定义的方法在 切入点执行之后 被触发

* 测试结果：

  MoocAspect before.
  AspectBiz biz.
  MoocAspect afterReturning.

抛出异常后通知（After throwing advice）：

* 在 切入点 方法报异常时才会出现  在biz方法下抛异常 throw new RuntimeException();

* 正常情况下不会报

* 结果：

  MoocAspect before.
  AspectBiz biz.
  MoocAspect afterThrowing.

后通知（After（finally）advice）：

* 找到切面的类 MoocAspect 在其下增加 after 方法

* after下定义的方法在 切入点执行完成之后 被触发

* 结果（没有抛异常）

  MoocAspect before.
  AspectBiz biz.
  MoocAspect afterReturning.
  MoocAspect after.

* 结果（抛异常） 不管有没有抛异常，后通知都会执行

  MoocAspect before.
  AspectBiz biz.
  MoocAspect afterThrowing.
  MoocAspect after.

环绕通知（Around advice）：

* 通知方法的第一个参数必须是ProceedingJoinPoint类型，pjp.proceed()是具体方法执行前后的通知

* 结果：

  MoocAspect before.
  MoocAspect around 1.
  AspectBiz biz.
  MoocAspect around 2.
  MoocAspect after.
  MoocAspect afterReturning.

环绕通知（Around advice）：-- 使用参数

* MoocAspect 中增加方法：aroundInit

* 该方法对应的切入点设定了参数名、方法名，方法init  -- AspectBiz

  切面是通知和切入点的结合。

  一个完整的切面定义包括：通知说明了干什么和什么时候干（before，after，around），切入点说明了在哪干（指定具体哪个方法。

```xml
<bean id="moocAspect" class="com.imooc.aop.schema.advice.MoocAspect"></bean>
<bean id="aspectBiz" class="com.imooc.aop.schema.advice.biz.AspectBiz"></bean>
<aop:config>
		<aop:aspect id="moocAspectAOP" ref="moocAspect">
      <!-- 匹配biz下以Biz结尾的类下所有的方法 -->
			<aop:pointcut expression="execution(* com.imooc.aop.schema.advice.biz.*Biz.*(..))" id="moocPiontcut"/>
      <!-- 通知方法before中定义了干什么，在执行前被触发。pointcut-ref定义了通知方法在哪个切入点触发 -->
      <aop:before method="before" pointcut-ref="moocPiontcut"/>
      <aop:after-returning method="afterReturning" pointcut-ref="moocPiontcut"/>
      <aop:after-throwing method="afterThrowing" pointcut-ref="moocPiontcut"/>
 			<aop:after method="after" pointcut-ref="moocPiontcut"/> 
      <aop:around method="around" pointcut-ref="moocPiontcut"/>
      <aop:around method="aroundInit" pointcut="execution(* com.imooc.aop.schema.advice.biz.AspectBiz.init(String, int))
 							and args(bizName, times)"/>
      <!-- 切面声明： 匹配类型： biz下的所有类；implement-interface：声明的接口；default-impl：上边接口实现的类-->
      <aop:declare-parents types-matching="com.imooc.aop.schema.advice.biz.*(+)" 
							implement-interface="com.imooc.aop.schema.advice.Fit"
							default-impl="com.imooc.aop.schema.advice.FitImpl"/>
    </aop:aspect>
</aop:config>
```

```java
// 切面 -- 通知方法
public class MoocAspect {
	
	public void before() {
		System.out.println("MoocAspect before.");
	}
  public void afterReturning() {
		System.out.println("MoocAspect afterReturning.");
	}
	
	public void afterThrowing() {
		System.out.println("MoocAspect afterThrowing.");
	}
	
	public void after() {
		System.out.println("MoocAspect after.");
	}
  public Object around(ProceedingJoinPoint pjp) {
		Object obj = null;
		try {
			System.out.println("MoocAspect around 1."); //具体方法执行前通知
			obj = pjp.proceed();
			System.out.println("MoocAspect around 2."); //具体方法执行后通知
		} catch (Throwable e) {
			e.printStackTrace();
		}
		return obj;
	}
  public Object aroundInit(ProceedingJoinPoint pjp, String bizName, int times) {
		System.out.println(bizName + "   " + times);
		Object obj = null;
		try {
			System.out.println("MoocAspect aroundInit 1.");
			obj = pjp.proceed();
			System.out.println("MoocAspect aroundInit 2.");
		} catch (Throwable e) {
			e.printStackTrace();
		}
		return obj;
	}
}
```

```java
//切入点对应的类  没有声明bean，怎么用bean调用？
public class AspectBiz {
	
	public void biz() {
		System.out.println("AspectBiz biz.");
    //throw new RuntimeException();
	}
  public void init(String bizName, int times) {
		System.out.println("AspectBiz init : " + bizName + "   " + times);
	}
}
```

```java
@Test
	public void testBiz() {
		AspectBiz biz = super.getBean("aspectBiz");
		biz.biz();
	}
@Test
	public void testInit() {
		AspectBiz biz = super.getBean("aspectBiz");
		biz.init("moocService", 3);
	}
```

## 5、Introductions应用

* Introduction 引入，向现有的类添加新方法属性
* 允许一个 切面 声明一个实现 指定接口 的 通知对象，并且提供了一个 接口实现类 来代表这些对象
  * 比如，FitImpl代表 types-matching 下匹配到的AspectBiz 对象
* 由<aop:aspect> 中的<aop:declare-parents> 元素声明 
  * 该元素用于声明所匹配的类型拥有一个新的parent

```xml
<bean id="moocAspect" class="com.imooc.aop.schema.advice.MoocAspect"></bean>
<bean id="aspectBiz" class="com.imooc.aop.schema.advice.biz.AspectBiz"></bean>
<aop:config>
		<aop:aspect id="moocAspectAOP" ref="moocAspect">
      <!-- 切面声明： 匹配类型： biz下的所有类；implement-interface：声明的接口；default-impl：上边接口实现的类-->
      <aop:declare-parents types-matching="com.imooc.aop.schema.advice.biz.*(+)" 
							implement-interface="com.imooc.aop.schema.advice.Fit"
							default-impl="com.imooc.aop.schema.advice.FitImpl"/>
    </aop:aspect>
</aop:config>
```

接口：

```java
public interface Fit {
	
	void filter();

}
```

实现类：

```java
public class FitImpl implements Fit {

	@Override
	public void filter() {
		System.out.println("FitImpl filter.");
	}

}
```

测试：

```java
	@Test
	public void testFit() {
		Fit fit = (Fit)super.getBean("aspectBiz");  //aspectBiz为biz下边的类的beanId，转为声明中的partent
		fit.filter(); //调用声明中的实现类
	}
```

## 6、Advisors

* advisor就像一个小的自包含的方面，只有一个advice

* 切面自身通过一个bean表示，并且必须实现某个advice接口，同时，advisor也可以很好地的利用AspectJ的注入点表达式

* Spring通过配置文件中<aop:advisor>元素 支持advisor实际使用中，大多数情况下它会和transactional advice配合使用

* 为了定义一个advisor的优选级以便让advice有序，可以使用order属性来定义advisor的顺序

  

* 使用环绕通知实现访问限制的例子

xml:

```xml
<context:component-scan base-package="com.imooc.aop.schema"></context:component-scan>

	<aop:config>
    <!-- 切面id及引用，引用指向另一个bean -->
		<aop:aspect id="concurrentOperationRetry" ref="concurrentOperationExecutor">
      <!-- 执行expression中定义的所有类型的方法，在包下 -->
			<aop:pointcut id="idempotentOperation"
				expression="execution(* com.imooc.aop.schema.advisors.service.*.*(..)) " />
      <!-- 环绕通知，切入点id：idempotentOperation，method定义在切面下，对应为：concurrentOperationExecutor -->
			<aop:around pointcut-ref="idempotentOperation" method="doConcurrentOperation" />
		</aop:aspect>
	</aop:config>
	
	<bean id="concurrentOperationExecutor" class="com.imooc.aop.schema.advisors.ConcurrentOperationExecutor">
		<property name="maxRetries" value="3" />
		<property name="order" value="100" />
	</bean>
```

ConcurrentOperationExecutor类  --切面引用的类

```java
public class ConcurrentOperationExecutor implements Ordered {

	private static final int DEFAULT_MAX_RETRIES = 2;

	private int maxRetries = DEFAULT_MAX_RETRIES;
	
	private int order = 1;

	public void setMaxRetries(int maxRetries) {
		this.maxRetries = maxRetries;
	}

	public int getOrder() {
		return this.order;
	}

	public void setOrder(int order) {
		this.order = order;
	}

	public Object doConcurrentOperation(ProceedingJoinPoint pjp) throws Throwable {
		int numAttempts = 0;
		PessimisticLockingFailureException lockFailureException;
		do {
			numAttempts++;
			System.out.println("Try times : " + numAttempts);
			try {
				return pjp.proceed();
			} catch (PessimisticLockingFailureException ex) {
				lockFailureException = ex;
			}
		} while (numAttempts <= this.maxRetries);
		System.out.println("Try error : " + numAttempts);
		throw lockFailureException;
	}
}
```

//切入点执行的方法

```java
<!-- @Service 也标识是一个bean -->
@Service
public class InvokeService {
	
	public void invoke() {
		System.out.println("InvokeService ......");
	}
	
	public void invokeException() {
		throw new PessimisticLockingFailureException("");
	}

}
```

测试类：

```java
@Test
	public void testSave() {
		InvokeService service = super.getBean("invokeService");
		service.invoke();
		
		System.out.println();
		service.invokeException();
 	}
```

注意：走切入点执行类下的：invoke方法的时候，会自动调用切面中定义的doConcurrentOperation方法。

切面中的方法会在连接点定义的方法下执行？？
# JdbcTemplate

## JdbcTemplate的概念和准备

**1、什么是 JdbcTemplate**

（1）Spring 框架对 JDBC 进行封装，使用 JdbcTemplate 方便实现对数据库操作

**2、准备工作**

1）引入相关 jar 包 

<img src="C:\Users\86187\AppData\Roaming\Typora\typora-user-images\image-20210909104251304.png" alt="image-20210909104251304" style="zoom: 80%;" />

2）在 spring 配置文件配置数据库连接池

```xml
<!-- 数据库连接池 --> 
<bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource" destroy-method="close"> 
    <property name="url" value="jdbc:mysql:///user_db" />
	<property name="username" value="root" />
	<property name="password" value="root" />
	<property name="driverClassName" value="com.mysql.jdbc.Driver" />
</bean>
```

3）配置 JdbcTemplate 对象，注入 DataSource

```xml
<!-- JdbcTemplate 对象 --> 
<bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate">
	<!--注入 dataSource--> 
    <property name="dataSource" ref="dataSource"></property>
</bean>
```

4）创建 service 类，创建 dao 类，在 dao 注入 jdbcTemplate 对象

\* 配置文件

```xml
<!-- 组件扫描 --> 
<context:component-scan base-package="com.atguigu"></context:component-scan>
```

- Service

  ```java
  @Service
  public class BookService {
  	//注入 dao
  	@Autowired
  	private BookDao bookDao; 
  }
  ```

- Dao

  ```java
  @Repository
  public class BookDaoImpl implements BookDao {
  	//注入 JdbcTemplate
  	@Autowired
  	private JdbcTemplate jdbcTemplate; 
  }
  ```

## JdbcTemplate操作数据库（添加）

**1、对应数据库创建实体类**

**2、编写 service 和 dao**

1）在 dao 进行数据库添加操作

2）调用 JdbcTemplate 对象里面 update 方法实现添加操作

```java
update (String sql, 0bject... args )
```

有两个参数：

- 第一个参数：sql 语句
- 第二个参数：可变参数，设置 sql 语句值

```java
@Repository
public class BookDaoImpl implements BookDao {
	//注入 JdbcTemplate
	@Autowired
	private JdbcTemplate jdbcTemplate;
	//添加的方法
	@Override
	public void add(Book book) {
		//1 创建 sql 语句
		String sql = "insert into t_book values(?,?,?)";
		//2 调用方法实现
		Object[] args = {book.getUserId(), book.getUsername(), 
		book.getUstatus()};
		int update = jdbcTemplate.update(sql,args);
		System.out.println(update);
	} 
}
```

**3、测试类**

```java
@Test
public void testJdbcTemplate() {
	ApplicationContext context = new ClassPathXmlApplicationContext("bean1.xml");
	BookService bookService = context.getBean("bookService", BookService.class);
	Book book = new Book();
	book.setUserId("1");
	book.setUsername("java");
	book.setUstatus("a");
	bookService.addBook(book);
}
```

## JdbcTemplate操作数据库（修改和删除）

**1、修改**

```java
@Override
public void updateBook(Book book) {
	String sql = "update t_book set username=?,ustatus=? where user_id=?";
	Object[] args = {book.getUsername(), book.getUstatus(),book.getUserId()};
	int update = jdbcTemplate.update(sql, args);
	System.out.println(update);
}
```

**2、删除**

```java
@Override
public void delete(String id) {
	String sql = "delete from t_book where user_id=?";
	int update = jdbcTemplate.update(sql, id);
	System.out.println(update);
}
```

## JdbcTemplate操作数据库（查询）

### 1、查询返回某个值

1）查询表里面有多少条记录，返回是某个值

2）使用 JdbcTemplate实现查询返回某个值代码

```java
queryFor0bject (String sql, Class<T> requiredType)
```

有两个参数：

- 第一个参数：sql 语句
- 第二个参数：返回类型 Class

```java
//查询表记录数
@Override
public int selectCount() {
	String sql = "select count(*) from t_book";
	Integer count = jdbcTemplate.queryForObject(sql, Integer.class);
	return count;
}
```

### 2、查询返回对象

1）场景：查询图书详情

2）JdbcTemplate实现查询返回对象

```java
queryFor0bject (String sql, RowMapper<T> rowMapper, 0bject... args )
```

有三个参数：

- 第一个参数：sql 语句
- 第二个参数：RowMapper 是接口，针对返回不同类型数据，使用这个接口里面实现类完成数据封装
- 第三个参数：sql 语句值

```java
//查询返回对象
@Override
public Book findBookInfo(String id) {
	String sql = "select * from t_book where user_id=?";
	//调用方法
	Book book = jdbcTemplate.queryForObject(sql, new BeanPropertyRowMapper<Book>(Book.class), id);
	return book;
}
```

### 3、查询返回集合

1）场景：查询图书列表分页

2）调用JdbcTemplate 方法实现查询返回集合

```java
query(String sql, RowMapper<T> rowMapper, 0bject... args)
```

有三个参数：

- 第一个参数：sql 语句
- 第二个参数：RowMapper 是接口，针对返回不同类型数据，使用这个接口里面实现类完成数据封装
- 第三个参数：sql 语句值

```java
//查询返回集合
@Override
public List<Book> findAllBook() {
	String sql = "select * from t_book";
	//调用方法
	List<Book> bookList = jdbcTemplate.query(sql, new BeanPropertyRowMapper<Book>(Book.class));
	return bookList;
}
```

# 事务

## 事务概念

### 1、什么是事务

1）事务是数据库操作最基本单元，逻辑上一组操作，要么都成功，如果有一个失败所有操作都失败

2）典型场景：银行转账

\* lucy 转账 100 元 给 mary

\* lucy 少 100，mary 多 100

### 2、事务四个特性（ACID）

1）原子性

2）一致性

3）隔离性

4）持久性

## Spring管理事务介绍

1、事务添加到 JavaEE 三层结构里面 Service 层（业务逻辑层）
2、在 Spring 进行事务管理操作有两种方式：编程式事务管理和声明式事务管理（使用）
3、声明式事务管理
（1）基于注解方式（使用）
（2）基于 xml 配置文件方式
4、在 Spring 进行声明式事务管理，底层使用 AOP 原理
5、Spring 事务管理 API，提供一个接口，代表事务管理器，这个接口针对不同的框架提供不同的实现类

<img src="C:\Users\86187\AppData\Roaming\Typora\typora-user-images\image-20210910084110059.png" alt="image-20210910084110059" style="zoom:80%;" />

### 基于注解声明式事务管理

1、在 spring 配置文件配置事务管理器

```xml
<!--创建事务管理器--> 
<bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
	<!--注入数据源--> 
    <property name="dataSource" ref="dataSource"></property>
</bean>
```

2、在 spring 配置文件，开启事务注解
（1）在 spring 配置文件引入名称空间 tx

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xmlns:tx="http://www.springframework.org/schema/tx"
       xsi:schemaLocation="http://www.springframework.org/schema/beans 
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context 
       http://www.springframework.org/schema/context/spring-context.xsd
       http://www.springframework.org/schema/aop 
       http://www.springframework.org/schema/aop/spring-aop.xsd
       http://www.springframework.org/schema/tx 
       http://www.springframework.org/schema/tx/spring-tx.xsd"> 
    
<beans/>
```

（2）开启事务注解

```xml
<!--开启事务注解--> 
<tx:annotation-driven transaction-manager="transactionManager"></tx:annotation-driven>
```

3、在 service 类上面（或者 service 类里面方法上面）添加事务注解
（1）@Transactional，这个注解添加到类上面，也可以添加方法上面
（2）如果把这个注解添加类上面，这个类里面所有的方法都添加事务
（3）如果把这个注解添加方法上面，为这个方法添加事务

```java
@Service
@Transactional
public class UserService {}
```

### 声明式事务的参数配置

在 service 类上面添加注解@Transactional，在这个注解里面可以配置事务相关参数

<img src="C:\Users\86187\AppData\Roaming\Typora\typora-user-images\image-20210910093722102.png" alt="image-20210910093722102" style="zoom:80%;" />

**1、propagation：事务传播行为**
多事务方法直接进行调用，这个过程中事务 是如何进行管理的

<img src="C:\Users\86187\AppData\Roaming\Typora\typora-user-images\image-20210910094003076.png" alt="image-20210910094003076" style="zoom:80%;" />

事务的传播行为可以由传播属性指定。Spring 定义了7种类传播行为。

|   传播属性    |                             描述                             |
| :-----------: | :----------------------------------------------------------: |
|   REQUIRED    | 如果有事务在运行，当前的方法就在这个事务内运行,否则，就启动一个新的事务，并在自己的事务内运行 |
| REQUIRED_NEW  | 当前的方法必须启动新事务，并在它自己的事务内运行.如果有事务正在运行，应该将它挂起 |
|   SUPPORTS    | 如果有事务在运行，当前的方法就在这个事务内运行.否则它可以不运行在事务中 |
| NOT_SUPPORTED |   当前的方法不应该运行在事务中.如果有运行的事务，将它挂起    |
|   MANDATORY   | 当前的方法必须运行在事务内部，如果没有正在运行的事务,就抛出异常 |
|     NEVER     |  当前的方法不应该运行在事务中，如果有运行的事务，就抛出异常  |
|    NESTED     | 如果有事务在运行，当前的方法就应该在这个事务的嵌套事务内运行.否则，就启动一个新的事务，并在它自己的事务内运行. |

**2、ioslation：事务隔离级别**
（1）事务有特性成为隔离性，多事务操作之间不会产生影响。不考虑隔离性产生很多问题
（2）有三个读问题：脏读、不可重复读、虚（幻）读

**脏读：**一个未提交事务读取到另一个未提交事务的数据（是一定要避免的）

<img src="C:\Users\86187\AppData\Roaming\Typora\typora-user-images\image-20210910094809870.png" alt="image-20210910094809870" style="zoom:80%;" />

**不可重复读：**一个未提交事务读取到另一提交事务修改数据（属于一种现象）

<img src="C:\Users\86187\AppData\Roaming\Typora\typora-user-images\image-20210910094920262.png" alt="image-20210910094920262" style="zoom:80%;" />

**虚读：**一个未提交事务读取到另一提交事务添加数据

（3）解决：通过设置事务隔离级别，解决读问题

|                            | 脏读 | 不可重复读 | 幻读 |
| :------------------------: | :--: | :--------: | :--: |
| READ_UNCOMMITTED(读未提交) |  有  |     有     |  有  |
| READ_COMMITTED( 读已提交)  |  无  |     有     |  有  |
| REPEATABLE_READ(可重复读)  |  无  |     无     |  有  |
|    SERIALIZABLE(串行化)    |  无  |     无     |  无  |

**3、timeout：超时时间**
（1）事务需要在一定时间内进行提交，如果不提交进行回滚
（2）默认值是 -1 ，设置时间以秒单位进行计算
**4、readOnly：是否只读**
（1）读：查询操作，写：添加修改删除操作
（2）readOnly 默认值 false，表示可以查询，可以添加修改删除操作
（3）设置 readOnly 值是 true，设置成 true 之后，只能查询
**5、rollbackFor：回滚**
（1）设置出现哪些异常进行事务回滚
**6、noRollbackFor：不回滚**
（1）设置出现哪些异常不进行事务回滚


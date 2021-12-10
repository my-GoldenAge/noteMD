# JDBC

```java
/**
 * 步骤：
 * 1、注册驱动
 * 2、获取数据库连接对象
 * 3、获取数据库操作对象
 * 4、执行SQL
 * 5、返回记录条数/获取结果集对象
 * 6、关闭资源
 */
public class JDBCTest01 {
    public static void main(String[] args) {

        Connection connection = null;
        Statement statement = null;
        ResultSet resultSet = null;
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            /**
             * String url 连接数据库的地址
             * String user 数据库用户名root
             * String password 数据库密码
             * jdbc:mysql:// 协议
             * localhost 本地ip地址
             * 3306 默认端口号
             * eagletest 需要使用的数据库
             *
             */
            String url = "jdbc:mysql://localhost:3306/eagletest" +
                    "?serverTimezone=GMT";

            connection = DriverManager.getConnection(url, null, null);
            System.out.println(connection);
            statement = connection.createStatement();
            String sql = "select * from emp";
            resultSet = statement.executeQuery(sql);

            while (resultSet.next()) {
//                取出结果集中的数据
                int empno = resultSet.getInt("EMPNO");
                String ename = resultSet.getString("ENAME");
                System.out.println("主键："+empno+" 姓名："+ename);
            }
        } catch (ClassNotFoundException | SQLException e) {
            e.printStackTrace();
        } finally {
//            6、关闭数据库资源
            if (resultSet != null) {
                try {
                    resultSet.close();
                } catch (SQLException throwables) {
                    throwables.printStackTrace();
                }
            }
            if (statement != null) {
                try {
                    statement.close();
                } catch (SQLException throwables) {
                    throwables.printStackTrace();
                }
            }
            if (connection != null) {
                try {
                    connection.close();
                } catch (SQLException throwables) {
                    throwables.printStackTrace();
                }
            }
        }
    }
}
```

## 使用JDBC第一步：加载驱动

**什么是数据库驱动程序？**

- JDK提供jdbc接口，就是java怎样去调用数据库，但是注意提供的只是接口，数据库提供商实现这些接口，就是所谓数据库驱动。java调用数据库驱动，驱动真正执行数据库操作。

注册驱动有三种方式：

1. Class.forName(“com.mysql.jdbc.Driver”);
推荐这种方式，不会对具体的驱动类产生依赖
2. DriverManager.registerDriver(com.mysql.jdbc.Driver);
会对具体的驱动类产生依赖
3. System.setProperty(“jdbc.drivers”, “driver1:driver2”);
虽然不会对具体的驱动类产生依赖；但注册不太方便，所以很少使用
## 使用JDBC第二步：建立连接

通过Connection建立连接，Connection是一个接口类，其功能是与数据库进行连接（会话）。

建立Connection接口类对象：

Connection conn =DriverManager.getConnection(url, user, password);

```java
 /**
             * String url 连接数据库的地址
             * String user 数据库用户名root
             * String password 数据库密码
             * jdbc:mysql:// 协议
             * localhost 本地ip地址
             * 3306 默认端口号
             * eagletest 需要使用的数据库
             *
             */
            String url = "jdbc:mysql://localhost:3306/eagletest" +
                    "?serverTimezone=GMT";

            connection = DriverManager.getConnection(url, null, null);
```

user即为登录数据库的用户名，如root

password即为登录数据库的密码，为空就填""

## 使用JDBC第三步：创建执行对象

执行对象Statement负责执行SQL语句，由Connection对象产生。

Statement接口类还派生出两个接口类PreparedStatement和CallableStatement，这两个接口类对象为我们提供了更加强大的数据访问功能。

创建Statement的语法为：

Statement st = conn.createStatement();

### 使用PreparedStatement 获取数据库对象防止SQL注入

```java
/**
 * sql注入：指的就是通过在sql中加入数据库的关键字，导致最终sql执行的结果是错误的
 * select * from tb_user where 1 = 1 or password = ""
 * PreparedStatement 这个对象可以防止sql注入 因为这个对象在执行sql的时候
 * 是分为两个步骤 ： 1、先预编译sql，先把sql的架子给搭建出来，但是没有赋值，2、给sql中注入具体的数据，3、执行sql
 * select * from tb_user where username = ? and password = ?
 * ? = jack
 * ? = 123456
 * Statement对象没有预编译的过程，直接就是执行sql
 * select * from tb_user where username = jack and password = 123456
 */
public class JdbcDemo03 {
    public static void main(String[] args) {
        Connection connection = null;
        PreparedStatement preparedStatement = null;
        ResultSet resultSet = null;
        try {
            //注册驱动
            Class.forName("com.mysql.cj.jdbc.Driver");
            //获取数据库对象
            connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/user" +
                            "?serverTimezone=GMT&characterEncoding=utf8",
                    "root", "root");
//            获取数据库操作对象，并且预编译SQL
            preparedStatement = connection.prepareStatement("" +
                    "select * from users where username=? and password=?");
//            这里需要用到PreparedStatement接口set方法给占位符进行赋值。
//            注意一点，这里的参数索引是从1开始的。        
            preparedStatement.setString(1, "张三");
            preparedStatement.setString(2, "123");
//            执行SQL
            resultSet = preparedStatement.executeQuery();
            if (resultSet != null && resultSet.next()) {
                System.out.println("用户名为：" + resultSet.getString("username"));
                System.out.println("密码为：" + resultSet.getString("password"));
            }

        } 
```

## 使用JDBC第四步：执行SQL语句

执行对象Statement提供两个常用的方法来执行SQL语句。

* executeQuery(Stringsql),该方法用于执行实现查询功能的sql语句，返回类型为ResultSet（结果集）。

如：ResultSet  rs =st.executeQuery(sql);

* executeUpdate(Stringsql),该方法用于执行实现增、删、改功能的sql语句，返回类型为int，即受影响的行数。

如：int flag = st.executeUpdate(sql);

### 执行SQL语句时如果语句中使用程序中的变量

```java
resultSet = statement.executeQuery("select * from users" +
        "where username = '"+next+"' and password = '"+next1+"'");
```
### 理解

在查询筛选时有些操作就可以直接交给SQL语句完成，因为通过select查询执行的SQL语句得到的是一张表，而executeQuery()会将这张表中的每一行封装成一个对象返回给ResultSet 集合

## 使用JDBC第五步：处理执行结果

ResultSet对象负责保存Statement执行后所产生的查询结果。

结果集ResultSet是通过游标来操作的。

游标就是一个可控制的、可以指向任意一条记录的指针。有了这个指针我们就能轻易地指出我们要对结果集中的哪一条记录进行修改、删除，或者要在哪一条记录之前插入数据。一个结果集对象中只包含一个游标。

## 使用JDBC 第六步——释放资源

Connection对象的close方法用于关闭连接，并释放和连接相关的资源。

## 使用事务的支持

JDBC提供了3个方法来进行事务管理

* setAutoCommit() 设置自动提交，方法中需要传入一个boolean类型的参数，true为自动提交，false为手动提交
* commit() 提交事务
一般写在try语句块的末尾
* rollback() 回滚事务
一般写在catch语句块中
```java
/**
 * A账户向B账户转账一千
 * 模拟一个异常
 * 开启对事务的支持
 * 在jdbc中如何开启对事务的支持？
 * jdbc默认是关闭事务的，如果想开启事务的话 要调用 connection.setAutoCommit();
 * 如果想关闭自动提交变为手动提交就要传入false，connection.setAutoCommit(false);
 * 然后在sql都执行成功的情况下我们要进行一个事务提交的操作connection.commit();
 *
 * connection.rollback()是一个回滚的方法，是为了让事务回到执行之前的状态
 */
public class JdbcTest02 {
    public static void main(String[] args) {
        Connection connection = null;
        Statement statement = null;
        ResultSet resultSet = null;
        try {
            //注册驱动
            Class.forName("com.eagle.mysql.cj.jdbc.Driver");
            //获取数据库对象
            connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/web_test" +
                            "?serverTimezone=GMT&characterEncoding=utf8",
                    "root","root");
//            将自动提交设置为手动提交
            connection.setAutoCommit(false);
            //获取操作对象
            statement = connection.createStatement();
            //执行sql
            int num = statement.executeUpdate("update account set balance_A = balance_A - 1000 where id = 1");
            System.out.println(num==1 ? "扣钱成功" : "扣钱失败");
            num = statement.executeUpdate("update account set balance_B = balance_B + 1000 where id = 1");
            System.out.println(num==1?"转账成功":"转账失败");
            connection.commit();
        } catch (Exception e) {
            e.printStackTrace();
            try {
//                connection.rollback();是事务回滚的方法，让事务回到执行SQL语句之前的状态
                connection.rollback();
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
        }finally {
            //资源回收
            if (resultSet != null){
                try {
                    resultSet.close();
                } catch (SQLException throwables) {
                    throwables.printStackTrace();
                }
            }
            if (statement != null){
                try {
                    statement.close();
                } catch (SQLException throwables) {
                    throwables.printStackTrace();
                }
            }
            if (connection != null){
                try {
                    connection.close();
                } catch (SQLException throwables) {
                    throwables.printStackTrace();
                }
            }
        }
    }
}
```
### 关于数据库的悲观锁和乐观锁（都是跟事务有关的）：

* 乐观锁：假设在多线程场景下，多个线程同时对一个数据库中的表进行操作，

如果多个线程会去修改同一条数据，乐观锁的思想就是绝对这种情况不可能发生

乐观所可以不用去开启事务的支持（采用的是自动提交的策略）

update tb_user set username = 'tom' where id = 1 and version = "影响记录条数只要大于或者等于1，版本号就会改变"

* 悲观锁：针对与以上描述的情况，悲观锁思想就会觉得这种情况一定会发生，然后要提前去解决这个问题

悲观锁一定要去开启事务的支持，采用手动提交的策略来解决问题， 行级锁，在sql后面加上 for update

* 当一个线程在对某一条记录进行操作的时候，那么别的线程只能等待
## Jdbc六步封装成工具类

工具类的构造函数是private修饰的，即无法实例化对象，而且里面的方法都是static修饰


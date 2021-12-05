# Spring整合Junit

Spring整合Junit可以使创建spring容器、获取实例的操作也简化成注解

```java
/**
 * @Author XiaoSe
 * Date on 2021/9/8  19:49
 */
/**
 * @RunWith 这个注解可以去替换运行器
 *     SpringJUnit4ClassRunner 单元测试框架
 * @ContextConfiguration 加载配置文件
 * 以上两个注解可以在spring程序运行的时候获取核心容器对象,并且只要注入想要使用的实例即可直接使用，相当于getBean()
 * 
 *  基于注解的方式：@ContextConfiguration(classes = SpringConfig.class)
 *  基于xml的方式：@ContextConfiguration(locations = "classpath:xml/beans.xml")
 */
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(locations = "classpath:beans.xml")
public class JunitTest1 {
    @Autowired
    private User user;

    @Test
    public void test1(){

        user.login();
    }

}
```


---
title: 学习笔记——MyBatis入门
date: 2018-07-30 18:59:54
tags: MyBatis
categories: 开源框架
---
## MyBatis简介

MyBatis 是支持定制化SQL、存储过程以及高级映射的优秀的持久层框架。MyBatis 避免了几乎所有的 JDBC 代码和手动设置参数以及获取结果集。MyBatis 可以对配置和原生Map使用简单的 XML 或注解，将接口和 Java 的 POJOs(Plain Old Java Objects,普通的 Java对象)映射成数据库中的记录。


<!-- more -->
 

## 例子

#### 1)首先创建一个java web项目



![image](http://upload-images.jianshu.io/upload_images/14481291-8626d93b97d57c7c?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 

#### 2）导入所需要的jar包

链接：https://pan.baidu.com/s/1BkC3eNpqpX-ITXaBHbHzFg 密码：r3hj



 

#### 3）创建数据库user和表user，使用utf-8编码



 

#### 4）mysql驱动配置文件



优点：优化性能

 

#### 5）创建mybatis配置文件mybatis.cfg.xml

```
  <?xml version="1.0" encoding="UTF-8"?>
  <!DOCTYPE configuration PUBLIC "-//mybatis.org//DTD Config 3.0//EN" "http://mybatis.org/dtd/mybatis-3-config.dtd">
  <configuration>
      <!-- 引入外部配置文件; -->
      <properties resource="mysql.properties"></properties>
         
  <!--        <typeAliases> -->
  <!--         <typeAlias alias="UserBean" type="com.cxy.mybatis.bean.UserBean" /> -->
  <!--     </typeAliases> -->
         
      <!-- 配置mybatis运行环境,可以配置多个，在具体用时再做切换 -->
      <environments default="test">
         <environment id="test">
             <!-- type="JDBC" 代表使用JDBC的提交和回滚来管理事务 -->
             <!-- 事务管理类型：JDBC、MANAGED -->
             <transactionManager type="JDBC" />
             
             <!-- mybatis提供了3种数据源类型，分别是：POOLED,UNPOOLED,JNDI -->
             <!-- POOLED 表示支持JDBC数据源连接池 -->
             <!-- UNPOOLED 表示不支持数据源连接池 -->
             <!-- JNDI 表示支持外部数据源连接池 -->
             <dataSource type="POOLED">
                 <property name="driver" value="${jdbc.driver}" />
                 <property name="url" value="${jdbc.url}" />
                 <property name="username" value="${jdbc.username}" />
                 <property name="password" value="${jdbc.password}" />
             </dataSource>
         </environment>
     </environments> 
     
     <mappers>
          <!-- 告知映射文件方式1，一个一个的配置-->
          <mapper resource="com/cxy/mybatis/mapper/UserMapper.xml"/>
          <!-- 告知映射文件方式2，自动扫描包内的Mapper接口与配置文件 -->
  <!--         <package name="com/cxy/bean"/> -->
      </mappers>
  </configuration>
```
 

#### 6）创建实体类（UserBean.java）

```
  package com.cxy.mybatis.bean;
  
  /**
   * 用户实体类
   * @author cxy
   *
   */
  public class UserBean {
      public UserBean() {
          super();
      }
      public UserBean(int id, String name, int sex, String website, String phone) {
          super();
          this.id = id;
          this.name = name;
          this.sex = sex;
          this.website = website;
          this.phone = phone;
      }
      private int id;
      private String name;
      private int sex;
      private String website;
      private String phone;
      public int getId() {
          return id;
      }
      public void setId(int id) {
          this.id = id;
      }
      public String getName() {
          return name;
      }
      public void setName(String name) {
          this.name = name;
      }
      public int getSex() {
          return sex;
      }
      public void setSex(int sex) {
          this.sex = sex;
      }
      public String getWebsite() {
          return website;
      }
      public void setWebsite(String website) {
          this.website = website;
      }
      public String getPhone() {
          return phone;
      }
      public void setPhone(String phone) {
          this.phone = phone;
      }
      @Override
      public String toString() {
          return "UserBean [id=" + id + ", name=" + name + ", sex=" + sex
                  + ", website=" + website + ", phone=" + phone + "]";
      }
      
  }
```
 

#### 7)创建接口（UserMapper.java）

```
  package com.cxy.mybatis.mapper;
  
  import java.util.List;
  
  import com.cxy.mybatis.bean.UserBean;
  
  public interface UserMapper {
      /**
       * 新增用戶
       * @param user
       * @return
       * @throws Exception
       */
      public int insertUser(UserBean user) throws Exception;
      /**
       * 修改用戶
       * @param user
       * @param id
       * @return
       * @throws Exception
       */
      public int updateUser (UserBean user) throws Exception;
       /**
        * 刪除用戶
        * @param id
        * @return
        * @throws Exception
        */
      public int deleteUser(int id) throws Exception;
      /**
       * 根据id查询用户信息
       * @param id
       * @return
       * @throws Exception
       */
      public UserBean selectUserById(int id) throws Exception;
       /**
        * 查询所有的用户信息
        * @return
        * @throws Exception
        */
      public List<UserBean> selectAllUser() throws Exception;
  }
```
 

#### 8)创建映射文件（UserMapper.xml）

```
  <?xml version="1.0" encoding="UTF-8"?>
  <!DOCTYPE mapper PUBLIC "-//mybatis.org/DTD Mapper 3.0" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  <mapper namespace="com.cxy.mybatis.mapper.UserMapper">
      <!-- 在各种标签中的id属性必须和接口中的方法名相同 ， id属性值必须是唯一的，不能够重复使用。-->
      <!-- parameterType属性指明查询时使用的参数类型，resultType属性指明查询返回的结果集类型-->
      <!-- useGeneratedKeys：(仅 对 insert有 用 )这 会 告 诉 MyBatis使 用 JDBC的getGeneratedKeys方法来取出由数据（比如：像 MySQL 和 SQLServer 这样的数据库管理系统的自动递增字段）内部生成的主键。默认值： false。 -->    
      <!-- keyProperty：(仅对 insert有用 )标记一个属性， MyBatis会通过 getGeneratedKeys或者通过 insert语句的 selectKey子元素设置它的值。默认：不设置。 -->
      <!-- #{}中的内容，为占位符，当参数为某个JavaBean时，表示放置该Bean对象的属性值  -->
  
      <insert id="insertUser" useGeneratedKeys="true" keyProperty="id">
          insert into user (id,name,sex,website,phone) values (#{id},#{name},#{website},#{sex},#{phone})
      </insert>
      
      <update id="updateUser" >
            update user set id=#{id},name=#{name},sex=#{sex},website=#{website},phone=#{phone} where id=#{id}
      </update>
      
      <delete id="deleteUser" parameterType="int">
           delete from user where id=#{id}  
      </delete>
      
      <select id="selectUserById" parameterType="int" resultType="com.cxy.mybatis.bean.UserBean">
           select * from user where id=#{id}
      </select>
      
      <select id="selectAllUser" resultType="com.cxy.mybatis.bean.UserBean">
           select * from user
      </select>
  </mapper>
```
注：

1、配置文件 mybatis.cfg.xml 是 mybatis 用来建立 sessionFactory，里面主要包含了数据库连接相关内容，还有 java 类所对应的别名，比如：`<typeAlias alias="UserBean" type="com.cxy.mybatis.bean.UserBean"/>` 这个别名非常重要，在具体的类的映射中，比如：UserMapper.xml 中 resultType 就是对应这个。要保持一致，这里的 resultType 还有另外单独的定义方式。</br>
2、mybatis.cfg.xml 里面 的`<mapper resource="com/cxy/mybatis/mapper/UserMapper.xml"/>`是包含要映射的类的 xml 配置文件。</br>
3、在UserMapper.xml 文件里面主要是定义各种 SQL 语句，以及这些语句的参数，以及要返回的类型等等。

 

#### 9)创建工具类（DBTools.java）

```
  package com.cxy.mybatis.tools;
  
  import java.io.Reader;
  
  import org.apache.ibatis.io.Resources;
  import org.apache.ibatis.session.SqlSession;
  import org.apache.ibatis.session.SqlSessionFactory;
  import org.apache.ibatis.session.SqlSessionFactoryBuilder;
  
  public class DBTools {
      public static SqlSessionFactory sessionFactory;
      
      static{
          try {
              String resource = "mybatis.cfg.xml";
              //使用MyBatis提供的Resources类加载mybatis的配置文件
              Reader reader = Resources.getResourceAsReader(resource);
              //构建sqlSession的工厂
              sessionFactory = new SqlSessionFactoryBuilder().build(reader);
          } catch (Exception e) {
              e.printStackTrace();
          }
          
      }
      //创建能执行映射文件中sql的sqlSession
      public static SqlSession getSession(){
          return sessionFactory.openSession();
      }
      
  }
```
 

#### 10)创建测试类（UserService.java）

```
   package com.cxy.mybatis.service;
   
   import java.util.List;
   
   import org.apache.ibatis.session.SqlSession;
   
   import com.cxy.mybatis.bean.UserBean;
   import com.cxy.mybatis.mapper.UserMapper;
   import com.cxy.mybatis.tools.DBTools;
   
   public class UserService {
       public static void main(String[] args) {
           insertUser();
           deleteUser();
           updateUserById();
           selectUserById();
           selectAllUser();
       }
   
       /**
        * 新增用户
        */
       private static void insertUser() {
           SqlSession session = DBTools.getSession();
           UserMapper mapper = session.getMapper(UserMapper.class);
           UserBean user = new UserBean(2, "lisi", 1 ,"www.lisi.com","15950909990");
           try {
               mapper.insertUser(user);
               System.out.println(user.toString());
               session.commit();
           } catch (Exception e) {
               e.printStackTrace();
               session.rollback();
           }
       }
       
       /**
        * 删除用户
        */
       private static void deleteUser(){
           SqlSession session = DBTools.getSession();
           UserMapper mapper = session.getMapper(UserMapper.class);
           try {
               mapper.deleteUser(2);
               session.commit();
           } catch (Exception e) {
               e.printStackTrace();
               session.rollback();
           }
       }
       
       /**
        * 根据id修改用户
        */
       private static void updateUserById(){
           SqlSession session = DBTools.getSession();
           UserMapper mapper = session.getMapper(UserMapper.class);
           UserBean user = new UserBean(1, "zhu", 1,"www.lisi.com","15950909990");
           try {
               mapper.updateUser(user);
               System.out.println(user.toString());
               session.commit();
           } catch (Exception e) {
               e.printStackTrace();
               session.rollback();
           }
       }
       
       /**
        * 根据id查询用户
        */
       private static void selectUserById(){
           SqlSession session = DBTools.getSession();
           UserMapper mapper = session.getMapper(UserMapper.class);
           try {
               UserBean user = mapper.selectUserById(1);
               System.out.println(user.toString());
               session.commit();
           } catch (Exception e) {
               e.printStackTrace();
               session.rollback();
           }
       }
       
       /**
        * 查询所有的用户
        */
       private static void selectAllUser(){
           SqlSession session = DBTools.getSession();
           UserMapper mapper = session.getMapper(UserMapper.class);
           try {
               List<UserBean> user = mapper.selectAllUser();
               System.out.println(user.toString());
               session.commit();
           } catch (Exception e) {
               e.printStackTrace();
               session.rollback();
           }
       }
   }
```
 

## 总结

MyBatis的优点：

1. 基于SQL语法，简单易学。

2. sql写在xml里，便于统一管理和优化。

3. 降低sql与程序代码的耦合。

4. 提供映射标签，支持对象与数据库的orm字段关系映射

5. 提供对象关系映射标签，支持对象关系组建维护

6. 提供xml标签，支持编写动态sql。

7. 能了解底层组装过程。

8. 传统的jdbc相比，减少了大量的代码量，是最简单的持久化框架。

9. 所有sql语句，全部定义在xml（建议）中。也可以通过注解的方式在接口上实现。这些映射文件称之为mapper.

10. sql代码从程序代码中彻底分离，可重用，增强了项目中的分工，增强了移植性

MyBatis的缺点：

1. sql工作量很大，尤其是字段多、关联表多时，更是如此。

2. sql依赖于数据库，导致数据库移植性差。

3. 由于xml里标签id必须唯一，导致DAO中方法不支持方法重载。

4. 字段映射标签和对象关系映射标签仅仅是对映射关系的描述，具体实现仍然依赖于sql。（比如配置了一对多Collection标签，如果sql里没有join子表或查询子表的话，查询后返回的对象是不具备对象关系的，即Collection的对象为null）

5. DAO层过于简单，对象组装的工作量较大。

6.  不支持级联更新、级联删除。

7. 编写动态sql时,不方便调试，尤其逻辑复杂时。

8. 提供的写动态sql的xml标签功能简单（连struts都比不上），编写动态sql仍然受限，且可读性低。

9. 若不查询主键字段，容易造成查询出的对象有“覆盖”现象。

10. 参数的数据类型支持不完善。（如参数为Date类型时，容易报没有get、set方法，需在参数上加@param）

11. 多参数时，使用不方便，功能不够强大。（目前支持的方法有map、对象、注解@param以及默认采用012索引位的方式）

12. 缓存使用不当，容易产生脏数据。

 

总结：

mybatis的优点其实也是mybatis的缺点，正因为mybatis使用简单，数据的可靠性、完整性的瓶颈便更多依赖于程序员对sql的使用水平上了。sql写在xml里，虽然方便了修改、优化和统一浏览，但可读性很低，调试也非常困难，也非常受限，无法像jdbc那样在代码里根据逻辑实现复杂动态sql拼接。mybatis简单看就是提供了字段映射和对象关系映射的jdbc，省去了数据赋值到对象的步骤而已，除此以外并无太多作为，不要把它想象成hibernate那样强大，简单小巧易用上手，方便浏览修改sql就是它最大的优点了。

mybatis适用于小型且程序员能力较低的项目和人群使用，对于中大型项目来说我并不推荐使用，如果觉得hibernate效率低的话（实际上也是使用不当所致，hibernate是实际上是不适用于拥有高负载的工程项目），还不如直接用spring提供的jdbc简单框架（Template），同样支持对象映射。
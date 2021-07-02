# 常用注解的简单解析

--------------------------------------

## Spring中经常使用的一些注解

| 注解           | 作用                                                         |
| -------------- | :----------------------------------------------------------- |
| @Autowired     | Spring提供的自动装配bean。@Autowired是通过**byType**方式实现的。要想使用自动装配，必须把相关类注册到spring中，例如使用@Component、@Service、@Controller、@Repository**[常用]** |
| @Resource      | Java提供的自动装配bean，和@Autowired的功能一样。@Resource是通过**byName**的方式实现的。 |
| @Qualifier     | 当@Autowired无法找到相应的bean时使用该注解定义路径           |
| @Component     | 自动装配的注解（没有明确角色），相当于在XML中配置<bean id="name" class="path"/>。要在XML中配置<context: component-scan base-package="path"/>和<context: annotation-config/>才能生效。 |
| @Service       | 和@Component作用一样，但是在**Service**层中，把某个类注册到spring中进行装配 |
| @Controller    | 和@Component作用一样，但是在**Controller**层中，把某个类注册到spring中进行装配 |
| @Repository    | 和@Component作用一样，但是在**DAO**层中，把某个类注册到spring中进行装配 |
| @Value         | 相当于<bean>标签里面的<property name="name" value="value"/>  |
| @Configuration |                                                              |
| @bean          |                                                              |

-------------------------

## 请求、响应和验证方面的注解

|注解|作用|
|----|----|
|@RequestMapping|@RequestMapping是一个用来**处理请求**地址映射的注解，可用于类或方法上。用于类上，表示访问类中所有方法的请求都以此注解中地址值为父路径。 用于方法上，表示在类的父路径下追加方法上注解中的地址将会访问到该方法。|
|@GetMapping|= @RequestMapping(method = RequestMethod.GET)|
|@PostMapping|=@RequestMapping(method = RequestMethod.POST)|
|@ResponseBody|@ResponseBody注解通常修饰一个方法，将方法中返回的对象转化为json格式写入HTTP响应正文中，传递到前端。通常使用在 @RequestMapping 后，返回结果不会被解析为跳转路径，而是直接写入HTTP 响应正文中。|
|@RequestBody|@RequestBody修饰类中方法某个形参，表示此参数接收请求中请求体，且请求体只能以json格式传输，并能将json数据转化为对应的java对象上|
|@RequestParam|@RequestParam注解修饰方法中形参，获取请求中特定的请求参数值并赋值给形参，同时可以对特定的请求参数进行验证、设置默认值等等|
|@Validated||

-------------------------

|注解|作用|
|----|----|
|@JsonIgnore|在json序列化时将pojo/DAO中标记的属性或者方法忽略掉，返回的json数据即不包含该属性。|
|@NoArgsConstructor|当类中有 final 字段没有被初始化时，编译器会报错，此时可用 @NoArgsConstructor(force = true)，然后就会为没有初始化的 final 字段设置默认值 0 / false / null。对于具有约束的字段（例如 @NonNull 字段），不会生成检查或分配，因此请注意，正确初始化这些字段之前，这些约束无效。|
|@Data|注解在类上, 为类提供读写属性, 此外还提供了 equals()、hashCode()、toString() 方法。|


---------------------

## HTTP 请求方法

| 方法   | 描述                                                         |
| ------ | ------------------------------------------------------------ |
| GET    | 请求从服务器获取特定资源。举个例子：`GET /users`（获取所有学生） |
| POST   | 向指定资源提交数据进行处理请求（例如提交表单或者上传文件）。数据被包含在请求体中。POST 请求可能会导致新的资源的建立和/或已有资源的修改。在服务器上创建一个新的资源。举个例子：`POST /users`（创建学生） |
| PUT    | 更新服务器上的资源（客户端提供更新后的整个资源）。举个例子：`PUT /users/12`（更新编号为 12 的学生） |
| DELETE | 从服务器删除特定的资源。举个例子：`DELETE /users/12`（删除编号为 12 的学生） |

### POST和GET的区别

1. POST 是被设计用来向上放东西的，而GET是被设计用来从服务器取东西的，GET也能够向服务器传送较少的数据，而Get之所以也能传送数据,只是用来设计告诉服务器,你到底需要什么样的数据。POST的信息作为HTTP 请求的内容，而GET是在HTTP 头部传输的。
2. POST与GET在HTTP 中传送的方式不同，GET的参数是在HTTP 的头部传送的，而Post的数据则是在HTTP 请求的内容里传送。
3. POST传输数据时，不需要在URL中显示出来，而GET方法要在URL中显示。
4. GET方法由于受到URL长度的限制,只能传递大约1024字节；POST传输的数据量大，可以达到2M。








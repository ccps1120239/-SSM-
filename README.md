## 关于SSM三大框架整合的配置文件说明
- pom.xml

		前提必须是maven工程；
		里面主要是spring、mybatis，servlet-api、junit、log4j、文件上传、数据库驱动、
		annotation、Java EE jar包、aop、jstl、mybatis分页插件等等依赖；
		需要注意的是：
			log4j：我在此pom文件中添加了多种log4j依赖的选择，可根据自己的使用习惯、项目需求去自行
			删除或注释掉自己不需要的log4j的配置；
			
- spring-mybatis.xml（applicationContext.xml）

		此文件内已经将spring和mybatis进行了整合；
		主要有：
			自动扫描、加载jdbc.properties文件、配置连接池数据源
			注意：配置连接池中，我提供了Druid和dbcp两种连接池的配置，可根据你的需求选择其一即可；
			状态过滤器、
			spring与mybatis的结合；
			注意：此项配置默认两者完美结合，不需要配置mybatis的映射配置文件(mybatis-config.xml)
			<!-- 如果需要添加mybatis的映射配置文件就添加如下这句即可  -->
			<!-- 添加mybatis-config配置文件到spring中  -->
			<property name="configLocation" value="classpath:mybatis-config.xml"><property>
			如果需要，则添加，如果不需要，则把里面的这项删除即可;
			Mapper映射所在包的配置(就是我们所知道的Dao)、
			配置aop拦截service、
			配置事物增强，事物如何切入
- spring-mvc.xml

		上面已经完成了spring和mybatis两大框架的配置，springmvc的配置我们单独放；
		主要有：
			配置包自动扫描、
			Json数据格式转换配置、
			静态资源的访问配置、
			启动SpringMVC的注解功能，完成请求和注解POJO的映射、
			定义跳转的文件的前后缀 ，视图模式配置、
			文件上传解析器
- jdbc.properties

		数据库连接池的数据配置；

- log4j.properties与log4j.xml

		这俩文件可以二选一，具体点击进入这俩文件参考注释说明；
		
- mybatis-config.xml(可选)
		
		此项配置对应上述spring-mybatis文件中的spring和mybatis文件结合配置部分的mybatis映射文件；
		具体参照上述做法；
		mybatis控制台LOG输出；
		别名设置(可选)；
		mybatis分页插件(可选)；
- web.xml

		主要有：
			加载spring容器(Spring和mybatis的配置文件);
			spring监听器；
			防止Spring内存溢出监听器；
			配置SpringMVC核心控制器；
			编码过滤器；

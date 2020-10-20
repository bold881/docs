# 在SpringBoot应用中集成mybatis

1. 引入依赖

   ```xml
   		<dependency>
   			<groupId>org.mybatis.spring.boot</groupId>
   			<artifactId>mybatis-spring-boot-starter</artifactId>
   			<version>${mybatis.version}</version>
   		</dependency>
   ```

2. 配置文件中设置mapper地址

   ```yaml
   mybatis:
     mapper-locations: mappers/**/*.xml
   ```

   



#案例介绍及原因

类似此案例的情况:
https://github.com/spring-projects/spring-boot/issues/3850

最后查的原因: 
@ComponentScan: 允许程序自动扫描包，扫描当前包及其子包下标注了@Component

参考:
https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/context/annotation/ComponentScan.html

默认是实例化当前包的spring bean，如果你的包放在了根目录，那么就是全部实例化了，但是springboot的auto-configration又会存在很多不存在的，so启动报错

# 问题
## 正常
将application移动到根目录后启动报错如下
## 错误
将application移动到根目录后启动报错如下
```
/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/bin/java "-javaagent:/Applications/IntelliJ IDEA.app/Contents/lib/idea_rt.jar=50914:/Applications/IntelliJ IDEA.app/Contents/bin" -Dfile.encoding=UTF-8 -classpath /Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/charsets.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/deploy.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/ext/cldrdata.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/ext/dnsns.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/ext/jaccess.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/ext/jfxrt.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/ext/localedata.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/ext/nashorn.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/ext/sunec.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/ext/sunjce_provider.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/ext/sunpkcs11.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/ext/zipfs.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/javaws.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/jce.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/jfr.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/jfxswt.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/jsse.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/management-agent.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/plugin.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/resources.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/rt.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/lib/ant-javafx.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/lib/dt.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/lib/javafx-mx.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/lib/jconsole.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/lib/packager.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/lib/sa-jdi.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/lib/tools.jar:/Users/victor/Downloads/demo2/target/classes:/Users/victor/.m2/repository/org/springframework/boot/spring-boot-starter-web/2.1.2.RELEASE/spring-boot-starter-web-2.1.2.RELEASE.jar:/Users/victor/.m2/repository/org/springframework/boot/spring-boot-starter/2.1.2.RELEASE/spring-boot-starter-2.1.2.RELEASE.jar:/Users/victor/.m2/repository/org/springframework/boot/spring-boot/2.1.2.RELEASE/spring-boot-2.1.2.RELEASE.jar:/Users/victor/.m2/repository/org/springframework/boot/spring-boot-autoconfigure/2.1.2.RELEASE/spring-boot-autoconfigure-2.1.2.RELEASE.jar:/Users/victor/.m2/repository/org/springframework/boot/spring-boot-starter-logging/2.1.2.RELEASE/spring-boot-starter-logging-2.1.2.RELEASE.jar:/Users/victor/.m2/repository/ch/qos/logback/logback-classic/1.2.3/logback-classic-1.2.3.jar:/Users/victor/.m2/repository/ch/qos/logback/logback-core/1.2.3/logback-core-1.2.3.jar:/Users/victor/.m2/repository/org/apache/logging/log4j/log4j-to-slf4j/2.11.1/log4j-to-slf4j-2.11.1.jar:/Users/victor/.m2/repository/org/apache/logging/log4j/log4j-api/2.11.1/log4j-api-2.11.1.jar:/Users/victor/.m2/repository/org/slf4j/jul-to-slf4j/1.7.25/jul-to-slf4j-1.7.25.jar:/Users/victor/.m2/repository/javax/annotation/javax.annotation-api/1.3.2/javax.annotation-api-1.3.2.jar:/Users/victor/.m2/repository/org/yaml/snakeyaml/1.23/snakeyaml-1.23.jar:/Users/victor/.m2/repository/org/springframework/boot/spring-boot-starter-json/2.1.2.RELEASE/spring-boot-starter-json-2.1.2.RELEASE.jar:/Users/victor/.m2/repository/com/fasterxml/jackson/core/jackson-databind/2.9.8/jackson-databind-2.9.8.jar:/Users/victor/.m2/repository/com/fasterxml/jackson/core/jackson-annotations/2.9.0/jackson-annotations-2.9.0.jar:/Users/victor/.m2/repository/com/fasterxml/jackson/core/jackson-core/2.9.8/jackson-core-2.9.8.jar:/Users/victor/.m2/repository/com/fasterxml/jackson/datatype/jackson-datatype-jdk8/2.9.8/jackson-datatype-jdk8-2.9.8.jar:/Users/victor/.m2/repository/com/fasterxml/jackson/datatype/jackson-datatype-jsr310/2.9.8/jackson-datatype-jsr310-2.9.8.jar:/Users/victor/.m2/repository/com/fasterxml/jackson/module/jackson-module-parameter-names/2.9.8/jackson-module-parameter-names-2.9.8.jar:/Users/victor/.m2/repository/org/springframework/boot/spring-boot-starter-tomcat/2.1.2.RELEASE/spring-boot-starter-tomcat-2.1.2.RELEASE.jar:/Users/victor/.m2/repository/org/apache/tomcat/embed/tomcat-embed-core/9.0.14/tomcat-embed-core-9.0.14.jar:/Users/victor/.m2/repository/org/apache/tomcat/embed/tomcat-embed-el/9.0.14/tomcat-embed-el-9.0.14.jar:/Users/victor/.m2/repository/org/apache/tomcat/embed/tomcat-embed-websocket/9.0.14/tomcat-embed-websocket-9.0.14.jar:/Users/victor/.m2/repository/org/hibernate/validator/hibernate-validator/6.0.14.Final/hibernate-validator-6.0.14.Final.jar:/Users/victor/.m2/repository/javax/validation/validation-api/2.0.1.Final/validation-api-2.0.1.Final.jar:/Users/victor/.m2/repository/org/jboss/logging/jboss-logging/3.3.2.Final/jboss-logging-3.3.2.Final.jar:/Users/victor/.m2/repository/com/fasterxml/classmate/1.4.0/classmate-1.4.0.jar:/Users/victor/.m2/repository/org/springframework/spring-web/5.1.4.RELEASE/spring-web-5.1.4.RELEASE.jar:/Users/victor/.m2/repository/org/springframework/spring-beans/5.1.4.RELEASE/spring-beans-5.1.4.RELEASE.jar:/Users/victor/.m2/repository/org/springframework/spring-webmvc/5.1.4.RELEASE/spring-webmvc-5.1.4.RELEASE.jar:/Users/victor/.m2/repository/org/springframework/spring-aop/5.1.4.RELEASE/spring-aop-5.1.4.RELEASE.jar:/Users/victor/.m2/repository/org/springframework/spring-context/5.1.4.RELEASE/spring-context-5.1.4.RELEASE.jar:/Users/victor/.m2/repository/org/springframework/spring-expression/5.1.4.RELEASE/spring-expression-5.1.4.RELEASE.jar:/Users/victor/.m2/repository/org/slf4j/slf4j-api/1.7.25/slf4j-api-1.7.25.jar:/Users/victor/.m2/repository/org/springframework/spring-core/5.1.4.RELEASE/spring-core-5.1.4.RELEASE.jar:/Users/victor/.m2/repository/org/springframework/spring-jcl/5.1.4.RELEASE/spring-jcl-5.1.4.RELEASE.jar DemoApplication
objc[12849]: Class JavaLaunchHelper is implemented in both /Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/bin/java (0x10cb5d4c0) and /Library/Java/JavaVirtualMachines/jdk1.8.0_151.jdk/Contents/Home/jre/lib/libinstrument.dylib (0x10cbe94e0). One of the two will be used. Which one is undefined.

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v2.1.2.RELEASE)

2019-01-18 17:22:13.727  INFO 12849 --- [           main] DemoApplication                          : Starting DemoApplication on victordeMacBook-Pro.local with PID 12849 (/Users/victor/Downloads/demo2/target/classes started by victor in /Users/victor/Downloads/demo2)
2019-01-18 17:22:13.731  INFO 12849 --- [           main] DemoApplication                          : No active profile set, falling back to default profiles: default
2019-01-18 17:22:13.846  WARN 12849 --- [           main] ionWarningsApplicationContextInitializer : 

** WARNING ** : Your ApplicationContext is unlikely to start due to a @ComponentScan of the default package.


2019-01-18 17:22:19.231  WARN 12849 --- [           main] ConfigServletWebServerApplicationContext : Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanDefinitionStoreException: Failed to read candidate component class: URL [jar:file:/Users/victor/.m2/repository/org/springframework/boot/spring-boot-autoconfigure/2.1.2.RELEASE/spring-boot-autoconfigure-2.1.2.RELEASE.jar!/org/springframework/boot/autoconfigure/jdbc/DataSourceAutoConfiguration$EmbeddedDatabaseConfiguration.class]; nested exception is java.lang.IllegalStateException: Could not evaluate condition on org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration$EmbeddedDatabaseConfiguration due to org/springframework/dao/DataAccessException not found. Make sure your own configuration does not rely on that class. This can also happen if you are @ComponentScanning a springframework package (e.g. if you put a @ComponentScan in the default package by mistake)
2019-01-18 17:22:19.244  INFO 12849 --- [           main] ConditionEvaluationReportLoggingListener : 

Error starting ApplicationContext. To display the conditions report re-run your application with 'debug' enabled.
2019-01-18 17:22:19.269 ERROR 12849 --- [           main] o.s.boot.SpringApplication               : Application run failed

org.springframework.beans.factory.BeanDefinitionStoreException: Failed to read candidate component class: URL [jar:file:/Users/victor/.m2/repository/org/springframework/boot/spring-boot-autoconfigure/2.1.2.RELEASE/spring-boot-autoconfigure-2.1.2.RELEASE.jar!/org/springframework/boot/autoconfigure/jdbc/DataSourceAutoConfiguration$EmbeddedDatabaseConfiguration.class]; nested exception is java.lang.IllegalStateException: Could not evaluate condition on org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration$EmbeddedDatabaseConfiguration due to org/springframework/dao/DataAccessException not found. Make sure your own configuration does not rely on that class. This can also happen if you are @ComponentScanning a springframework package (e.g. if you put a @ComponentScan in the default package by mistake)
	at org.springframework.context.annotation.ClassPathScanningCandidateComponentProvider.scanCandidateComponents(ClassPathScanningCandidateComponentProvider.java:454) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ClassPathScanningCandidateComponentProvider.findCandidateComponents(ClassPathScanningCandidateComponentProvider.java:316) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ClassPathBeanDefinitionScanner.doScan(ClassPathBeanDefinitionScanner.java:275) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ComponentScanAnnotationParser.parse(ComponentScanAnnotationParser.java:132) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ConfigurationClassParser.doProcessConfigurationClass(ConfigurationClassParser.java:287) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ConfigurationClassParser.processConfigurationClass(ConfigurationClassParser.java:242) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ConfigurationClassParser.parse(ConfigurationClassParser.java:199) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ConfigurationClassParser.parse(ConfigurationClassParser.java:167) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ConfigurationClassPostProcessor.processConfigBeanDefinitions(ConfigurationClassPostProcessor.java:315) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ConfigurationClassPostProcessor.postProcessBeanDefinitionRegistry(ConfigurationClassPostProcessor.java:232) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.support.PostProcessorRegistrationDelegate.invokeBeanDefinitionRegistryPostProcessors(PostProcessorRegistrationDelegate.java:275) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.support.PostProcessorRegistrationDelegate.invokeBeanFactoryPostProcessors(PostProcessorRegistrationDelegate.java:95) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.support.AbstractApplicationContext.invokeBeanFactoryPostProcessors(AbstractApplicationContext.java:691) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:528) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:142) ~[spring-boot-2.1.2.RELEASE.jar:2.1.2.RELEASE]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:775) [spring-boot-2.1.2.RELEASE.jar:2.1.2.RELEASE]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:397) [spring-boot-2.1.2.RELEASE.jar:2.1.2.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:316) [spring-boot-2.1.2.RELEASE.jar:2.1.2.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1260) [spring-boot-2.1.2.RELEASE.jar:2.1.2.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1248) [spring-boot-2.1.2.RELEASE.jar:2.1.2.RELEASE]
	at DemoApplication.main(DemoApplication.java:10) [classes/:na]
Caused by: java.lang.IllegalStateException: Could not evaluate condition on org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration$EmbeddedDatabaseConfiguration due to org/springframework/dao/DataAccessException not found. Make sure your own configuration does not rely on that class. This can also happen if you are @ComponentScanning a springframework package (e.g. if you put a @ComponentScan in the default package by mistake)
	at org.springframework.boot.autoconfigure.condition.SpringBootCondition.matches(SpringBootCondition.java:55) ~[spring-boot-autoconfigure-2.1.2.RELEASE.jar:2.1.2.RELEASE]
	at org.springframework.context.annotation.ConditionEvaluator.shouldSkip(ConditionEvaluator.java:108) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ConditionEvaluator.shouldSkip(ConditionEvaluator.java:88) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ConditionEvaluator.shouldSkip(ConditionEvaluator.java:71) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ClassPathScanningCandidateComponentProvider.isConditionMatch(ClassPathScanningCandidateComponentProvider.java:515) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ClassPathScanningCandidateComponentProvider.isCandidateComponent(ClassPathScanningCandidateComponentProvider.java:498) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	at org.springframework.context.annotation.ClassPathScanningCandidateComponentProvider.scanCandidateComponents(ClassPathScanningCandidateComponentProvider.java:431) ~[spring-context-5.1.4.RELEASE.jar:5.1.4.RELEASE]
	... 20 common frames omitted
Caused by: java.lang.NoClassDefFoundError: org/springframework/dao/DataAccessException
	at org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration$EmbeddedDatabaseCondition.getMatchOutcome(DataSourceAutoConfiguration.java:148) ~[spring-boot-autoconfigure-2.1.2.RELEASE.jar:2.1.2.RELEASE]
	at org.springframework.boot.autoconfigure.condition.SpringBootCondition.matches(SpringBootCondition.java:47) ~[spring-boot-autoconfigure-2.1.2.RELEASE.jar:2.1.2.RELEASE]
	... 26 common frames omitted
Caused by: java.lang.ClassNotFoundException: org.springframework.dao.DataAccessException
	at java.net.URLClassLoader.findClass(URLClassLoader.java:381) ~[na:1.8.0_151]
	at java.lang.ClassLoader.loadClass(ClassLoader.java:424) ~[na:1.8.0_151]
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:335) ~[na:1.8.0_151]
	at java.lang.ClassLoader.loadClass(ClassLoader.java:357) ~[na:1.8.0_151]
	... 28 common frames omitted


Process finished with exit code 1
```

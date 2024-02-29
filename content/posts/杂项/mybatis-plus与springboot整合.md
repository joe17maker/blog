---
title: "Mybatis-plus整合springboot"
date: 2022-08-14T10:40:10+08:00
draft: false
tags: ["bug"]
categories: ["杂项"]
---
遇到这个bug第二次了记录一下吧。遇到一个非常诡异的bug, 结果居然是springboot版本太高，不支持3.5.4的mybatis-plus.springboot版本为3.2.0，改为3.1.2正常。这种bug太难排查了。
```
C:\Users\A\.jdks\corretto-17.0.8.1\bin\java.exe -ea -Didea.test.cyclic.buffer.size=1048576 "-javaagent:E:\program files\IntelliJ IDEA Community Edition 2022.2.1\lib\idea_rt.jar=7755:E:\program files\IntelliJ IDEA Community Edition 2022.2.1\bin" -Dfile.encoding=UTF-8 -classpath "C:\Users\A\.m2\repository\org\junit\platform\junit-platform-launcher\1.10.0\junit-platform-launcher-1.10.0.jar;C:\Users\A\.m2\repository\org\junit\vintage\junit-vintage-engine\5.10.0\junit-vintage-engine-5.10.0.jar;E:\program files\IntelliJ IDEA Community Edition 2022.2.1\lib\idea_rt.jar;E:\program files\IntelliJ IDEA Community Edition 2022.2.1\plugins\junit\lib\junit5-rt.jar;E:\program files\IntelliJ IDEA Community Edition 2022.2.1\plugins\junit\lib\junit-rt.jar;E:\mycommunity\coderconnect\target\test-classes;E:\mycommunity\coderconnect\target\classes;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot-starter-web\3.2.0-SNAPSHOT\spring-boot-starter-web-3.2.0-20231027.174801-479.jar;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot-starter\3.2.0-SNAPSHOT\spring-boot-starter-3.2.0-20231027.174801-479.jar;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot-starter-logging\3.2.0-SNAPSHOT\spring-boot-starter-logging-3.2.0-20231027.174801-479.jar;C:\Users\A\.m2\repository\ch\qos\logback\logback-classic\1.4.11\logback-classic-1.4.11.jar;C:\Users\A\.m2\repository\ch\qos\logback\logback-core\1.4.11\logback-core-1.4.11.jar;C:\Users\A\.m2\repository\org\apache\logging\log4j\log4j-to-slf4j\2.21.0\log4j-to-slf4j-2.21.0.jar;C:\Users\A\.m2\repository\org\apache\logging\log4j\log4j-api\2.21.0\log4j-api-2.21.0.jar;C:\Users\A\.m2\repository\org\slf4j\jul-to-slf4j\2.0.9\jul-to-slf4j-2.0.9.jar;C:\Users\A\.m2\repository\jakarta\annotation\jakarta.annotation-api\2.1.1\jakarta.annotation-api-2.1.1.jar;C:\Users\A\.m2\repository\org\yaml\snakeyaml\2.2\snakeyaml-2.2.jar;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot-starter-json\3.2.0-SNAPSHOT\spring-boot-starter-json-3.2.0-20231027.174801-479.jar;C:\Users\A\.m2\repository\com\fasterxml\jackson\core\jackson-databind\2.15.3\jackson-databind-2.15.3.jar;C:\Users\A\.m2\repository\com\fasterxml\jackson\core\jackson-annotations\2.15.3\jackson-annotations-2.15.3.jar;C:\Users\A\.m2\repository\com\fasterxml\jackson\core\jackson-core\2.15.3\jackson-core-2.15.3.jar;C:\Users\A\.m2\repository\com\fasterxml\jackson\datatype\jackson-datatype-jdk8\2.15.3\jackson-datatype-jdk8-2.15.3.jar;C:\Users\A\.m2\repository\com\fasterxml\jackson\datatype\jackson-datatype-jsr310\2.15.3\jackson-datatype-jsr310-2.15.3.jar;C:\Users\A\.m2\repository\com\fasterxml\jackson\module\jackson-module-parameter-names\2.15.3\jackson-module-parameter-names-2.15.3.jar;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot-starter-tomcat\3.2.0-SNAPSHOT\spring-boot-starter-tomcat-3.2.0-20231027.174801-479.jar;C:\Users\A\.m2\repository\org\apache\tomcat\embed\tomcat-embed-core\10.1.15\tomcat-embed-core-10.1.15.jar;C:\Users\A\.m2\repository\org\apache\tomcat\embed\tomcat-embed-el\10.1.15\tomcat-embed-el-10.1.15.jar;C:\Users\A\.m2\repository\org\apache\tomcat\embed\tomcat-embed-websocket\10.1.15\tomcat-embed-websocket-10.1.15.jar;C:\Users\A\.m2\repository\org\springframework\spring-web\6.1.0-SNAPSHOT\spring-web-6.1.0-20231028.145402-786.jar;C:\Users\A\.m2\repository\org\springframework\spring-beans\6.1.0-SNAPSHOT\spring-beans-6.1.0-20231028.145402-786.jar;C:\Users\A\.m2\repository\io\micrometer\micrometer-observation\1.12.0-RC1\micrometer-observation-1.12.0-RC1.jar;C:\Users\A\.m2\repository\io\micrometer\micrometer-commons\1.12.0-RC1\micrometer-commons-1.12.0-RC1.jar;C:\Users\A\.m2\repository\org\springframework\spring-webmvc\6.1.0-SNAPSHOT\spring-webmvc-6.1.0-20231028.145402-786.jar;C:\Users\A\.m2\repository\org\springframework\spring-aop\6.1.0-SNAPSHOT\spring-aop-6.1.0-20231028.145402-786.jar;C:\Users\A\.m2\repository\org\springframework\spring-context\6.1.0-SNAPSHOT\spring-context-6.1.0-20231028.145402-786.jar;C:\Users\A\.m2\repository\org\springframework\spring-expression\6.1.0-SNAPSHOT\spring-expression-6.1.0-20231028.145402-786.jar;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot-devtools\3.2.0-SNAPSHOT\spring-boot-devtools-3.2.0-20231027.174801-479.jar;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot\3.2.0-SNAPSHOT\spring-boot-3.2.0-20231027.174801-479.jar;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot-autoconfigure\3.2.0-SNAPSHOT\spring-boot-autoconfigure-3.2.0-20231027.174801-480.jar;C:\Users\A\.m2\repository\com\mysql\mysql-connector-j\8.1.0\mysql-connector-j-8.1.0.jar;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot-configuration-processor\3.2.0-SNAPSHOT\spring-boot-configuration-processor-3.2.0-20231027.174801-479.jar;C:\Users\A\.m2\repository\org\projectlombok\lombok\1.18.30\lombok-1.18.30.jar;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot-starter-test\3.2.0-SNAPSHOT\spring-boot-starter-test-3.2.0-20231027.174801-479.jar;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot-test\3.2.0-SNAPSHOT\spring-boot-test-3.2.0-20231027.174801-479.jar;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot-test-autoconfigure\3.2.0-SNAPSHOT\spring-boot-test-autoconfigure-3.2.0-20231027.174801-479.jar;C:\Users\A\.m2\repository\com\jayway\jsonpath\json-path\2.8.0\json-path-2.8.0.jar;C:\Users\A\.m2\repository\jakarta\xml\bind\jakarta.xml.bind-api\4.0.1\jakarta.xml.bind-api-4.0.1.jar;C:\Users\A\.m2\repository\jakarta\activation\jakarta.activation-api\2.1.2\jakarta.activation-api-2.1.2.jar;C:\Users\A\.m2\repository\net\minidev\json-smart\2.5.0\json-smart-2.5.0.jar;C:\Users\A\.m2\repository\net\minidev\accessors-smart\2.5.0\accessors-smart-2.5.0.jar;C:\Users\A\.m2\repository\org\ow2\asm\asm\9.3\asm-9.3.jar;C:\Users\A\.m2\repository\org\assertj\assertj-core\3.24.2\assertj-core-3.24.2.jar;C:\Users\A\.m2\repository\net\bytebuddy\byte-buddy\1.14.9\byte-buddy-1.14.9.jar;C:\Users\A\.m2\repository\org\awaitility\awaitility\4.2.0\awaitility-4.2.0.jar;C:\Users\A\.m2\repository\org\hamcrest\hamcrest\2.2\hamcrest-2.2.jar;C:\Users\A\.m2\repository\org\junit\jupiter\junit-jupiter\5.10.0\junit-jupiter-5.10.0.jar;C:\Users\A\.m2\repository\org\junit\jupiter\junit-jupiter-api\5.10.0\junit-jupiter-api-5.10.0.jar;C:\Users\A\.m2\repository\org\opentest4j\opentest4j\1.3.0\opentest4j-1.3.0.jar;C:\Users\A\.m2\repository\org\junit\platform\junit-platform-commons\1.10.0\junit-platform-commons-1.10.0.jar;C:\Users\A\.m2\repository\org\apiguardian\apiguardian-api\1.1.2\apiguardian-api-1.1.2.jar;C:\Users\A\.m2\repository\org\junit\jupiter\junit-jupiter-params\5.10.0\junit-jupiter-params-5.10.0.jar;C:\Users\A\.m2\repository\org\junit\jupiter\junit-jupiter-engine\5.10.0\junit-jupiter-engine-5.10.0.jar;C:\Users\A\.m2\repository\org\junit\platform\junit-platform-engine\1.10.0\junit-platform-engine-1.10.0.jar;C:\Users\A\.m2\repository\org\mockito\mockito-core\5.6.0\mockito-core-5.6.0.jar;C:\Users\A\.m2\repository\net\bytebuddy\byte-buddy-agent\1.14.9\byte-buddy-agent-1.14.9.jar;C:\Users\A\.m2\repository\org\objenesis\objenesis\3.3\objenesis-3.3.jar;C:\Users\A\.m2\repository\org\mockito\mockito-junit-jupiter\5.6.0\mockito-junit-jupiter-5.6.0.jar;C:\Users\A\.m2\repository\org\skyscreamer\jsonassert\1.5.1\jsonassert-1.5.1.jar;C:\Users\A\.m2\repository\com\vaadin\external\google\android-json\0.0.20131108.vaadin1\android-json-0.0.20131108.vaadin1.jar;C:\Users\A\.m2\repository\org\springframework\spring-core\6.1.0-SNAPSHOT\spring-core-6.1.0-20231028.145402-786.jar;C:\Users\A\.m2\repository\org\springframework\spring-jcl\6.1.0-SNAPSHOT\spring-jcl-6.1.0-20231028.145402-786.jar;C:\Users\A\.m2\repository\org\springframework\spring-test\6.1.0-SNAPSHOT\spring-test-6.1.0-20231028.145402-786.jar;C:\Users\A\.m2\repository\org\xmlunit\xmlunit-core\2.9.1\xmlunit-core-2.9.1.jar;C:\Users\A\.m2\repository\com\baomidou\mybatis-plus-boot-starter\3.5.4\mybatis-plus-boot-starter-3.5.4.jar;C:\Users\A\.m2\repository\com\baomidou\mybatis-plus\3.5.4\mybatis-plus-3.5.4.jar;C:\Users\A\.m2\repository\com\baomidou\mybatis-plus-core\3.5.4\mybatis-plus-core-3.5.4.jar;C:\Users\A\.m2\repository\com\baomidou\mybatis-plus-annotation\3.5.4\mybatis-plus-annotation-3.5.4.jar;C:\Users\A\.m2\repository\com\baomidou\mybatis-plus-extension\3.5.4\mybatis-plus-extension-3.5.4.jar;C:\Users\A\.m2\repository\org\mybatis\mybatis\3.5.13\mybatis-3.5.13.jar;C:\Users\A\.m2\repository\com\github\jsqlparser\jsqlparser\4.6\jsqlparser-4.6.jar;C:\Users\A\.m2\repository\org\mybatis\mybatis-spring\2.1.1\mybatis-spring-2.1.1.jar;C:\Users\A\.m2\repository\com\baomidou\mybatis-plus-spring-boot-autoconfigure\3.5.4\mybatis-plus-spring-boot-autoconfigure-3.5.4.jar;C:\Users\A\.m2\repository\org\springframework\boot\spring-boot-starter-jdbc\3.2.0-SNAPSHOT\spring-boot-starter-jdbc-3.2.0-20231027.174801-479.jar;C:\Users\A\.m2\repository\com\zaxxer\HikariCP\5.0.1\HikariCP-5.0.1.jar;C:\Users\A\.m2\repository\org\springframework\spring-jdbc\6.1.0-SNAPSHOT\spring-jdbc-6.1.0-20231028.145402-786.jar;C:\Users\A\.m2\repository\org\springframework\spring-tx\6.1.0-SNAPSHOT\spring-tx-6.1.0-20231028.145402-786.jar;C:\Users\A\.m2\repository\com\baomidou\mybatis-plus-generator\3.5.4\mybatis-plus-generator-3.5.4.jar;C:\Users\A\.m2\repository\org\apache\velocity\velocity-engine-core\2.3\velocity-engine-core-2.3.jar;C:\Users\A\.m2\repository\org\apache\commons\commons-lang3\3.13.0\commons-lang3-3.13.0.jar;C:\Users\A\.m2\repository\org\slf4j\slf4j-api\2.0.9\slf4j-api-2.0.9.jar;C:\Users\A\.m2\repository\junit\junit\4.13.2\junit-4.13.2.jar;C:\Users\A\.m2\repository\org\hamcrest\hamcrest-core\2.2\hamcrest-core-2.2.jar" com.intellij.rt.junit.JUnitStarter -ideVersion5 -junit5 com.joe.coderconnect.service.impl.UserServiceImplTest,test
00:39:57.555 [main] INFO org.springframework.test.context.support.AnnotationConfigContextLoaderUtils -- Could not detect default configuration classes for test class [com.joe.coderconnect.service.impl.UserServiceImplTest]: UserServiceImplTest does not declare any static, non-private, non-final, nested classes annotated with @Configuration.
00:39:57.750 [main] INFO org.springframework.boot.test.context.SpringBootTestContextBootstrapper -- Found @SpringBootConfiguration com.joe.coderconnect.CoderconnectApplication for test class com.joe.coderconnect.service.impl.UserServiceImplTest
00:39:58.006 [main] INFO org.springframework.boot.devtools.restart.RestartApplicationListener -- Restart disabled due to context in which it is running

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::       (v3.2.0-SNAPSHOT)

2023-10-29T00:39:58.423+08:00  INFO 16580 --- [           main] c.j.c.service.impl.UserServiceImplTest   : Starting UserServiceImplTest using Java 17.0.8.1 with PID 16580 (started by A in E:\mycommunity\coderconnect)
2023-10-29T00:39:58.425+08:00  INFO 16580 --- [           main] c.j.c.service.impl.UserServiceImplTest   : No active profile set, falling back to 1 default profile: "default"
2023-10-29T00:39:59.420+08:00  WARN 16580 --- [           main] o.s.w.c.s.GenericWebApplicationContext   : Exception encountered during context initialization - cancelling refresh attempt: java.lang.IllegalArgumentException: Invalid value type for attribute 'factoryBeanObjectType': java.lang.String
2023-10-29T00:39:59.434+08:00  INFO 16580 --- [           main] .s.b.a.l.ConditionEvaluationReportLogger : 

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2023-10-29T00:39:59.459+08:00 ERROR 16580 --- [           main] o.s.boot.SpringApplication               : Application run failed

java.lang.IllegalArgumentException: Invalid value type for attribute 'factoryBeanObjectType': java.lang.String
	at org.springframework.beans.factory.support.FactoryBeanRegistrySupport.getTypeForFactoryBeanFromAttributes(FactoryBeanRegistrySupport.java:86) ~[spring-beans-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.getTypeForFactoryBean(AbstractAutowireCapableBeanFactory.java:838) ~[spring-beans-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.beans.factory.support.AbstractBeanFactory.isTypeMatch(AbstractBeanFactory.java:620) ~[spring-beans-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.doGetBeanNamesForType(DefaultListableBeanFactory.java:573) ~[spring-beans-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.getBeanNamesForType(DefaultListableBeanFactory.java:532) ~[spring-beans-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.context.support.PostProcessorRegistrationDelegate.invokeBeanFactoryPostProcessors(PostProcessorRegistrationDelegate.java:138) ~[spring-context-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.context.support.AbstractApplicationContext.invokeBeanFactoryPostProcessors(AbstractApplicationContext.java:775) ~[spring-context-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:597) ~[spring-context-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:748) ~[spring-boot-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:450) ~[spring-boot-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:322) ~[spring-boot-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.boot.test.context.SpringBootContextLoader.lambda$loadContext$3(SpringBootContextLoader.java:137) ~[spring-boot-test-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.util.function.ThrowingSupplier.get(ThrowingSupplier.java:58) ~[spring-core-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.util.function.ThrowingSupplier.get(ThrowingSupplier.java:46) ~[spring-core-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.boot.SpringApplication.withHook(SpringApplication.java:1436) ~[spring-boot-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.boot.test.context.SpringBootContextLoader$ContextLoaderHook.run(SpringBootContextLoader.java:544) ~[spring-boot-test-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.boot.test.context.SpringBootContextLoader.loadContext(SpringBootContextLoader.java:137) ~[spring-boot-test-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.boot.test.context.SpringBootContextLoader.loadContext(SpringBootContextLoader.java:108) ~[spring-boot-test-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContextInternal(DefaultCacheAwareContextLoaderDelegate.java:225) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContext(DefaultCacheAwareContextLoaderDelegate.java:152) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.test.context.support.DefaultTestContext.getApplicationContext(DefaultTestContext.java:130) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.test.context.web.ServletTestExecutionListener.setUpRequestContextIfNecessary(ServletTestExecutionListener.java:191) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.test.context.web.ServletTestExecutionListener.prepareTestInstance(ServletTestExecutionListener.java:130) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.test.context.TestContextManager.prepareTestInstance(TestContextManager.java:247) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.test.context.junit.jupiter.SpringExtension.postProcessTestInstance(SpringExtension.java:163) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.lambda$invokeTestInstancePostProcessors$10(ClassBasedTestDescriptor.java:378) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.executeAndMaskThrowable(ClassBasedTestDescriptor.java:383) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.lambda$invokeTestInstancePostProcessors$11(ClassBasedTestDescriptor.java:378) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at java.base/java.util.stream.ReferencePipeline$3$1.accept(ReferencePipeline.java:197) ~[na:na]
	at java.base/java.util.stream.ReferencePipeline$2$1.accept(ReferencePipeline.java:179) ~[na:na]
	at java.base/java.util.ArrayList$ArrayListSpliterator.forEachRemaining(ArrayList.java:1625) ~[na:na]
	at java.base/java.util.stream.AbstractPipeline.copyInto(AbstractPipeline.java:509) ~[na:na]
	at java.base/java.util.stream.AbstractPipeline.wrapAndCopyInto(AbstractPipeline.java:499) ~[na:na]
	at java.base/java.util.stream.StreamSpliterators$WrappingSpliterator.forEachRemaining(StreamSpliterators.java:310) ~[na:na]
	at java.base/java.util.stream.Streams$ConcatSpliterator.forEachRemaining(Streams.java:735) ~[na:na]
	at java.base/java.util.stream.Streams$ConcatSpliterator.forEachRemaining(Streams.java:734) ~[na:na]
	at java.base/java.util.stream.ReferencePipeline$Head.forEach(ReferencePipeline.java:762) ~[na:na]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.invokeTestInstancePostProcessors(ClassBasedTestDescriptor.java:377) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.lambda$instantiateAndPostProcessTestInstance$6(ClassBasedTestDescriptor.java:290) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.instantiateAndPostProcessTestInstance(ClassBasedTestDescriptor.java:289) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.lambda$testInstancesProvider$4(ClassBasedTestDescriptor.java:279) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at java.base/java.util.Optional.orElseGet(Optional.java:364) ~[na:na]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.lambda$testInstancesProvider$5(ClassBasedTestDescriptor.java:278) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.execution.TestInstancesProvider.getTestInstances(TestInstancesProvider.java:31) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.lambda$prepare$0(TestMethodTestDescriptor.java:106) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.prepare(TestMethodTestDescriptor.java:105) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.prepare(TestMethodTestDescriptor.java:69) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$prepare$2(NodeTestTask.java:123) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.prepare(NodeTestTask.java:123) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.execute(NodeTestTask.java:90) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at java.base/java.util.ArrayList.forEach(ArrayList.java:1511) ~[na:na]
	at org.junit.platform.engine.support.hierarchical.SameThreadHierarchicalTestExecutorService.invokeAll(SameThreadHierarchicalTestExecutorService.java:41) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$6(NodeTestTask.java:155) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$8(NodeTestTask.java:141) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.Node.around(Node.java:137) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$9(NodeTestTask.java:139) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.executeRecursively(NodeTestTask.java:138) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.execute(NodeTestTask.java:95) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at java.base/java.util.ArrayList.forEach(ArrayList.java:1511) ~[na:na]
	at org.junit.platform.engine.support.hierarchical.SameThreadHierarchicalTestExecutorService.invokeAll(SameThreadHierarchicalTestExecutorService.java:41) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$6(NodeTestTask.java:155) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$8(NodeTestTask.java:141) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.Node.around(Node.java:137) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$9(NodeTestTask.java:139) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.executeRecursively(NodeTestTask.java:138) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.execute(NodeTestTask.java:95) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.SameThreadHierarchicalTestExecutorService.submit(SameThreadHierarchicalTestExecutorService.java:35) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.HierarchicalTestExecutor.execute(HierarchicalTestExecutor.java:57) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.HierarchicalTestEngine.execute(HierarchicalTestEngine.java:54) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.execute(EngineExecutionOrchestrator.java:198) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.execute(EngineExecutionOrchestrator.java:169) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.execute(EngineExecutionOrchestrator.java:93) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.lambda$execute$0(EngineExecutionOrchestrator.java:58) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.withInterceptedStreams(EngineExecutionOrchestrator.java:141) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.execute(EngineExecutionOrchestrator.java:57) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.DefaultLauncher.execute(DefaultLauncher.java:103) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.DefaultLauncher.execute(DefaultLauncher.java:85) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.DelegatingLauncher.execute(DelegatingLauncher.java:47) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.SessionPerRequestLauncher.execute(SessionPerRequestLauncher.java:63) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at com.intellij.junit5.JUnit5IdeaTestRunner.startRunnerWithArgs(JUnit5IdeaTestRunner.java:57) ~[junit5-rt.jar:na]
	at com.intellij.rt.junit.IdeaTestRunner$Repeater$1.execute(IdeaTestRunner.java:38) ~[junit-rt.jar:na]
	at com.intellij.rt.execution.junit.TestsRepeater.repeat(TestsRepeater.java:11) ~[idea_rt.jar:na]
	at com.intellij.rt.junit.IdeaTestRunner$Repeater.startRunnerWithArgs(IdeaTestRunner.java:35) ~[junit-rt.jar:na]
	at com.intellij.rt.junit.JUnitStarter.prepareStreamsAndStart(JUnitStarter.java:235) ~[junit-rt.jar:na]
	at com.intellij.rt.junit.JUnitStarter.main(JUnitStarter.java:54) ~[junit-rt.jar:na]




============================
CONDITIONS EVALUATION REPORT
============================


Positive matches:
-----------------

    None


Negative matches:
-----------------

    None


Exclusions:
-----------

    None


Unconditional classes:
----------------------

    None



2023-10-29T00:39:59.472+08:00 ERROR 16580 --- [           main] o.s.test.context.TestContextManager      : Caught exception while allowing TestExecutionListener [org.springframework.test.context.web.ServletTestExecutionListener] to prepare test instance [com.joe.coderconnect.service.impl.UserServiceImplTest@5555ffcf]

java.lang.IllegalStateException: Failed to load ApplicationContext for [WebMergedContextConfiguration@28cb3a25 testClass = com.joe.coderconnect.service.impl.UserServiceImplTest, locations = [], classes = [com.joe.coderconnect.CoderconnectApplication], contextInitializerClasses = [], activeProfiles = [], propertySourceDescriptors = [], propertySourceProperties = ["org.springframework.boot.test.context.SpringBootTestContextBootstrapper=true"], contextCustomizers = [org.springframework.boot.test.context.filter.ExcludeFilterContextCustomizer@6e6f2380, org.springframework.boot.test.json.DuplicateJsonObjectContextCustomizerFactory$DuplicateJsonObjectContextCustomizer@1530c739, org.springframework.boot.test.mock.mockito.MockitoContextCustomizer@0, org.springframework.boot.test.web.client.TestRestTemplateContextCustomizer@7ef82753, org.springframework.boot.test.autoconfigure.actuate.observability.ObservabilityContextCustomizerFactory$DisableObservabilityContextCustomizer@1f, org.springframework.boot.test.autoconfigure.properties.PropertyMappingContextCustomizer@0, org.springframework.boot.test.autoconfigure.web.servlet.WebDriverContextCustomizer@18271936, org.springframework.boot.test.context.SpringBootTestAnnotation@9d9c1285], resourceBasePath = "src/main/webapp", contextLoader = org.springframework.boot.test.context.SpringBootContextLoader, parent = null]
	at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContext(DefaultCacheAwareContextLoaderDelegate.java:180) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.test.context.support.DefaultTestContext.getApplicationContext(DefaultTestContext.java:130) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.test.context.web.ServletTestExecutionListener.setUpRequestContextIfNecessary(ServletTestExecutionListener.java:191) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.test.context.web.ServletTestExecutionListener.prepareTestInstance(ServletTestExecutionListener.java:130) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.test.context.TestContextManager.prepareTestInstance(TestContextManager.java:247) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.test.context.junit.jupiter.SpringExtension.postProcessTestInstance(SpringExtension.java:163) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.lambda$invokeTestInstancePostProcessors$10(ClassBasedTestDescriptor.java:378) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.executeAndMaskThrowable(ClassBasedTestDescriptor.java:383) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.lambda$invokeTestInstancePostProcessors$11(ClassBasedTestDescriptor.java:378) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at java.base/java.util.stream.ReferencePipeline$3$1.accept(ReferencePipeline.java:197) ~[na:na]
	at java.base/java.util.stream.ReferencePipeline$2$1.accept(ReferencePipeline.java:179) ~[na:na]
	at java.base/java.util.ArrayList$ArrayListSpliterator.forEachRemaining(ArrayList.java:1625) ~[na:na]
	at java.base/java.util.stream.AbstractPipeline.copyInto(AbstractPipeline.java:509) ~[na:na]
	at java.base/java.util.stream.AbstractPipeline.wrapAndCopyInto(AbstractPipeline.java:499) ~[na:na]
	at java.base/java.util.stream.StreamSpliterators$WrappingSpliterator.forEachRemaining(StreamSpliterators.java:310) ~[na:na]
	at java.base/java.util.stream.Streams$ConcatSpliterator.forEachRemaining(Streams.java:735) ~[na:na]
	at java.base/java.util.stream.Streams$ConcatSpliterator.forEachRemaining(Streams.java:734) ~[na:na]
	at java.base/java.util.stream.ReferencePipeline$Head.forEach(ReferencePipeline.java:762) ~[na:na]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.invokeTestInstancePostProcessors(ClassBasedTestDescriptor.java:377) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.lambda$instantiateAndPostProcessTestInstance$6(ClassBasedTestDescriptor.java:290) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.instantiateAndPostProcessTestInstance(ClassBasedTestDescriptor.java:289) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.lambda$testInstancesProvider$4(ClassBasedTestDescriptor.java:279) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at java.base/java.util.Optional.orElseGet(Optional.java:364) ~[na:na]
	at org.junit.jupiter.engine.descriptor.ClassBasedTestDescriptor.lambda$testInstancesProvider$5(ClassBasedTestDescriptor.java:278) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.execution.TestInstancesProvider.getTestInstances(TestInstancesProvider.java:31) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.lambda$prepare$0(TestMethodTestDescriptor.java:106) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.prepare(TestMethodTestDescriptor.java:105) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.prepare(TestMethodTestDescriptor.java:69) ~[junit-jupiter-engine-5.10.0.jar:5.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$prepare$2(NodeTestTask.java:123) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.prepare(NodeTestTask.java:123) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.execute(NodeTestTask.java:90) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at java.base/java.util.ArrayList.forEach(ArrayList.java:1511) ~[na:na]
	at org.junit.platform.engine.support.hierarchical.SameThreadHierarchicalTestExecutorService.invokeAll(SameThreadHierarchicalTestExecutorService.java:41) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$6(NodeTestTask.java:155) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$8(NodeTestTask.java:141) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.Node.around(Node.java:137) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$9(NodeTestTask.java:139) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.executeRecursively(NodeTestTask.java:138) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.execute(NodeTestTask.java:95) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at java.base/java.util.ArrayList.forEach(ArrayList.java:1511) ~[na:na]
	at org.junit.platform.engine.support.hierarchical.SameThreadHierarchicalTestExecutorService.invokeAll(SameThreadHierarchicalTestExecutorService.java:41) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$6(NodeTestTask.java:155) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$8(NodeTestTask.java:141) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.Node.around(Node.java:137) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$9(NodeTestTask.java:139) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.executeRecursively(NodeTestTask.java:138) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.execute(NodeTestTask.java:95) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.SameThreadHierarchicalTestExecutorService.submit(SameThreadHierarchicalTestExecutorService.java:35) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.HierarchicalTestExecutor.execute(HierarchicalTestExecutor.java:57) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.engine.support.hierarchical.HierarchicalTestEngine.execute(HierarchicalTestEngine.java:54) ~[junit-platform-engine-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.execute(EngineExecutionOrchestrator.java:198) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.execute(EngineExecutionOrchestrator.java:169) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.execute(EngineExecutionOrchestrator.java:93) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.lambda$execute$0(EngineExecutionOrchestrator.java:58) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.withInterceptedStreams(EngineExecutionOrchestrator.java:141) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.execute(EngineExecutionOrchestrator.java:57) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.DefaultLauncher.execute(DefaultLauncher.java:103) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.DefaultLauncher.execute(DefaultLauncher.java:85) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.DelegatingLauncher.execute(DelegatingLauncher.java:47) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at org.junit.platform.launcher.core.SessionPerRequestLauncher.execute(SessionPerRequestLauncher.java:63) ~[junit-platform-launcher-1.10.0.jar:1.10.0]
	at com.intellij.junit5.JUnit5IdeaTestRunner.startRunnerWithArgs(JUnit5IdeaTestRunner.java:57) ~[junit5-rt.jar:na]
	at com.intellij.rt.junit.IdeaTestRunner$Repeater$1.execute(IdeaTestRunner.java:38) ~[junit-rt.jar:na]
	at com.intellij.rt.execution.junit.TestsRepeater.repeat(TestsRepeater.java:11) ~[idea_rt.jar:na]
	at com.intellij.rt.junit.IdeaTestRunner$Repeater.startRunnerWithArgs(IdeaTestRunner.java:35) ~[junit-rt.jar:na]
	at com.intellij.rt.junit.JUnitStarter.prepareStreamsAndStart(JUnitStarter.java:235) ~[junit-rt.jar:na]
	at com.intellij.rt.junit.JUnitStarter.main(JUnitStarter.java:54) ~[junit-rt.jar:na]
Caused by: java.lang.IllegalArgumentException: Invalid value type for attribute 'factoryBeanObjectType': java.lang.String
	at org.springframework.beans.factory.support.FactoryBeanRegistrySupport.getTypeForFactoryBeanFromAttributes(FactoryBeanRegistrySupport.java:86) ~[spring-beans-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.getTypeForFactoryBean(AbstractAutowireCapableBeanFactory.java:838) ~[spring-beans-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.beans.factory.support.AbstractBeanFactory.isTypeMatch(AbstractBeanFactory.java:620) ~[spring-beans-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.doGetBeanNamesForType(DefaultListableBeanFactory.java:573) ~[spring-beans-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.getBeanNamesForType(DefaultListableBeanFactory.java:532) ~[spring-beans-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.context.support.PostProcessorRegistrationDelegate.invokeBeanFactoryPostProcessors(PostProcessorRegistrationDelegate.java:138) ~[spring-context-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.context.support.AbstractApplicationContext.invokeBeanFactoryPostProcessors(AbstractApplicationContext.java:775) ~[spring-context-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:597) ~[spring-context-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:748) ~[spring-boot-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:450) ~[spring-boot-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:322) ~[spring-boot-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.boot.test.context.SpringBootContextLoader.lambda$loadContext$3(SpringBootContextLoader.java:137) ~[spring-boot-test-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.util.function.ThrowingSupplier.get(ThrowingSupplier.java:58) ~[spring-core-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.util.function.ThrowingSupplier.get(ThrowingSupplier.java:46) ~[spring-core-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.boot.SpringApplication.withHook(SpringApplication.java:1436) ~[spring-boot-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.boot.test.context.SpringBootContextLoader$ContextLoaderHook.run(SpringBootContextLoader.java:544) ~[spring-boot-test-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.boot.test.context.SpringBootContextLoader.loadContext(SpringBootContextLoader.java:137) ~[spring-boot-test-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.boot.test.context.SpringBootContextLoader.loadContext(SpringBootContextLoader.java:108) ~[spring-boot-test-3.2.0-20231027.174801-479.jar:3.2.0-SNAPSHOT]
	at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContextInternal(DefaultCacheAwareContextLoaderDelegate.java:225) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContext(DefaultCacheAwareContextLoaderDelegate.java:152) ~[spring-test-6.1.0-20231028.145402-786.jar:6.1.0-SNAPSHOT]
	... 72 common frames omitted


java.lang.IllegalStateException: Failed to load ApplicationContext for [WebMergedContextConfiguration@28cb3a25 testClass = com.joe.coderconnect.service.impl.UserServiceImplTest, locations = [], classes = [com.joe.coderconnect.CoderconnectApplication], contextInitializerClasses = [], activeProfiles = [], propertySourceDescriptors = [], propertySourceProperties = ["org.springframework.boot.test.context.SpringBootTestContextBootstrapper=true"], contextCustomizers = [org.springframework.boot.test.context.filter.ExcludeFilterContextCustomizer@6e6f2380, org.springframework.boot.test.json.DuplicateJsonObjectContextCustomizerFactory$DuplicateJsonObjectContextCustomizer@1530c739, org.springframework.boot.test.mock.mockito.MockitoContextCustomizer@0, org.springframework.boot.test.web.client.TestRestTemplateContextCustomizer@7ef82753, org.springframework.boot.test.autoconfigure.actuate.observability.ObservabilityContextCustomizerFactory$DisableObservabilityContextCustomizer@1f, org.springframework.boot.test.autoconfigure.properties.PropertyMappingContextCustomizer@0, org.springframework.boot.test.autoconfigure.web.servlet.WebDriverContextCustomizer@18271936, org.springframework.boot.test.context.SpringBootTestAnnotation@9d9c1285], resourceBasePath = "src/main/webapp", contextLoader = org.springframework.boot.test.context.SpringBootContextLoader, parent = null]

	at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContext(DefaultCacheAwareContextLoaderDelegate.java:180)
	at org.springframework.test.context.support.DefaultTestContext.getApplicationContext(DefaultTestContext.java:130)
	at org.springframework.test.context.web.ServletTestExecutionListener.setUpRequestContextIfNecessary(ServletTestExecutionListener.java:191)
	at org.springframework.test.context.web.ServletTestExecutionListener.prepareTestInstance(ServletTestExecutionListener.java:130)
	at org.springframework.test.context.TestContextManager.prepareTestInstance(TestContextManager.java:247)
	at org.springframework.test.context.junit.jupiter.SpringExtension.postProcessTestInstance(SpringExtension.java:163)
	at java.base/java.util.stream.ReferencePipeline$3$1.accept(ReferencePipeline.java:197)
	at java.base/java.util.stream.ReferencePipeline$2$1.accept(ReferencePipeline.java:179)
	at java.base/java.util.ArrayList$ArrayListSpliterator.forEachRemaining(ArrayList.java:1625)
	at java.base/java.util.stream.AbstractPipeline.copyInto(AbstractPipeline.java:509)
	at java.base/java.util.stream.AbstractPipeline.wrapAndCopyInto(AbstractPipeline.java:499)
	at java.base/java.util.stream.StreamSpliterators$WrappingSpliterator.forEachRemaining(StreamSpliterators.java:310)
	at java.base/java.util.stream.Streams$ConcatSpliterator.forEachRemaining(Streams.java:735)
	at java.base/java.util.stream.Streams$ConcatSpliterator.forEachRemaining(Streams.java:734)
	at java.base/java.util.stream.ReferencePipeline$Head.forEach(ReferencePipeline.java:762)
	at java.base/java.util.Optional.orElseGet(Optional.java:364)
	at java.base/java.util.ArrayList.forEach(ArrayList.java:1511)
	at java.base/java.util.ArrayList.forEach(ArrayList.java:1511)
Caused by: java.lang.IllegalArgumentException: Invalid value type for attribute 'factoryBeanObjectType': java.lang.String
	at org.springframework.beans.factory.support.FactoryBeanRegistrySupport.getTypeForFactoryBeanFromAttributes(FactoryBeanRegistrySupport.java:86)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.getTypeForFactoryBean(AbstractAutowireCapableBeanFactory.java:838)
	at org.springframework.beans.factory.support.AbstractBeanFactory.isTypeMatch(AbstractBeanFactory.java:620)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.doGetBeanNamesForType(DefaultListableBeanFactory.java:573)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.getBeanNamesForType(DefaultListableBeanFactory.java:532)
	at org.springframework.context.support.PostProcessorRegistrationDelegate.invokeBeanFactoryPostProcessors(PostProcessorRegistrationDelegate.java:138)
	at org.springframework.context.support.AbstractApplicationContext.invokeBeanFactoryPostProcessors(AbstractApplicationContext.java:775)
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:597)
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:748)
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:450)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:322)
	at org.springframework.boot.test.context.SpringBootContextLoader.lambda$loadContext$3(SpringBootContextLoader.java:137)
	at org.springframework.util.function.ThrowingSupplier.get(ThrowingSupplier.java:58)
	at org.springframework.util.function.ThrowingSupplier.get(ThrowingSupplier.java:46)
	at org.springframework.boot.SpringApplication.withHook(SpringApplication.java:1436)
	at org.springframework.boot.test.context.SpringBootContextLoader$ContextLoaderHook.run(SpringBootContextLoader.java:544)
	at org.springframework.boot.test.context.SpringBootContextLoader.loadContext(SpringBootContextLoader.java:137)
	at org.springframework.boot.test.context.SpringBootContextLoader.loadContext(SpringBootContextLoader.java:108)
	at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContextInternal(DefaultCacheAwareContextLoaderDelegate.java:225)
	at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContext(DefaultCacheAwareContextLoaderDelegate.java:152)
	... 17 more


Process finished with exit code -1

```
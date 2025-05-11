# Configuration must environment specific

Configuration must be environment specific – that’s just a fact of life. If that weren’t the case, then it wouldn’t be configuration and we would just hardcode values in code.

**For a Spring application there are several solutions you can use** – from simple solutions all the way to uber-flexible, highly complex alternatives.

One of more common and straightforward solutions is a flexible use of **properties files** and the [first class property support provided by Spring](https://www.baeldung.com/properties-with-spring "Using properties files").

As a proof of concept, for the purposes of this article, we’ll take a look at one specific type of property – the database configuration. It makes perfect sense to use one type of database configuration for production, another for testing and yet another for a dev environment.

# The properties Files For each Environment

Let’s start our Proof of Concept – by defining the environments we want to target:

-  Dev
- Staging
- Production

Next – let’s create 3 properties files – one for each of these environments:

- _persistence-dev.properties_
- _persistence-staging.properties_
- _persistence-production.properties_

In a typical Maven application, these can reside in _src/main/resources_, but the wherever they are, they will need to be **available on the classpath** when the application is deployed.

An important sidenote – **having all properties files under version control makes configuration much more transparent** and reproducible. This is in opposition to having the configs on disk somewhere and simply pointing Spring to them.

# The spring configuration

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xmlns:context="http://www.springframework.org/schema/context"
   xsi:schemaLocation="http://www.springframework.org/schema/beans
      http://www.springframework.org/schema/beans/spring-beans-4.0.xsd
      http://www.springframework.org/schema/context
      http://www.springframework.org/schema/context/spring-context-4.0.xsd">

      <context:property-placeholder
         location="
         classpath*:*persistence-${envTarget}.properties" />

</beans>
```

The same can of course be done with Java Configuration as well :

```java
@PropertySource({ "classpath:persistence-${envTarget:dev}.properties" })
```

his approach allows for the flexibility of having multiple _*.properties_ files for **specific, focused purposes**. For example – in our case, the persistence Spring config imports the persistence properties – which makes perfect sense. The security config would import security related properties and so on.

# Setting the Property in each Environment

The final, deployable war **will contain all properties files** – for persistence, the three variants of _persistence-*.properties_. Since the files are actually named differently, there is no fear of accidentally including the wrong one. We will set **the _envTarget_ variable** and thus select the instance we want from the multiple existing variants.

The _envTarget_ variable can be set in the OS/environment or as a parameter to the JVM command line:

`-DenvTarget=dev`

# Testing on Maven

For integration tests that need persistence enabled – we’ll simply set the _envTarget_ property in the pom.xml:

```xml
<plugin>
   <groupId>org.apache.maven.plugins</groupId>
   <artifactId>maven-surefire-plugin</artifactId>
   <configuration>
      <systemPropertyVariables>
         <envTarget>h2_test</envTarget>
      </systemPropertyVariables>
   </configuration>
</plugin>
```

The corresponding _persistence-h2_test.properties_ file can be placed in _src/test/resources_ so that it will **only be used for testing** and not unnecessarily included and deployed with the war at runtime.

# Going Further

here are several ways to build additional flexibility into this solution if needed.

One such way is to use a **more complex encoding for the names** of the properties files, specifying not just the environment in which they are to be used, but also more information (such as the persistence provider). For example, we might use the following types of properties: _persistence-h2.properties_, _persistence-mysql.properties_ or, even more specific: _persistence-dev_h2.properties_, _persistence-staging_mysql.properties_, _persistence-production_amazonRDS.properties_.

The advantage of such a naming convention – and it is **just a convention** as nothing changes in the overall approach – is simply transparency. It now becomes much clearer what the configuration does only by looking at the names:

- **_persistence-dev_h2.properties_**: the persistence provider for the _dev_ environment is a lightweight, in-memory H2 database
- **_persistence-staging_mysql.properties_**: the persistence provider for the _staging_ environment is a MySQL instance
- **_persistence-production_amazon_rds.propertie_**: the persistence provider for the _production_ environment is Amazon RDS



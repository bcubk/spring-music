Spring Music
============

This is a sample application for using [Spring Framework](http://spring.io) and [Spring Boot](http://projects.spring.io/spring-boot/).

This application has been built to store the same domain objects in one of a variety of different persistence technologies - relational, document, and key-value stores. This is not meant to represent a realistic use case for these technologies, since you would typically choose the one most applicable to the type of data you need to store.

The application uses Spring Java configuration and [bean profiles](http://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-profiles.html) to configure the application and the connection objects needed to use the persistence stores. 

## Building

This project requires a Java version between 8 and 17 to compile.

To build a runnable Spring Boot jar file, run the following command:

~~~
$ ./gradlew clean assemble
~~~

## Running the application locally

One Spring bean profile should be activated to choose the database provider that the application should use. The profile is selected by setting the system property `spring.profiles.active` when starting the app.

The application can be started locally using the following command:

~~~
$ java -jar -Dspring.profiles.active=<profile> build/libs/spring-music.jar
~~~

where `<profile>` is one of the following values:

* `mysql`
* `postgres`
* `mongodb`
* `redis`

If no profile is provided, an in-memory relational database will be used. If any other profile is provided, the appropriate database server must be started separately. Spring Boot will auto-configure a connection to the database using it's auto-configuration defaults. The connection parameters can be configured by setting the appropriate [Spring Boot properties](http://docs.spring.io/spring-boot/docs/current/reference/html/common-application-properties.html).

If more than one of these profiles is provided, the application will throw an exception and fail to start.

## Alternate Java versions

By default, the application will be built and deployed using Java 8 compatibility.
If you want to use a more recent version of Java, you will need to update two things.

In `build.gradle`, change the `targetCompatibility` Java version:

~~~
java {
  ...
  targetCompatibility = JavaVersion.VERSION_1_8
}
~~~

Set `targetCompatibility` to `JavaVersion.VERSION_11` for Java 11 or `JavaVersion.VERSION_17` for Java 17.

## Exercise 

You can find the description to the exercise [here](docs/exercise.md)

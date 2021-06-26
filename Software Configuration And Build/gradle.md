# Gradle
+ Gradle is a build automation tool
+ Building a project actually refers to 
    + compiling source code
    + running both unit and integration tests
    + packaging the compiled source code into jars, wars or even docker images
    + We then deploy these artifacts onto servers or even a cloud environment 
    + and several other tasks can be automated using gradle

+ Before gradle we have other build tools like Maven, Ant etc
+ Gradle gives us everything that is good in Maven, Ant like
    + Supports convention over configuration(like maven)
    + Also allows to customize(like Ant)
        + If we don't have any tasks that are required for our project, then we can customize and create own tasks in a very simple manner using DSL
+ Gradle uses programming languages or scripting languages like groovy or kotlin inside `build.gradle` file
+ We donot need to use XML instead use groovy or kotlin using  which it is  very easy to write a domain specific build file. That is why it is called gradle DSL
+ Gradle has become standard build management tool for android and also it is used by several open source projects like spring, hibernate and various other companies and enterprises
+ Advantages of Gradele:
    + Gradle is used not only by java projects but by other programming languages like Groovy, C++, Kotlin, Swift and more
    + Gradle will manage the dependencies that we use in our project by using the repositories that we configure this can be Maven repository(Central or Local), Jcenter, FileSystem on local machine or on server
    + Gradle will pull all the dependencies from these remote repositories and it will cache them locally and use them for the next builds
    + Gradle offers a way to customize the way the dependencies are pulled
    + In Maven, the only thing we can customize is the version of the dependency But in Gradle we can define custom rules based on which the dependencies can be pulled
    + Gradle also allows custom dependency scopes, unlike Maven which has fixed scopes like test, compile etc. In case of Gradle we can use custom scopes easily
    + When it comes to build gradle is super fast. It keeps track of all the tasks that were aleady run for a particular build and it only processes those files that have changed recently
        + For example. we have 10 Java files and after build we have changed only two of those files, And we run build, Gradle will comile only those two java files and will use the output of the other eight files from the previous build
        + This is called as build cache
    + check in video (todo)
    + We can install plugins depending on the type of project we are working and on the tasks we want in the project
        + we can use plugin like jar, war, jacoco, spring boot 
    + For writing build.gradle file we can use either groovy or kotlin


```
dependencies{
     providedCompile 'javax.servlet:javax.servlet-api:3.1.0'
     testCompile group: 'junit', name: 'junit', version: '4.4'
}
```




## Ant
build.xml
Tasks
Customize
Ivy
+ Pros
    + 
+ Cons
    + It does not have inbuilt dependency management. So we have to use third party tools like Ivy to make libraries or dependencies that are required
    + Ant uses lot of XML based tasks

## Maven
Use convention over configuration(eg: intead of you worrying about folder structure of your project and all that, you follow the project structure we ask you to do. For example put all the source code under src/main/java and put test code under src/main/test and src/main/resources and src/test/resources for some other files storage. After that execute  maven jar and i will do the build )
+ pros
    + Inbuild dependency management and along with that it uses XML to a minimum
+ cons
    + Customization for projects(especially for large projects) is little harder and this is where gradle comes in
 
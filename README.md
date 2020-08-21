## 编译过程

1. 执行构建命令
> ./gradlew assemble

会碰到错误：
JAVA_HOME must be set to build Elasticsearch

先找到`BuildPlugin.groovy`文件
> find ./ -name BuildPlugin.groovy

然后将System.getenv('JAVA_HOME')写死成"/Library/Java/JavaVirtualMachines/jdk1.8.0_231.jdk/Contents/Home"

在 build.gradle 文件的最后，加上

buildscript {
    repositories {
        maven{ url 'http://maven.aliyun.com/nexus/content/groups/public/'}
    }
}

allprojects {
    repositories {
        maven{ url 'http://maven.aliyun.com/nexus/content/groups/public/'}
    }
}

2. 导入idea，会碰到错误
You must run gradle idea from the root of elasticsearch before importing into IntelliJ

> ./gradlew idea







-------------------------
## 调试过程
参考：https://blog.csdn.net/wwwdc1012/article/details/81978966

我使用远程调试的方式
> ./gradlew run --debug-jvm

新建一个remote，并启动，这个时候才会把项目启动起来

然后输入网址localhost:9200即可。
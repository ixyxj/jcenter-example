# jcenter-example
发布自己的开源库到jcenter

### 版本

| plugin name                 | plugin version |
| --------------------------- | -------------- |
| gradle-bintray-plugin       | 1.8.0          |
| android-maven-gradle-plugin | 2.1            |

### 引用

```
apply from: 'https://raw.githubusercontent.com/ixyxj/jcenter-example/master/v1/publish.gradle'
```



### 配置

分别在project和module下添加config.gradle, pubblish.gradle

1. root project下build.gradle下添加

```
apply from: "config.gradle"
buildscript {
    
    repositories {
        google()
        jcenter()
        mavenCentral()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.2.1'
        classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.8.0'
        classpath 'com.github.dcendents:android-maven-gradle-plugin:2.1'

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}

allprojects {
    repositories {
        google()
        jcenter()
        mavenCentral()
    }
}
```

注意：2.1版本需要添加mavenCentral下载。之前都下载失败了，然后到github找到：[android-maven-gradle-plugin](https://github.com/dcendents/android-maven-gradle-plugin), 在releases版本中看到Plugin Name，一定要对应

2. 在lib文件夹下build.gradle添加, 并将其android{}配置删除

```
apply from: 'publish.gradle'
```



3. 上传插件：[gradle-bintray-plugin](https://github.com/bintray/gradle-bintray-plugin)， 我发现这个项目中的gradle 3.0 example中配置是android-maven 1.1之前的版本插件名， 里面有publish方法，但install方法找不到。




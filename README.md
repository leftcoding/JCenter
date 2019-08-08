### JCenter

> 把 module 库 ，发布到 Jcenter 上

### 使用方法

##### 1. 在根目录新建 `config.gradle`文件，添加内容

```groovy
ext {
    plugins = [
            maven      : 'com.github.dcendents.android-maven',
            bintray    : 'com.jfrog.bintray'
    ]

    bintray = [
            version       : "1.0.1", // 指定库的版本号
            group         : "android.left.permission", // 库的group名，确定好之后不能修改

            siteUrl       : 'https://github.com/leftcoding/LiPermission', // 项目开源地址
            gitUrl        : 'https://github.com/leftcoding/LiPermission.git', // 项目git地址

            packaging     : 'aar',
            name          : 'annotation', // 项目名，随意
            description   : '动态权限注解', // 项目描述，随意

            licenseName   : 'The Apache Software License, Version 2.0', // 开源协议
            licenseUrl    : 'http://www.apache.org/licenses/LICENSE-2.0.txt', // 开源协议地址

            developerId   : 'left', // 开发者id
            developerName : 'lingyan', // 开发者姓名
            developerEmail: '137387869@qq.com', // 开发者邮箱

            binrayLibrary : "permission-annotation", // 项目在bintray上的名称
            bintrayRepo   : "permission", // 发布到自己在bintray的哪个仓库中，一般默认maven
            bintrayUser   : 'left', // bintray的用户名
            bintrayLicense: "Apache-2.0" // 指定bintray上的开源协议
    ]
}
```

##### 2. 在根目录`build.gradle` 文件中，添加内容

```groovy
apply from: "config.gradle"
```

##### 3. 在根目录`local.properties`文件中，添加内容

```groovy
bintray.user=你的用户ID
bintray.apikey=你的用户apikey
```

##### 4. 在`module`目录中，`build.gradle` 文件尾部，添加内容

```groovy
apply from: 'https://raw.githubusercontent.com/leftcoding/JCenter/master/maven.gradle'
```

### 发布

先清除编译

```java
./gradlew clean install
```

发布项目

```java
./gradlew bintrayUpload
```

最后到 [bintray](https://bintray.com/) , 同步到 JCenter


---
layout: post
title:  "How to upload in maven central and jcenter(Gradle)"
categories: OpenSource
---

오픈소스([FishBun](https://github.com/sangcomz/FishBun))를 시작하기로 마음먹고 라이브러리를 올리면서 정리한 내용입니다.


* ## [bintray](https://bintray.com/)에 회원가입을 합니다. 그리고 아이디와 apikey를 얻습니다.
* ## Project Gradle 수정


```java
dependencies {
  classpath 'com.android.tools.build:gradle:1.3.0'
  classpath 'com.github.dcendents:android-maven-gradle-plugin:1.3'
  classpath "com.jfrog.bintray.gradle:gradle-bintray-plugin:1.4"
}
```
* ## App Gradle 수정

```java
apply plugin: 'com.android.library'
apply plugin: 'com.github.dcendents.android-maven'
apply plugin: "com.jfrog.bintray"

version = "0.0.2"

android {
    compileSdkVersion 23
    buildToolsVersion "23.0.2"
    defaultConfig {
        minSdkVersion 15
        targetSdkVersion 23
        versionCode 1
        versionName '0.1'


    }
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }


    productFlavors {
    }
}

dependencies {
    compile fileTree(include: ['*.jar'], dir: 'libs')
    compile 'com.android.support:appcompat-v7:23.1.0'
    compile 'com.android.support:design:23.1.0'
    compile 'com.android.support:recyclerview-v7:23.1.0'
    compile 'com.github.bumptech.glide:glide:3.6.0'
}

def siteUrl = 'https://github.com/sangcomz/FishBun'      // Homepage URL of the library
def gitUrl = 'https://github.com/sangcomz/FishBun.git'   // Git repository URL
group = "com.sangcomz"                      // Maven Group ID for the artifact


install {
    repositories.mavenInstaller {
        // This generates POM.xml with proper parameters
        pom {
            project {
                packaging 'aar'

                // Add your description here
                name 'fishbun'
                description = 'The project aims to provide a album.'
                url siteUrl

                // Set your license
                licenses {
                    license {
                        name 'The Apache Software License, Version 2.0'
                        url 'http://www.apache.org/licenses/LICENSE-2.0.txt'
                    }
                }
                developers {
                    developer {
                        id 'sangcomz'
                        name 'Jeong Seok Won'
                        email 'sangcomz@naver.com'
                    }
                }
                scm {
                    connection gitUrl
                    developerConnection gitUrl
                    url siteUrl

                }
            }
        }
    }
}

task sourcesJar(type: Jar) {
    from android.sourceSets.main.java.srcDirs
    classifier = 'sources'
}

afterEvaluate {
    javadoc.classpath += project.android.libraryVariants.toList().first().javaCompile.classpath
}

task javadoc(type: Javadoc) {
    source = android.sourceSets.main.java.srcDirs
    classpath += project.files(android.getBootClasspath().join(File.pathSeparator))
}


task javadocJar(type: Jar, dependsOn: javadoc) {
    classifier = 'javadoc'
    from javadoc.destinationDir

}
artifacts {
    archives javadocJar
    archives sourcesJar
}



Properties properties = new Properties()
properties.load(project.rootProject.file('local.properties').newDataInputStream())

// https://github.com/bintray/gradle-bintray-plugin
bintray {
    user = properties.getProperty("bintray.user")
    key = properties.getProperty("bintray.apikey")
    publish = true
    configurations = ['archives']
    pkg {
        repo = "maven"
        // it is the name that appears in bintray when logged
        name = "fishbun"
        websiteUrl = siteUrl
        vcsUrl = gitUrl
        licenses = ["Apache-2.0"]
        publish = true
    }
}
```

* ## local.properties 작성

```java
bintray.user=your user id
bintray.apikey=your api key
```

### 안드로이드 프로젝트의 설정은 끝났습니다.

* ## upload 하기


```bash
//windows
gradlew bintrayUpload

//mac
./gradlew bintrayUpload
```

### 성공했다면 https://bintray.com/ 에 접속하시면 maven repository에 패키지가 추가된것을 확인할 수 있습니다.
###  그 후에 jcenter로 업데이트를 요청하시면 끝납니다. 나중에 승인이 오면 찾아서 사용하실 수 있습니다.

-참고 사이트-
* [Publishing Gradle Android library to jCenter repository](https://www.virag.si/2015/01/publishing-gradle-android-library-to-jcenter/)
* [gradle-jcenter-publish](https://github.com/danielemaddaluno/gradle-jcenter-publish)
* [zerobrain님 블로그](http://zerobrain.tistory.com/53)

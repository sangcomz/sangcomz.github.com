---
layout: post
title:  "Unit Test에서 Json File 사용하기"
categories: Test
---

## 발생 원인

Unit Test를 할 때 json 파일을 parsing해서 그 data와 함께 테스트를 하고 싶었다.  
실제 json data를 사용해서 테스트를 해보고 싶었다.  
결론적으론 굳이 실제 json data를 써야할 필요성을 느끼지 못했다.  
실제 json data는 나의 통제를 벗어나 내가 디테일하게 테스트 하고 싶어도,   
그 많은 json data를 내가 알지를 못해서 일반적인 테스트밖에 할 수 없는것같다    
실제 많은 다양한 상황들을 테스트 해보고 싶으면,   
테스트 해보고 싶은 json data를 내가 임의로 만들어서 테스트 해보는게 맞는것같다.    
하지만 실제 data를 결론적으론 사용해서 아주 넓은 의미의 테스트를 했다.(유의미한 결과는 없었지만...)    

## 해결 방법

_unitTests.returnDefaultValues_ 설정해줘야한다. 이유는..   
>If the exceptions thrown by Android APIs in the android.jar are problematic for your tests, you can change the behavior so that methods instead return either null or zero by adding the following configuration in your project's top-level build.gradle file:

```
android {
    testOptions {
        unitTests.returnDefaultValues = true
    }
}
```

### 방법 1 (선택한 방법)

json 객체로 직접 만들지 않고 바뀐 객체로 만들어준다.    
GpxModel data형이 있으면 json파일을 읽어서 string으로 만들어주고 이후에 string을 gson을 통해서 GpxModel으로 변형.   
나는 ArrayList가 필요해서  Type을 Array로 지정했다.  


```java
    private ArrayList<GpxModel> readJsonToGpxModel(String fileName) {

        InputStream inputStream = getClass().getResourceAsStream(fileName);

        BufferedReader br = new BufferedReader(new InputStreamReader(inputStream));

        StringBuilder sb = new StringBuilder();

        int bufferSize = 1024 * 1024;

        char readBuf[] = new char[bufferSize];
        int resultSize = 0;

        try {
            while ((resultSize = br.read(readBuf)) != -1) {
                if (resultSize == bufferSize) {
                    sb.append(readBuf);
                } else {
                    for (int i = 0; i < resultSize; i++) {
                        sb.append(readBuf[i]);
                    }
                }
            }
        } catch (IOException e) {
            e.printStackTrace();
        }

        Type listType = new TypeToken<ArrayList<GpxModel>>() {
        }.getType();

        return new Gson().fromJson(sb.toString(), listType);
    }
```



### 방법 2

[JSON is bundled up with the Android SDK, so you'll just be hitting a stub. You can pull in a JSON jar, which will provide real objects to use. - StackOverFlow](json http://stackoverflow.com/questions/29402155/android-unit-test-not-mocked)

```
dependencies{
    testCompile 'org.json:json:20140107'
    testCompile files('libs/json.jar')
}
```
함께 컴파일 한 뒤에 json객체를 생성하면 return 값이 null or zero가 아닌 json file에 담긴 값이 나온다.



틀린 부분 혹은 부족한 점은 알려주세요!!   
감사합니다!

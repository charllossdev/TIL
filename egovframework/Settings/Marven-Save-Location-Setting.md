
# EgovFrameWork Marven Location Setting

Marven Dependency Injection Location setting

  * Default : C:\Users\[USER_PC_NAME]\.m2\repository



# Set Marven Location Setting

  1. Set location
  2. Make [Setting.xml] - localRepository Setting
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>

    <settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                          http://maven.apache.org/xsd/settings-1.0.0.xsd">

      <localRepository>C:/eGovFrameDev-3.7.0-64bit/repository</localRepository>
    </settings>
    ```
  3. Eclipse Setting
    **Menu - Window - Preferences - Maven - User Settings**
    User Setting Location Fix [Setting.xml]
    ![maven-preference](assets/Marven-Save-Location-Setting-0d6fa5cf.png)
  4. Re Downloading New Marven Dependency
> 주의
> 상기 설정은 Workspace 별로 해줘야 한다.
>> 만약 설정하지 않으면 Default 경로에 저장되는 점'

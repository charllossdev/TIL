# 전자정부 프레임 워크 설정 에러 해결 건

# 2019-04-06
The Eclipse executable launcher was unable to locate its companion shared library." 오류

> eclipse.ini 파일의 설정이 잘못되어 있기 때문인데 메모장으로 eclipse.ini 파일을 열어서 수정을 합니다.

```ini
-startup
plugins/org.eclipse.equinox.launcher_1.1.1.R36x_v20101122_1400.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.win32.win32.x86_1.1.2.R36x_v20101222
-showsplash
org.eclipse.platform

--launcher.defaultAction
openFile
-vm
c:\Program files\java\jdk1.6.0_24\bin\javaw.exe

-vmargs
-Xms40m
-Xmx384m
-XX:MaxPermSize=512m
==============================================================
```

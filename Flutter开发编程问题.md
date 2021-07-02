## 运行指令flutter doctor提示 Flutter requires Android SDK 28 and the Android BuildTools 28.0.3
	解决方案：打开sdk manager 升级build tool

## flutter doctor 发现[!] Android toolchain - develop for Android devices (Android SDK version 28.0.3)✗ Android license status unknown. Some Android licenses not accepted
	解决方案:
	首先要使用jdk8环境,
	升级 Android Studio
	执行:flutter doctor --android-licenses

## 运行指令flutter doctor提示 X Android license status unknown.Try re-installing or updating your Android SDK Manager.
	解决方案：升级sdkmanager，命令行运行指令F:\sdk\tools\bin\sdkmanager --update

## 升级sdk manager 失败提示：Exceptioninthread“main”java.lang.NoClassDefFoundError: javax/xml/bind/annotation/XmlSchema
	解决方案：
	1.请检查自己的java环境变量；
	2.因为java jdk版本太高（10）或低，换成jdk 8 就行了；




---
title: 手順 3 - モバイルアプリに拡張機能を登録
description: このパートでは、ユーザープロファイル、ID、ライフサイクル、シグナルの各拡張機能を登録するコードを追加します。
feature: Push
user: Admin
level: Experienced
jira: KT-4827
doc-type: tutorial
activity: use
team: TM
exl-id: d8c0d8c6-2e04-4c27-b27a-d0de79dd953b
source-git-commit: 9be31e056800b806c49a2c5ffbf9f9f42b001d4c
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 14%

---

# 手順 3 - モバイルアプリに拡張機能を登録

このパートでは、ユーザープロファイル、ID、ライフサイクル、シグナル拡張機能を登録するコードを追加します。 また、次のコードに示すように、Adobe Campaign Standard拡張機能を登録する必要があります。

[!DNL Android] Studio でプロジェクトを開きます。 MainApp のコード全体 **パッケージステートメントの最初の行を除く** を削除します。

次のコードを MainApp に貼り付けます。

<!--
Removed `{.line-numbers}` below
-->

```java
import [!DNL android].app.Application;
import android.util.Log;

import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.Campaign;
import com.adobe.marketing.mobile.Identity;
import com.adobe.marketing.mobile.InvalidInitException;
import com.adobe.marketing.mobile.Lifecycle;
import com.adobe.marketing.mobile.LoggingMode;
import com.adobe.marketing.mobile.MobileCore;
import com.adobe.marketing.mobile.Signal;
import com.adobe.marketing.mobile.UserProfile;

public class MainApp extends Application {

@Override
public void onCreate() {
super.onCreate();

MobileCore.setApplication(this);
MobileCore.setLogLevel(LoggingMode.DEBUG);

try{
    Campaign.registerExtension();
    UserProfile.registerExtension();
    Identity.registerExtension();
    Lifecycle.registerExtension();
    Signal.registerExtension();
    MobileCore.start(new AdobeCallback () {
        @Override
        public void call(Object o) {
            MobileCore.configureWithAppID("copy your launch property id here");
        }
    });
} catch (InvalidInitException e) {
    Log.d("ACS Exception", "exception");
}
}
}
```

32 行目では、[!UICONTROL  Launch] プロパティの環境ファイル ID を指定する必要があります。 これは、[!UICONTROL Launch] プロパティの [!UICONTROL environment tab] からアクセスできます。

![launch-id](assets/launch-id-property.PNG)

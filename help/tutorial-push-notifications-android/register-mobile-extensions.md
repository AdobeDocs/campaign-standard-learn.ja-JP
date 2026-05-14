---
title: 手順 3 - モバイルアプリに拡張機能を登録
description: この部分では、UserProfile、ID、ライフサイクル、Signal拡張機能を登録するコードを追加します。
feature: Push
user: Admin
level: Experienced
jira: KT-4827
doc-type: tutorial
activity: use
team: TM
exl-id: d8c0d8c6-2e04-4c27-b27a-d0de79dd953b
TQID: https://experienceleague.adobe.com/WjKV0qe9zi7cV37Wn54BJdI91n92i302t4k-yMIenZ4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 7d15c0a5dc01907ff529b3684eaddaca5321facc
workflow-type: tm+mt
source-wordcount: 111
ht-degree: 14%

---

# 手順 3 - モバイルアプリに拡張機能を登録

この部分では、ユーザープロファイル、ID、ライフサイクル、およびSignal拡張機能を登録するコードを追加します。 また、以下のコードに示すように、Adobe Campaign Standard拡張機能を登録する必要があります。

[!DNL Android] Studioでプロジェクトを開きます。 パッケージ文&#x200B;**の最初の行を除き、MainApp**&#x200B;のコード全体を削除します。

次のコードをMainAppにペーストします

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

32行目[!UICONTROL &#x200B; Launch] プロパティの環境ファイル IDを指定する必要があります。 これは、[!UICONTROL Launch] プロパティの[!UICONTROL environment tab]からアクセスできます。

![launch-id](assets/launch-id-property.PNG)

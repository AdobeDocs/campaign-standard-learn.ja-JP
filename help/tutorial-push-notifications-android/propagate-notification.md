---
title: 手順 5 - 通知の伝達
description: このパートでは、Android Notification Manager.Firebaseを使用してAdobe Campaignから受信したメッセージを反映します
feature: Push
jira: KT-4829
user: Admin
level: Experienced
doc-type: tutorial
activity: use
team: TM
exl-id: b0e01224-4ddc-4999-b8c6-794e49245428
TQID: https://experienceleague.adobe.com/xNsJ0Cj8CUpvHfR66lTnZZEp-shWD0OC14ctHHFu4IY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 7d15c0a5dc01907ff529b3684eaddaca5321facc
workflow-type: tm+mt
source-wordcount: 155
ht-degree: 2%

---

# 通知を送信するサービスを追加

このパートでは、[!DNL Android Notification Manager]を使用してAdobe Campaignから受信したメッセージを反映します。 [!DNL Notification manager]は、発生したイベントをユーザーに通知するために使用されます。
これは、バックグラウンドで何かが起こったことをユーザーに伝える方法です。

* [!DNL Android Studio]を起動
* *[!DNL ACSPushTutorial]* プロジェクトを開く
* プロジェクト構造の拡張
* パッケージフォルダー（[!DNL com.example.acspushtutorial]）と[!DNL New ->Java Class]を右クリックします
* このクラスに&#x200B;*[!DNL MyService]*&#x200B;という名前を付け、このクラスに[!DNL FirebaseMessagingService]が含まれていることを確認します
* このクラスに&#x200B;*[!DNL sendNotification]* メソッドを作成します。 この方法では、[!DNL NotificationCompat.Builder] オブジェクトを使用して、通知のコンテンツとチャネルを設定する必要があります。 通知を表示するには、[!DNL NotificationManagerCompat.notify()]を呼び出して、通知の一意のIDと[!DNL NotificationCompat.Builder.build()]の結果を渡します。

<!--
Removed `{.line-numbers}` below
-->

```java
package com.example.pushmessaging;
import android.app.NotificationChannel;
import android.app.NotificationManager;
import android.app.PendingIntent;
import android.content.Context;
import android.content.Intent;
import android.media.RingtoneManager;
import android.net.Uri;
import android.os.Build;
import android.util.Log;

import androidx.core.app.NotificationCompat;

import com.google.firebase.messaging.FirebaseMessagingService;
import com.google.firebase.messaging.RemoteMessage;

import java.util.Map;

public class MyService extends FirebaseMessagingService {
@Override
public void onMessageReceived(RemoteMessage remoteMessage)
{
Map<String,String> data  = remoteMessage.getData();
Log.d("data payload: ", data.toString());
sendNotification(remoteMessage);
}


private void sendNotification(RemoteMessage message) {
Intent intent = new Intent(this, MainActivity.class);
intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
PendingIntent pendingIntent = PendingIntent.getActivity(this, 0 /* Request code */, intent, PendingIntent.FLAG_ONE_SHOT);

String channelId = "0";
Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
NotificationCompat.Builder notificationBuilder =
        new NotificationCompat.Builder(this, channelId)
                .setSmallIcon(R.drawable.ic_launcher_background)
                .setContentTitle("Message from AEM")
                .setContentText(message.getData().get("body"))
                .setAutoCancel(true)
                .setSound(defaultSoundUri)
                .setContentIntent(pendingIntent);

NotificationManager notificationManager =
        (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);

// Since android Oreo notification channel is needed.
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
    NotificationChannel channel = new NotificationChannel(channelId,
            "Channel human readable title",
            NotificationManager.IMPORTANCE_DEFAULT);
    notificationManager.createNotificationChannel(channel);
}

notificationManager.notify(0 /* ID of notification */, notificationBuilder.build());
}
}
```

## [!DNL AndroidManifest.xml]を変更

作成したサービスを[!DNL AndroidManifest.xml]に追加します。 最終的な[!DNL AndroidManifest.xml]は次のようになります。

<!--
Removed `{.line-numbers}` below
-->

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.pushmessaging">

    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

    <application
        android:name=".MainApp"
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <service
            android:name=".MyService"
            android:exported="false">
            <intent-filter>
                <action android:name="com.google.firebase.MESSAGING_EVENT" />
            </intent-filter>
        </service>

        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

## アプリの実行

ツールバーまたは[!DNL Run] メニューの&#x200B;**緑の矢印**&#x200B;をクリックして、アプリを実行します。

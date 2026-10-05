---
title: 手順 2 - Mobile SDK の統合
description: このパートでは、Android アプリとMobile SDKを統合します。 モバイルSDKとAndroid アプリを統合するには
feature: Push
user: Admin
level: Experienced
jira: KT-4826
doc-type: tutorial
activity: use
team: TM
recommendations: noDisplay
exl-id: 0fa53536-8330-4e96-be2f-afc078609bcd
TQID: 'https://experienceleague.adobe.com/6WL8yj7aMoS9C6l-HwQZZ3Hg0B2jmNtlmaFnsAi0Ohw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: f5407121-8933-4ac3-8e06-a9b692a4e88a
    internal-label: Campaign Standard
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: a4657621-810c-498b-8a27-7ced9c176dda
    internal-label: Push notifications
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 508c3590ce956401ccfba3a256000cbc5849a684
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%
---
# 手順2 - [!UICONTROL Mobile SDK]とAndroid アプリの統合

このパートでは、[!DNL Android] アプリを[!UICONTROL Mobile SDK]と統合します。 [!UICONTROL mobile SDK]を[!DNL Android] アプリと統合するには、次の手順に従ってください。

* [!DNL Android Studio]で&#x200B;*ACSPushTutorial* プロジェクトを開く
* [!DNL android.app.Application]を拡張する&#x200B;*MainApp*&#x200B;という新しいJava クラスを作成します
* 現在のプロジェクト構造は次のようになります

![&#x200B; メインアプリ &#x200B;](assets/android-main-app.PNG)

* [!DNL Gradle Scripts] フォルダーを展開します。 モジュールの[!DNL build.gradle]をダブルクリックします。 次の依存関係を[!DNL build.gradle] ファイルの依存関係セクションにに貼り付けます。 [!DNL build.gradle] ファイルは次のようになります

<!--
Removed `{.line-numbers}` below
-->

```java
implementation 'com.adobe.marketing.mobile:campaign:1.+'
implementation 'com.adobe.marketing.mobile:userprofile:1.+'
implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
```

![module-gradle](assets/module-build-gradle.PNG)

* 「今すぐ同期」ボタンをクリックしてプロジェクトを同期し、[!DNL Android] プロジェクトを同期します

## [!DNL AndroidManifest.xml]を変更{#modify-android-manifest}

*AndroidManifest.xml*&#x200B;を開き、マニフェスト要素の後とアプリケーション要素の前に次の2行を貼り付けます。 これにより、アプリは外部の世界と通信できるようになります

<!--
Removed `{.line-numbers}` below
-->

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

アプリケーション要素に次の行をコピーします
[!DNL android:name=&quot;.MainApp&quot;]
を保存 [!DNL AndroidManifest.xml]
[!DNL AndroidManifest.xml]は次のようになります

<!--
Removed `{.line-numbers}` below
-->

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.acspushtutorial">
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

<activity android:name=".MainActivity">
<intent-filter>
    <action android:name="android.intent.action.MAIN" />
    <category android:name="android.intent.category.LAUNCHER" />
</intent-filter>
</activity>
</application>

</manifest>
```

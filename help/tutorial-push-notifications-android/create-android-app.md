---
title: 手順 1 - Android アプリの作成と Firebase Cloud Messaging を使用するための設定
description: ここでは、Adobe Campaign Standardから送信された [!UICONTROL Push notifications] を受信するアプリを作成  [!DNL Android]  作成します。 プッシュ通知を受け取るには、アプリをGoogle [!DNL Firebase Cloud Service] に登録する必要があります。
feature: Push
user: Admin
level: Experienced
jira: KT-4825
doc-type: tutorial
activity: use
team: TM
recommendations: noDisplay
exl-id: f087d9f2-cce9-4903-977f-3c5b47522c06
source-git-commit: 0ad82fb0533ed8fc2a85c2a32c7e54deef14d05a
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 手順 1 - アプリ [!DNL Android] 作成と [!DNL Firebase Cloud Messaging] を使用するための設定

ここでは、Adobe Campaign Standardから送信された [!UICONTROL Push notifications] ータ [!DNL Android] 受け取るアプリを作成します。 プッシュ通知を受け取るには、アプリをGoogle [!DNL Firebase Cloud Service] に登録する必要があります。

1. [!DNL Firebase] アカウントにログインします。

   [!DNL Firebase] は、高品質のアプリを迅速に開発するのに役立つGoogleのモバイルプラットフォームです。 [!DNL Firebase] アカウントをお持ちでない場合は、[ こちらから ](https://firebase.google.com) アカウントを作成してください。

2. Launch [!DNL Android Studio]
3. **[!UICONTROL File]**/**[!UICONTROL New]**/**[!UICONTROL New Project]をクリックします。**
4. 「**[!UICONTROL Empty Activity]**」を選択し、「**[!UICONTROL Next].**」をクリックします。

   ![android-project](assets/android-project.PNG)

5. プロジェクトにわかりやすい名前を付けます。

   このデモの目的のために、プロジェクトに *[!DNL ACSPushTutorial]* という名前を付けました

   ![android-project-configuration](assets/android-project-configuration.PNG)

6. デフォルトのパッケージ名をそのまま使用し、「**[!DNL Finish]**」をクリックしてプロジェクトを作成します。
7. プロジェクト構造は、以下のスクリーンショットのようになります

   ![android-project-structure](assets/android-project-structure.PNG)

8. **[!UICONTROL Tools]**/**[!UICONTROL Firebase]をクリックします。** （これによりプロジェクトが [!DNL Firebase] に追加されます）
9. 「**[!UICONTROL Set up Firebase Cloud Messaging].**」をクリックします。

   ![firebase のセットアップ ](assets/android-project-firebase-messaging.PNG)

10. 「**[!UICONTROL Connect to Firebase].**」をクリックします。
11. アプリが Firebase に接続されたら、「**[!UICONTROL Add FCM to your app].**」をクリックします。
12. 「**[!UICONTROL Accept Changes].**」をクリックします。

   アプリに FCM を追加する場合、ウィザードはプロジェクトに変更を加えるための権限を必要とします。

   ![[!DNL add-fcm-to-your-app]](assets/firebase-add-fcm-to-app.PNG)

アプリと Firebase が正常に統合されると、次のようなメッセージが表示されます。

![[!DNL fcm-successfull]](assets/android-firebase-success.PNG)

[ プロジェクトが  [!DNL Firebase ]console に表示されていることを確認します ](https://console.firebase.google.com/)。

## [!UICONTROL Push Channel] 設定

1. [!DNL Firebase] コンソールにログインします
2. **[!UICONTROL ACSPushTutorial]** プロジェクトを開きます。
3. **歯車アイコン** をクリックし、プロジェクト設定を開きます

   ![project-settings](assets/firebase-project-settings.PNG)

4. 「**[!UICONTROL Cloud Messaging]**」タブに移動します。
5. サーバーキーをコピー

   ![server-key](assets/firebase-server-key.PNG)

6. Adobe Campaign Standard インスタンスにログインします
7. **[!UICONTROL Adobe Campaign]**/**[!UICONTROL Administration]**/**[!UICONTROL Channels]**/**[!UICONTROL Mobile App].** をクリックします。
8. 適切な **[!UICONTROL Mobile Application Property].** を選択します。
9. 「**[!UICONTROL Push Channel settings]**」セクションの「**[!DNL Android]」アイコン** クリックします。
10. サーバーキーを「サーバーキー」フィールドに貼り付けます。

すべてが正常に動作すると、成功メッセージが表示されます。

![push-channel-settings](assets/push-channel-settings.PNG)

まとめると、[!DNL Android App] を作成し、[!DNL Android App] を [!DNL Firebase] に接続しました。 次に、Adobe Campaignのモバイルアプリに [!DNL Android App] ーサーキーを貼り付けて、Adobe Campaign Standardのモバイルアプリと [!DNL Android] を接続しました。

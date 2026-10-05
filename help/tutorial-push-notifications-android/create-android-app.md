---
title: 手順1 - Android アプリを作成し、Firebase Cloud Messagingを使用するように設定する
description: このパートでは、[!DNL Android] アプリを作成して、Adobe Campaign Standardから[!UICONTROL Push notifications]を受信します。 プッシュ通知を受け取るには、アプリをGoogleの[!DNL Firebase Cloud Service]に登録する必要があります。
feature: Push
user: Admin
level: Experienced
jira: KT-4825
doc-type: tutorial
activity: use
team: TM
recommendations: noDisplay
exl-id: f087d9f2-cce9-4903-977f-3c5b47522c06
TQID: 'https://experienceleague.adobe.com/-r-0ZHCJNt6bwarH4I-RzA46Ho9EJgDegCnN6VJVLgk'
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
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 508c3590ce956401ccfba3a256000cbc5849a684
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%
---
# 手順1 - [!DNL Android] アプリを作成し、[!DNL Firebase Cloud Messaging]を使用するように設定する

このパートでは、[!DNL Android] アプリを作成して、Adobe Campaign Standardから[!UICONTROL Push notifications]を受信します。 プッシュ通知を受け取るには、アプリをGoogleの[!DNL Firebase Cloud Service]に登録する必要があります。

1. [!DNL Firebase] アカウントにログインします。

   [!DNL Firebase]は、高品質なアプリをすばやく開発できるGoogleのモバイル プラットフォームです。 [!DNL Firebase] アカウントをお持ちでない場合は、ここから[&#x200B; アカウントを作成してください](https://firebase.google.com)。

2. [!DNL Android Studio]を起動
3. **[!UICONTROL File]** > **[!UICONTROL New]** > **[!UICONTROL New Project]をクリックします。**
4. **[!UICONTROL Empty Activity]**&#x200B;を選択し、**[!UICONTROL Next]をクリックします。**

   ![android-project](assets/android-project.PNG)

5. プロジェクトに意味のある名前を付けます。

   このデモでは、プロジェクトを&#x200B;*[!DNL ACSPushTutorial]*&#x200B;として指定しました

   ![android-project-configuration](assets/android-project-configuration.PNG)

6. 既定のパッケージ名を承認し、**[!DNL Finish]**&#x200B;をクリックしてプロジェクトを作成します。
7. プロジェクトの構造は、次のスクリーンショットと似ています

   ![android-project-structure](assets/android-project-structure.PNG)

8. **[!UICONTROL Tools]** > **[!UICONTROL Firebase].**&#x200B;をクリックします （これにより、プロジェクトが[!DNL Firebase]に追加されます）
9. **[!UICONTROL Set up Firebase Cloud Messaging].**&#x200B;をクリックします

   ![firebaseのセットアップ &#x200B;](assets/android-project-firebase-messaging.PNG)

10. **[!UICONTROL Connect to Firebase].**&#x200B;をクリックします
11. アプリをFirebaseに接続したら、**[!UICONTROL Add FCM to your app]をクリックします。**
12. **[!UICONTROL Accept Changes].**&#x200B;をクリックします

    アプリにFCMを追加する場合、プロジェクトに変更を加えるには、ウィザードに権限が必要です。

    ![[!DNL add-fcm-to-your-app]](assets/firebase-add-fcm-to-app.PNG)

アプリをFirebaseと正常に統合すると、次のようなメッセージが表示されます。

![[!DNL fcm-successfull]](assets/android-firebase-success.PNG)

[プロジェクトが [!DNL Firebase &#x200B;] コンソールにリストされていることを確認してください](https://console.firebase.google.com/)

## [!UICONTROL Push Channel]設定の構成

1. [!DNL Firebase] コンソールにログイン
2. **[!UICONTROL ACSPushTutorial]** プロジェクトを開きます。
3. **ギアアイコン**&#x200B;をクリックし、プロジェクト設定を開きます

   ![project-settings](assets/firebase-project-settings.PNG)

4. 「**[!UICONTROL Cloud Messaging]**」タブにタブします。
5. サーバーキーをコピー

   ![&#x200B; サーバーキー](assets/firebase-server-key.PNG)

6. Adobe Campaign Standard インスタンスへのログイン
7. **[!UICONTROL Adobe Campaign]** > **[!UICONTROL Administration]** > **[!UICONTROL Channels]** > **[!UICONTROL Mobile App]をクリックします。**
8. 適切な&#x200B;**[!UICONTROL Mobile Application Property].**&#x200B;を選択してください
9. **[!UICONTROL Push Channel settings]** セクションの&#x200B;**[!DNL Android]アイコン**&#x200B;をクリックします。
10. サーバーキーフィールドにサーバーキーを貼り付けます。

すべてがうまくいけば、成功のメッセージを見ることができます。

![push-channel-settings](assets/push-channel-settings.PNG)

要約すると、[!DNL Android App]を作成し、[!DNL Android App]を[!DNL Firebase]に接続しました。 次に、[!DNL Android] アプリのサーバーキーをAdobe Campaign Standardのモバイルアプリに貼り付けて、Adobe Campaignのモバイルアプリを[!DNL Android App]に接続しました。

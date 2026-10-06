---
title: パート 6 – プッシュ通知を送信して作業をテストする
description: パート 6 – プッシュ通知を送信して作業をテストする
feature: Push
jira: KT-4830
user: Admin
level: Experienced
doc-type: tutorial
activity: use
team: TM
exl-id: 10218e1f-6e85-490a-84d9-c5d42bd2321d
TQID: 'https://experienceleague.adobe.com/NrQc40vzqTy0fNfVT6fN0IjMKuXjilt6eZV-lgZpAcQ'
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
source-git-commit: 508c3590ce956401ccfba3a256000cbc5849a684
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 2%
---
# パート 6 - [!UICONTROL Push Notification]を送信して作業をテストする

Adobe Campaignを使用して[!UICONTROL Push Notification]を作成して送信する必要があります。 テスト用のシンプルなプッシュ通知を作成するには、次の手順に従います。

* Adobe Campaign Standard インスタンスにログインします
* **[!UICONTROL Marketing Activities]->[!UICONTROL Create]->[!UICONTROL Push Notification]**&#x200B;をクリックします
* **[!UICONTROL Send push to app subscribers(mobileApp)]**&#x200B;を選択し、「次へ」をクリックします
* **[!UICONTROL Associate a Mobile App to a delivery]** ドロップダウンリストから適切なモバイルアプリを選択し、**[!UICONTROL Next]**&#x200B;をクリックします
* カウントラベルをクリックすると、0より大きい値が返されます。 **[!UICONTROL Next]**&#x200B;をクリック
* 意味のある[!UICONTROL Message title]と[!UICONTROL Message body]を入力し、**[!UICONTROL Create]**&#x200B;をクリックします。
* 「**[!UICONTROL Prepare]**」をクリックします。 準備が完了したら、**[!UICONTROL Confirm]**&#x200B;をクリックしてメッセージを送信します。

すべてが正常に動作した場合は、エミュレーターで実行されているAndroid™ アプリに通知が表示されます

## その他のリソース

* [プッシュ通知の詳細ドキュメント](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/push-notifications/about-push-notifications.html?lang=ja)
* [プッシュ通知の作成（ビデオ）](/help/communication-channels/mobile/push-notifications/creating-a-push-notification.md)

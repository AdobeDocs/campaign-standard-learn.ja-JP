---
title: Android™ アプリ向けプッシュ通知の概要
description: このチュートリアルでは、プッシュ通知を Adobe Campaign から送信し Android™ アプリで受信する手順について説明します。
feature: Push
jira: KT-3846
doc-type: tutorial
activity: use
team: TM
recommendations: noDisplay
exl-id: 8dd772b2-b082-4e1e-842d-c5d6bcec564c
TQID: 'https://experienceleague.adobe.com/Ov4KKtdN-uhIr-TGldJCXw3GYFNUjap-SBE227dImfw'
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
source-git-commit: 508c3590ce956401ccfba3a256000cbc5849a684
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 100%
---
# Android™ アプリ向けプッシュ通知の概要

Adobe Campaign では、iOS と Android™ のモバイルデバイスに、パーソナライズされセグメント化されたプッシュ通知を送信できます。
これらのメッセージは、Experience Cloud Mobile SDK V4 または Experience Platform SDK を使用して Adobe Campaign でセットアップしたモバイルアプリケーションで受信されます。
このチュートリアルでは、プッシュ通知を Adobe Campaign から送信し Android™ アプリで受信する手順について説明します。

## 前提条件

* Adobe Campaign Standard 拡張機能を使用して起動プロパティを設定する必要があります。 以下のオンラインヘルプに従ってください。
  * [ビデオチュートリアル](https://video.tv.adobe.com/v/40903?captions=jpn&learn=on){transcript=true}
  * [ドキュメント](https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/communication-channels/mobile/configure-mobile-apps-using-aep-sdk.html?lang=ja)

* Adobe Campaign Standard で対応するプロパティのステータスが設定済みになっていることを確認します。
* [アクティブな Google Firebase アカウントを持っている](https://firebase.google.com)
* [最新バージョンの Android™ Studio がインストールされている](https://developer.android.com/studio)

## チュートリアルの手順

* [手順 1 - Android™ アプリの作成](/help/tutorial-push-notifications-android/create-android-app.md)
* [手順 2 - Mobile SDK の統合](/help/tutorial-push-notifications-android/integrating-with-mobile-sdk.md)
* [手順 3 - モバイルアプリに拡張機能を登録](/help/tutorial-push-notifications-android/register-mobile-extensions.md)
* [手順 4 - プッシュ識別情報の設定](/help/tutorial-push-notifications-android/set-push-identifier.md)
* [手順 5 - 通知の伝達](/help/tutorial-push-notifications-android/propagate-notification.md)
* [手順 6 - プッシュ通知を送信](/help/tutorial-push-notifications-android/send-push-notification.md)

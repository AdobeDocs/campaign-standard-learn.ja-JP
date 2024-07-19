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
source-git-commit: 943599bd7ce139ef846f093ebda9084a91550aca
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 100%

---

# Android™ アプリ向けプッシュ通知の概要

Adobe Campaign では、iOS と Android™ のモバイルデバイスに、パーソナライズされセグメント化されたプッシュ通知を送信できます。
これらのメッセージは、Experience Cloud Mobile SDK V4 または Experience Platform SDK を使用して Adobe Campaign でセットアップしたモバイルアプリケーションで受信されます。
このチュートリアルでは、プッシュ通知を Adobe Campaign から送信し Android™ アプリで受信する手順について説明します。

## 前提条件

* Adobe Campaign Standard 拡張機能を使用して起動プロパティを設定する必要があります。以下のオンラインヘルプに従ってください。
   * [ビデオチュートリアル](https://video.tv.adobe.com/v/26224?learn=on){transcript=true}
   * [ドキュメント](https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/communication-channels/mobile/configure-mobile-apps-using-aep-sdk.html?lang=ja)

* 対応するプロパティの Adobe Campaign Standard でのステータスが設定済みになっていることを確認します。
* [アクティブな Google Firebase アカウントを持っている](https://firebase.google.com)
* [最新バージョンの Android™ Studio がインストールされている](https://developer.android.com/studio)

## チュートリアルの手順

* [手順 1 - Android™ アプリの作成](/help/tutorial-push-notifications-android/create-android-app.md)
* [手順 2 - Mobile SDK の統合](/help/tutorial-push-notifications-android/integrating-with-mobile-sdk.md)
* [手順 3 - モバイルアプリに拡張機能を登録](/help/tutorial-push-notifications-android/register-mobile-extensions.md)
* [手順 4 - プッシュ識別情報の設定](/help/tutorial-push-notifications-android/set-push-identifier.md)
* [手順 5 - 通知の伝達](/help/tutorial-push-notifications-android/propagate-notification.md)
* [手順 6 - プッシュ通知を送信](/help/tutorial-push-notifications-android/send-push-notification.md)

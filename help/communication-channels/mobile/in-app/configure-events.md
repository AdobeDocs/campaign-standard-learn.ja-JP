---
title: イベントの設定
description: 'Adobe Campaign標準(ACS)でアプリ内メッセージを設定する場合、イベントが開始するアクションによって表示するメッセージがトリガーされるユーザーが定義します。 '
feature: In-App
topics: Mobile
kt: 2548
doc-type: feature video
activity: use
team: TM
translation-type: tm+mt
source-git-commit: 82fb2d39dc61a55c0aa20ca1fa215f35a7dd9088
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 1%

---


# 設定 [!UICONTROL Events] {#configuring-events}

メッセージを設定する場合、 [!UICONTROL In-App] 表示するメッセージをトリガーするユーザー開始アクションを定義する必要があります。 これらのアクションは呼び出され [!UICONTROL events]ます。 次の3つのカテゴリ [!UICONTROL events] を使用できます。 [!UICONTROL Mobile Application events]、 [!UICONTROL Life Cycle events]および [!UICONTROL Analytics events]。

## [!UICONTROL Mobile Application Events] {#mobile-application-events}

[!UICONTROL Mobile Application events] の組み合わせ [!UICONTROL custom events] がモバイルアプリケーションに実装されているかどうかを確認します。

次に例を示します。

* 顧客が品目を閲覧しました
* 顧客が買い物かごに品目を追加
* 買い物かごの放棄
* 顧客が何かを購入した

これらはAdobe Campaignで設定する必要 [!UICONTROL events] があります。 次のビデオでは、この方法について説明します。

>[!VIDEO](https://video.tv.adobe.com/v/26245?quality=12)

## [!UICONTROL Life Cycle events]  {#life-cycle-events}

[!UICONTROL Lifecycle events] は標準です [!UICONTROL events]。 The following [!UICONTROL events] are available:

* [!UICONTROL launched]
* [!UICONTROL upgraded]
* [!UICONTROL crashed]

使用例としては、アップグレード後に新機能を紹介するメッセージや、イベントのプロモーションなどがあります。

>[!NOTE]
>
>モバイルアプリケーションで設定する [!UICONTROL Lifecycle module] 必要があります。 アプリにライフサイクルを追加する [方法について詳しくは、こちらを参照してください](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/lifecycle)

## [!UICONTROL Analytics Events] {#analytics-events}

モバイルアプリで実装されるカテゴリに応じて、以下の3つの実装がサポートされます。

* Adobe Analytics
* [!UICONTROL Context data]
* [!UICONTROL View state]

>[!NOTE]
>
>[!UICONTROL Analytics events] Adobe Analyticsライセンスが必要です。 [!DNL Analytics]拡張機能を設定し [、](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics#configure-analytics-extension-in-launch) Analyticsをアプリに追加すると [、これらのイベントはACSの](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics#add-analytics-to-your-app)[!UICONTROL In-App] 設定で使用できるようになります。

## その他のリソース

* [ライフサイクル指標の有効化（ドキュメント）](https://aep-sdks.gitbook.io/docs/getting-started/initialize-the-sdk#enable-lifecycle-metrics)
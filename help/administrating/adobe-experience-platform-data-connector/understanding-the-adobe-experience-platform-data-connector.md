---
title: Adobe Experience Platform Data Connectorについて
description: Adobe Experience Platform Data Connectorは、XTK データ（Campaignに取り込まれたデータ）をAdobe Experience PlatformのExperience Data Model （XDM）データにマッピングすることで、Adobe Experience Platformでデータを利用できるようにします。
feature: People Core Service Integration
jira: KT-2826
thumbnail: 27304.jpg
role: User
level: Experienced
doc-type: feature video
activity: understand
team: TM
exl-id: 686961f9-5374-4cc6-8b36-7ee0584ea720
TQID: https://experienceleague.adobe.com/8z32-bArYoMN41QFSi19bXUFc617UqZvdzxaam0Xr-E
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 7d15c0a5dc01907ff529b3684eaddaca5321facc
workflow-type: tm+mt
source-wordcount: 273
ht-degree: 4%

---

# Adobe Experience Platform [!UICONTROL Data Connector]について

>[!NOTE]
>
>この機能はベータ版で、予告なく頻繁に更新および変更される可能性があります。
>
>この機能を実装する予定がある場合は、[!UICONTROL Adobe Customer Support]にお問い合わせください。

## 概要

Adobe Experience Platform [!UICONTROL Data Connector]は、XTK データ（Adobe Campaignで取り込まれたデータ）をAdobe Experience Platformの[!DNL Experience Data Model] （XDM）データにマッピングすることで、既存のお客様がAdobe Experience Platformでデータを利用できるようにします。

コネクタは一方向であり、Adobe Campaign StandardからAdobe Experience Platformにデータを送信します。 Adobe Experience PlatformからAdobe Campaign Standardにデータが送信されることはありません。

Adobe Experience Platform [!UICONTROL Data Connector]は、Adobe Campaign Standard [!UICONTROL custom resources]を理解し、お客様の全体的なデータスキーマをAdobe Experience Platform内でどのように使用すべきかを理解しているデータエンジニアを対象としています。

>[!VIDEO](https://video.tv.adobe.com/v/34384?captions=jpn&learn=on){transcript=true}

*このビデオでは、Adobe Experience Platform [!UICONTROL Data Connector] （09:35分）*&#x200B;の概要を説明します

>[!NOTE]
>
>[!UICONTROL subscription events]のすぐに使用できる転送はサポートされていません。 [!UICONTROL subscription events]を転送するには、対応するXDMとデータセットをAdobe Experience Platformで作成し、これらのデータにカスタムデータマッピングを設定します。
>
>既存の[!UICONTROL experience events]はAdobe Experience Platformに取り込めませんが、継続的に生成された[!UICONTROL experience events]はAdobe Experience Platformにストリーミングされます。

## データマッピングを実行するための主な手順

次のチュートリアルでは、Campaign StandardとAdobe Experience Platform間のデータマッピングを実行するための主な手順について説明します。

1. [カスタムリソースのマッピング](/help/administrating/adobe-experience-platform-data-connector/mapping-custom-resources.md)
2. [エクスペリエンスイベントのマッピング](/help/administrating/adobe-experience-platform-data-connector/mapping-experience-events.md)
3. [シードテーブルデータのマッピング](/help/administrating/adobe-experience-platform-data-connector/mapping-seed-table-data.md)
4. [データマッピングの変更](/help/administrating/adobe-experience-platform-data-connector/modifying-data-mapping.md)
5. [データ取り込みジョブのステータスの確認](/help/administrating/adobe-experience-platform-data-connector/checking-status-of-data-ingestion-jobs.md)


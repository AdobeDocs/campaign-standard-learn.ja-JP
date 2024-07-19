---
title: Adobe Experience Platform Data Connector について
description: Adobe Experience Platform Data Connector は、XTK データ（Campaign に取り込まれたデータ）をAdobe Experience Platformの Experience Data Model （XDM）データにマッピングすることで、既存のお客様がAdobe Experience Platformでデータを使用できるようにします。
feature: People Core Service Integration
jira: KT-2826
thumbnail: 27304.jpg
role: User
level: Experienced
doc-type: feature video
activity: understand
team: TM
exl-id: 686961f9-5374-4cc6-8b36-7ee0584ea720
source-git-commit: 943599bd7ce139ef846f093ebda9084a91550aca
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 5%

---

# Adobe Experience Platform [!UICONTROL Data Connector] について

>[!NOTE]
>
>この機能はベータ版で、予告なく頻繁に更新や変更が行われる可能性があります。
>
>この機能を実装する予定がある場合は、[!UICONTROL Adobe Customer Support] にお問い合わせください。

## 概要

Adobe Experience Platform [!UICONTROL Data Connector] は、XTK データ（Adobe Campaignに取り込まれたデータ）をAdobe Experience Platform上の [!DNL Experience Data Model] （XDM）データにマッピングすることで、既存のお客様がAdobe Experience Platform上でデータを利用できるようにするのに役立ちます。

コネクタは単方向で、Adobe Campaign StandardからAdobe Experience Platformにデータを送信します。 Adobe Experience PlatformからAdobe Campaign Standardにはデータが送信されません。

Adobe Experience Platform [!UICONTROL Data Connector] は、Adobe Campaign Standard [!UICONTROL custom resources] を理解し、顧客の全体的なデータスキーマがAdobe Experience Platform内でどのように配置されるべきかを理解している、データエンジニアを対象としています。

>[!VIDEO](https://video.tv.adobe.com/v/27304?learn=on){transcript=true}

*このビデオでは、Adobe Experience Platformの [!UICONTROL Data Connector] （9 分 35 秒）の概要を説明し* す。

>[!NOTE]
>
>[!UICONTROL subscription events] の標準転送はサポートされていません。 [!UICONTROL subscription events] を転送するには、対応する XDM とデータセットをAdobe Experience Platformで作成し、これらのデータのカスタムデータマッピングを設定します。
>
>既存の [!UICONTROL experience events] はAdobe Experience Platformに取り込むことはできませんが、進行中の生成された [!UICONTROL experience events] はAdobe Experience Platformにストリーミングされます。

## データマッピングを実行するための主な手順

次のチュートリアルでは、Campaign StandardとAdobe Experience Platformの間でデータマッピングを実行する主な手順を説明します。

1. [カスタムリソースのマッピング](/help/administrating/adobe-experience-platform-data-connector/mapping-custom-resources.md)
2. [エクスペリエンスイベントのマッピング](/help/administrating/adobe-experience-platform-data-connector/mapping-experience-events.md)
3. [シードテーブルデータのマッピング](/help/administrating/adobe-experience-platform-data-connector/mapping-seed-table-data.md)
4. [データマッピングの変更](/help/administrating/adobe-experience-platform-data-connector/modifying-data-mapping.md)
5. [データ取り込みジョブのステータスの確認](/help/administrating/adobe-experience-platform-data-connector/checking-status-of-data-ingestion-jobs.md)


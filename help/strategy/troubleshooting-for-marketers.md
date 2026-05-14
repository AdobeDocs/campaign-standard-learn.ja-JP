---
title: マーケター向けトラブルシューティング
description: 最も一般的なエラーを把握することで、迅速な問題解決と生産性の向上に役立ちます。 これらのトラブルシューティングのヒントは、同様のエラーが発生したときに効果的に解決するのに役立ちます。
feature: Workflows
role: User
level: Beginner, Intermediate, Experienced
doc-type: Article
last-substantial-update: 2023-05-18T00:00:00.000Z
jira: KT-13256
thumbnail: KT-13256.jpeg
exl-id: 24a6815b-52d1-4bd6-9d27-522720a91f83
TQID: https://experienceleague.adobe.com/ISwW4zu0AWc3kmK-H2kOy-r9bPvLsTCLAnk4mbgZkS0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616a
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 7d15c0a5dc01907ff529b3684eaddaca5321facc
workflow-type: tm+mt
source-wordcount: 743
ht-degree: 0%

---

# マーケター向けのトラブルシューティング：5つの一般的なワークフローと配信エラー

作成者：[ スライ パトラ ](https://www.linkedin.com/in/suraj-p-51612053/){target="_blank"}、Meijer、シニアコンサルタント

過去5年間、Adobe Experience Cloud製品のシニアエンジニアおよびカスタマーエキスパートとして、1934年に設立された米国のスーパーセンターチェーンである[Meijer](https://www.meijer.com/){target="_blank"}のビジネスユーザーが、ACSで複雑なマーケティングキャンペーンやトランザクションキャンペーンを実行できるようにしています。 私が取り組んできたプロジェクトには、パーソナライズのためのオファーや注文詳細を保存するカスタマイズされたキャンペーン、Adobe Audience Managerとの統合、セグメント取り込みのためのcustomer insightなどがあります。


ACSを使用している間、エラーが発生し、解決に時間がかかり、フラストレーションが生じる可能性があります。 最も一般的なエラーを把握することで、迅速な問題解決と生産性の向上に役立ちます。 以下は、同様のエラーが発生したときに効果的に解決するのに役立つトラブルシューティングのヒントです。

## データタイプの不一致エラー

**エラーコード：**
`PGS-220000 PostgreSQL error: ERROR: operator does not exist: character varying = bigint`

**原因：**
これらのタイプのエラーは、異なるデータタイプのフィールドを使用して調整しようとすると、ワークフローに表示されます。 例えば、文字列フィールドを持つload fileを使用してファイルをアップロードし、その文字列フィールドをデータ型がintのプロファイルフィールドと紐付けようとします。

![data-type-mismatch-error](/help/assets/kt-13256/data-type-mismatch.png)

**解決策：**
「ファイルをロード」アクティビティのフィールドのデータタイプを、一致するデータタイプに変更します。 「ファイルをロード」アクティビティを開きます。 「COLUMN DEFINITION」タブに移動し、目的のフィールドのデータタイプを変更します。


![data-type-mismatch-solution](/help/assets/kt-13256/data-type-mismatch-solution.png)

## 配信Personalization エラー

**エラーコード：**
`The schema for profiles specified in the transition ('') is not compatible with the schema defined in the delivery template ('nms:recipient'). They should be identical.`

**原因：**
このエラーは、メールアドレスに電子メールを送信しているときに表示されますが、電子メールやその他の識別子がプロファイルと紐付けられていません。 電子メール通信を送信するには、電子メールまたは識別子を常にプロファイルにリンクする必要があります。

![紐付けアクティビティを含むワークフロー](/help/assets/kt-13256/del-persn-error-wf.png)

**解決策：**
共通IDは、受信者テーブルを含む読み込まれたファイルに存在する必要があります。 この共通キーは、紐付けアクティビティ内の受信者テーブルに読み込みファイルを結合します。 メールは、受信者テーブルに存在しないレコードには送信できません。これには、ワークフロー内のこの紐付けステップが必要です。 これにより、受信する読み込みファイルアクティビティを、プロファイルの電子メール IDなどの識別子と照合します。 `nms:recipient` スキーマはプロファイルテーブルを参照し、受信レコードとプロファイルを照合することで、メール準備中に使用できるようになります。

以下に示すように、紐付けアクティビティのスクリーンショットを参照してください。

![紐付けの詳細を含むワークフロー](/help/assets/kt-13256/del-persn-error-wf-solution.png)

[紐付け](https://experienceleague.adobe.com/en/docs/campaign-standard/using/managing-processes-and-data/data-management-activities/reconciliation)の詳細をご覧ください。

## 共通フィールドデータセットエラー

**エラーコード：**
`The document types of inbound events (''and'') are incompatible (step 'Exclusion'). Unable to perform the operation. `

**原因：**
この問題は、ACS ワークフローで**exclusion アクティビティ**&#x200B;を使用している場合、IDに基づいて除外を実行する場合、プライマリセットと除外セットが同じフィールド名を持たない場合に発生します。


![共通フィールドデータセットエラー](/help/assets/kt-13256/dataset-error.png)

**解決策：**

このエラーを解決するには、次の2つの方法があります。

1. プライマリと除外の両方で同じフィールド名を使用し、そのフィールドをIDとして使用します

   あるいは

2. JOINS除外メソッドを使用して、レコードを除外するフィールドを選択します。

![共通フィールド データセット エラー – 解決策](/help/assets/kt-13256/dataset-error-solution.png)

## フィールド名がドロップされましたエラー

**エラーコード：**
`XTK-170036 Unable to parse expression 'i__name'`

**原因：**

エラーポイントは、**エンリッチメントアクティビティ**&#x200B;で発生する可能性があります。 最も一般的なものの1つは下に表示されます。

![ フィールド名が削除されましたエラー](/help/assets/kt-13256/field-name-dropped-error.png)

これは、アクティビティでエクスプレッション名を手動で編集した場合に発生します。 この画像は、式が`name `から`i__name`に変更されたことを示しています。

**解決策：**

このエラーは、次の3つの方法で解決できます。

1. 名前を元の式に戻します。

2. 新しい名前を使用する場合は、**エンリッチメントアクティビティ**&#x200B;の値を変更します。

3. 何が変わったのかを覚えていない場合は、アクティビティを再現することが最善の策です。

## 一時テーブルが削除されたエラー 

**エラーコード：**
`XTK-170024 The temporary schema "temp:deliveryEmail1" is not defined in the current context.`

**原因：**
これは、エンリッチメントやその他のアクティビティを伴う複雑なワークフローでよくあるエラーです。 ワークフローの複数の変更中に、一部のアクティビティワークフローが正しく保存されない可能性があります。

![一時テーブルが削除されましたエラー](/help/assets/kt-13256/temp-table-dropped-error.png)

**解決策：**
このエラーが発生する可能性がある多くの方法があるので、簡単な修正はありません。 単純なワークフローの場合は、アクティビティを再設定することをお勧めします。 複雑なワークフローでは、ワークフローアクティビティを新しいワークフローにコピーし、保存して再実行することをお勧めします。

---
title: マーケター向けトラブルシューティング
description: 最も一般的なエラーを把握することで、問題解決の迅速化と生産性の向上に役立ちます。 これらのトラブルシューティングヒントは、同様のエラーが発生した場合に効果的に解決するのに役立ちます。
version: Standard
feature: Workflows
role: User
level: Beginner, Intermediate, Experienced
doc-type: Article
last-substantial-update: 2023-05-18T00:00:00Z
jira: KT-13256
thumbnail: KT-13256.jpeg
exl-id: 24a6815b-52d1-4bd6-9d27-522720a91f83
source-git-commit: cfa097e1ea0d5ca8c97c1062ea8717c37a51530d
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# マーケター向けのトラブルシューティング：ワークフローと配信に関する 5 つの一般的なエラー

著者：[Suraj Patra](https://www.linkedin.com/in/suraj-p-51612053/){target="_blank"}、シニアコンサルタント、Meijer

過去 5 年間にわたり、Adobe Experience Cloudのシニアエンジニアおよびカスタマーエキスパートとして、1934 年に設立されたアメリカのスーパーセンターチェーンである [Meijer](https://www.meijer.com/){target="_blank"} のビジネスユーザーが、ACS で複雑なマーケティングおよびトランザクションキャンペーンを実行できるようにしています。 私が取り組んでいるプロジェクトには、パーソナライゼーションのためのオファーや注文の詳細の保存、Adobe Audience Managerとの統合、セグメント取り込みのためのカスタマーインサイトを行うためのカスタマイズされたキャンペーンなどがあります。


ACS を使用している間にエラーが発生しました。これは、解決に時間がかかり、フラストレーションを伴う可能性があります。 最も一般的なエラーを把握することで、問題解決の迅速化と生産性の向上に役立ちます。 同様のエラーが発生した場合に効果的に解決するのに役立つ、トラブルシューティングのヒントを以下に示します。

## データタイプ不一致エラー

**エラーコード：**
`PGS-220000 PostgreSQL error: ERROR: operator does not exist: character varying = bigint`

**原因：**
これらのタイプのエラーは、異なるデータタイプのフィールドを使用して紐付けしようとしたときにワークフローに表示されます。 例えば、「文字列」フィールドを持つ「ファイルを読み込み」を使用してファイルをアップロードし、文字列フィールドを、データタイプが int のプロファイルフィールドと紐付けしようとした場合です。

![data-type-mismatch-error](/help/assets/kt-13256/data-type-mismatch.png)

**解決策：**
「ファイルを読み込み」アクティビティのフィールドのデータタイプを、一致するデータタイプに変更します。 「ファイルを読み込み」アクティビティを開きます。 「列定義」タブに移動し、目的のフィールドのデータタイプを変更します。


![data-type-mismatch-solution](/help/assets/kt-13256/data-type-mismatch-solution.png)

## 配信Personalization エラー

**エラーコード：**
`The schema for profiles specified in the transition ('') is not compatible with the schema defined in the delivery template ('nms:recipient'). They should be identical.`

**原因：**
このエラーは、メールをアドレスに送信しているとき、メールやその他の識別子がプロファイルと紐付けされない場合に表示されます。 メール通信を送信するには、メールまたは識別子が常にプロファイルにリンクされている必要があります。

![ 紐付けアクティビティを使用したワークフロー ](/help/assets/kt-13256/del-persn-error-wf.png)

**解決策：**
読み込んだファイルから、受信者テーブルに共通の ID が存在する必要があります。 この共通キーは、紐付けアクティビティ内の受信者テーブルに読み込みファイルを結合します。 受信者テーブルに存在しないレコードにはメールが送信されない場合があります。この場合、ワークフロー内でこの紐付けステップが必要になります。 その際に、受信した読み込みファイル アクティビティを、プロファイルのメール ID などの識別子と紐付けます。 `nms:recipient` スキーマはプロファイルテーブルを参照し、受信レコードをプロファイルと紐付けすると、メールの準備中に使用できるようになります。

以下に示すように、紐付けアクティビティのスクリーンショットを参照します。

![ 紐付けの詳細を使用したワークフロー ](/help/assets/kt-13256/del-persn-error-wf-solution.png)

詳しくは、[ 紐付け ](https://experienceleague.adobe.com/en/docs/campaign-standard/using/managing-processes-and-data/data-management-activities/reconciliation) を参照してください。

## 共通フィールドデータセットエラー

**エラーコード：**
`The document types of inbound events (''and'') are incompatible (step 'Exclusion'). Unable to perform the operation. `

**原因：**
この問題は、ACS ワークフローで **除外アクティビティ** を使用しているとき、ID に基づいて除外を実行するとき、プライマリセットと除外セットが同じフィールド名を持っていないときに発生します。


![ 共通フィールドデータセットエラー ](/help/assets/kt-13256/dataset-error.png)

**解決策：**

このエラーを解決する方法は 2 つあります。

1. プライマリと除外の両方で同じフィールド名を使用し、そのフィールドを ID として使用します。

   あるいは

2. JOINS 除外メソッドを使用して、レコードを除外するフィールドを選択します。

![ 共通フィールドデータセットエラー – ソリューション ](/help/assets/kt-13256/dataset-error-solution.png)

## フィールド名のドロップエラー

**エラーコード：**
`XTK-170036 Unable to parse expression 'i__name'`

**原因：**

エラーポイントは、**エンリッチメントアクティビティ** で発生する場合があります。 最も一般的なものの 1 つを以下に示します。

![ フィールド名のドロップエラー ](/help/assets/kt-13256/field-name-dropped-error.png)

これは、アクティビティの式名を手動で編集したときに発生します。 この画像は、式が `name ` から `i__name` に変更されたことを示しています。

**解決策：**

このエラーは次の 3 つの方法で解決できます。

1. 名前を元の式に戻します。

2. 新しい名前を使用する場合は、**エンリッチメントアクティビティ** の値を変更します。

3. 何が変更されたかを覚えていない場合は、アクティビティを再作成することをお勧めします。

## 一時テーブルの削除エラー 

**エラーコード：**
`XTK-170024 The temporary schema "temp:deliveryEmail1" is not defined in the current context.`

**原因：**
これは、エンリッチメントやその他のアクティビティを含む複雑なワークフローで発生する一般的なエラーです。 ワークフローに対して複数の変更を行う際に、一部のアクティビティワークフローが正しく保存されないことがあります。

![ 一時テーブルの削除エラー ](/help/assets/kt-13256/temp-table-dropped-error.png)

**解決策：**
このエラーが発生する可能性がある方法は多数あるので、単純な修正はありません。 単純なワークフローの場合は、アクティビティを再設定する方が良いでしょう。 複雑なワークフローでは、ワークフローアクティビティを新しいワークフローにコピーし、保存して再実行する方が効率的です。

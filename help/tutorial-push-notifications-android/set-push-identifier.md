---
title: 手順 4 - pushidentifier の設定
description: '**pushIdentifier**は、プッシュ通知用のデバイストークンを含む文字列です。 Firebase から送信されるトークンと同じで、MobileCore.setPushIdentifier メソッドを使用して SDK に渡されます。'
feature: Push
user: Admin
level: Experienced
jira: KT-4828
doc-type: tutorial
activity: use
team: TM
exl-id: 08387b84-edaa-45ee-ae66-53bcbd5c7c39
source-git-commit: 757afce50981b96b7820c987308d639a73746c0c
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 手順 4 - [!DNL pushidentifier] の設定

**[!DNL pushidentifier]** は、[!DNL Push] 通知用のデバイストークンを含む文字列です。 [!DNL Firebase] から送信され、[!DNL MobileCore.setPushIdentifier] メソッドを使用して SDK に渡されるトークンと同じです。

[!DNL Android™]studio でプロジェクトを開きます。 [!DNL MainActivity] のコード全体 **パッケージステートメントの最初の行を除く** を削除します。

次のコードを [!DNL MainActivity] に貼り付けます。

<!--
Removed `{.line-numbers}` below
-->

```java
import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.util.Log;
import android.widget.Toast;

import com.adobe.marketing.mobile.MobileCore;
import com.google.android.gms.tasks.OnCompleteListener;
import com.google.android.gms.tasks.Task;
import com.google.firebase.iid.FirebaseInstanceId;
import com.google.firebase.iid.InstanceIdResult;

public class MainActivity extends AppCompatActivity {

@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);

registerToken();
}

void registerToken() {
FirebaseInstanceId.getInstance().getInstanceId()
    .addOnCompleteListener(new OnCompleteListener<InstanceIdResult>() {
        @Override
        public void onComplete(@NonNull Task<InstanceIdResult> task) {
            if (!task.isSuccessful()) {
                Log.w("Message App", "getInstanceId failed", task.getException());
                return;
            }

// Get new Instance ID token
String token = task.getResult().getToken();

Log.d("Got token", token);

MobileCore.setPushIdentifier(token);
}
});
}

@Override
public void onResume() {
super.onResume();
MobileCore.setApplication(getApplication());
MobileCore.lifecycleStart(null);
}

@Override
public void onPause() {
super.onPause();
MobileCore.lifecyclePause();
}
}
```

## アプリのテスト

先に進む前に、今がアプリをテストするのに良いタイミングです。

* 緑の矢印をクリックするか、**[!DNL Run->Run'app']** を選択して、アプリを実行します。
* [!DNL Android™] エミュレーターが起動し、アプリが [!DNL "Hello World"]text で実行されているのが確認できます。
* [!DNL logcat] ウィンドウを開きます。 「[!DNL Got]」を検索します。 次に示すように、[!DNL Firebase] から受信したトークンがログに書き込まれているのが確認できます。 「[!DNL Got token]」の後の長い文字列は [!DNL pushidentifier] で、Adobe Campaignに送信されます。

![logcat-token](assets/logcat-got-token.PNG)

### モバイルアプリケーション購読者の確認

Adobe Campaign Standard インスタンスにログインします。
**[!UICONTROL Administration->Channels->Mobile App(Experience Platform SDK)]** に移動します。 適切なモバイルアプリケーションを開きます。 「[!UICONTROL Mobile Application Subscribers]」タブに移動します。 [!UICONTROL registration token]listed が表示されます。

![ モバイルアプリケーション購読者 ](assets/mobile-application-subscribers.PNG)

>[!NOTE]
>
>[!UICONTROL Mobile Application Subscribers] のタブに登録トークンが表示されない場合は、先に進む前にここで停止します。

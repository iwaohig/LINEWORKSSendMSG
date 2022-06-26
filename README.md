LINE WORKS API 2.0 に対応した Power Automate カスタム コネクタを作成しました。
User Account認証 (OAuth) に対応しました。
Github からインポートして利用できます。

## LINE WORKS Developer Console で アプリの設定

LINE WORKS Developer Console で "アプリの新規追加" を行います。

![l_1517737_1932_1295192978cc5b6cfb886fcc1bf25814.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/c5a6414f-6c52-5d8e-62bf-5cb33602289e.png)

任意のアプリ名を入力して、[追加] をクリック。

![l_1517737_1933_59dcc6b6abdd842b427fd4cf024cee51.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/5dbad7c1-f2c2-d315-36a1-874170a65315.png)

"アプリの説明" に任意の説明文。

![l_1517737_1934_f0dd95f53112085209a78ae8c68229de.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/45a2fe04-edb5-37d2-ab0c-03a7490162ad.png)

"Redirect URL" に以下を入力して [追加] 。

```
https://global.consent.azure-apim.net/redirect
```

"OAuth Scopes" は "bot" を選択して [保存] 。

![l_1517737_1928_4fefdd57f5d4b4cbd2866f12410bd3eb.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/c77418aa-0530-2888-69d1-76920766c029.png)

![l_1517737_1929_f45ae5d50b1fa4064e2340d172517e63.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/8254384d-7359-c97b-0907-82dd674d905a.png)

## Power Automate でカスタム コネクタを新規作成

[+カスタム コネクタの新規作成] - [URL から OpenAPI をインポートします] をクリック。

![l_1517737_1912_14ae7b7e2aa96c5da6e5b1f21b8ecd42.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/36bc6cee-dd0a-b900-8356-7564f74ef920.png)

任意の "コネクタ名" を入力する。

"Open API の URL に貼り付ける" に以下の URL を入力して、[インポート] をクリック。

```
https://raw.githubusercontent.com/iwaohig/LINEWORKSSendMSG/main/LINE-WORKS.swagger.json
```

![l_1517737_1913_755a88b7e3d7184cb1a1fe3f4bc22603.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/2c08b6df-d93f-cbf9-7779-b4dd7032350f.png)

[続行] をクリック。

![l_1517737_1935_6fc38154c1f44bd45cf9644e90ba443e.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/1c207b9f-3fa2-c004-b11c-e6cc435e9a69.png)

[コネクタ アイコンのアップロード] と [アイコンの背景色] は任意の設定を行います。

右下の [セキュリティ] のリンクをクリック。

![l_1517737_1917_f4d35514b52093c6cfbb6f9dcfad00ac.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/5df6c634-4b43-be91-0d93-9e48fc9d0ca3.png)

[Client id], [Client Secret] は LINE WORKS Developer Console で作成したアプリの値を入力します。

[Redirect URL] は以下を入力。

```
https://auth.worksmobile.com/oauth2/v2.0/token
```

![l_1517737_1919_4b2257100628eadc2882c96735a6688e.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/f72dabc8-d88e-7612-1ce6-df39f8995193.png)

右上の [コネクタの作成] をクリック。

![l_1517737_1920_a9b9627ebfcc39faeb0bac82a4b245af.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/92d17518-6744-0dcf-ed3f-94bc37ac7d49.png)

作成が完了したら [閉じる] をクリック。

![l_1517737_1921_86d6ccded3c2c6752a12b944db283c97.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/e30e2d54-ca76-c209-b74e-8708b1f24cee.png)

## Power Automate のフローでカスタム コネクタを利用する

フローのアクションでカスタム コネクタのリストから作成したコネクタを選択します。

![l_1517737_1922_adf95bef6d4eed9fb84c60e51de0ba4e.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/dab487bb-f257-9d7d-0e70-50f5c308e555.png)

アクションはスクリーン ショットの 2 種類です。いずれかを選択します。

![l_1517737_1923_59a2a1bedecd8af2d01e849f8aa39bdc.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/75e8e44b-75c5-598d-f561-530c0ccc5e6a.png)

最初の利用時には接続の作成が必要です。[サインイン] をクリックします。

![l_1517737_1925_16f7a140a23ccc1791c608b16a1d51b2.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/cc6104fd-6e15-daf9-4a4b-0399958c2d2a.png)

認証ウィンドウで LINE WORKS にログインします。

![l_1517737_1930_0ad830f88065fa7cc482728c3a0ed192.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/6ea51948-725c-b671-1f86-c39149cc74d9.png)

コネクタの利用が可能になりました。

![l_1517737_1931_9cb9b565059abec420f16dd51810ffac.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/396107/f052dd26-814e-13db-0cf8-f1ce745bac38.png)





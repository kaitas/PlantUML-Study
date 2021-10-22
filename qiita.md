# Qiita記事の原稿
[](
https://qiita.com/drafts/c955e29c1638efafc5eb/
)
[https://qiita.com/drafts/c955e29c1638efafc5eb/](https://qiita.com/drafts/c955e29c1638efafc5eb/)

# 注:UML初心者に向けた記事です
---
# 最終的にこんな感じに…
![kawaii-PlantUML.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/191291/f7f1f124-9dbf-2acc-9b13-53dad8b56688.png)

---

## 注: AWS提供の画像を利用しますがAWSのサービスは使用しません。

---

## 環境設定とねらい
Visual Studio Code だけでUMLを練習する環境を作ります。Mac, Windows, Linuxで動きます。

---
## 用意するもの
- Visual Studio Code
- [PlantUML 拡張](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml)
    - Java（ふつうは[入ってます](https://java.com/ja/)）
    - GraphViz（[msiインストーラあり](https://graphviz.gitlab.io/_pages/Download/Download_windows.html)）


上記の手順についてわからない人は[Visual Studio Code で UML を描こう！](https://qiita.com/couzie/items/9dedb834c5aff09ea7b2)が完璧なので、まずは設定を済ませてきてください。

---

#まずは書いてみよう

Visual Studio Codeで新規ファイルを作って、まずは `myfirst.pu` というテキストファイルで保存します。
*.puはPlantUMLの推奨拡張子のようです。
`Alt + D` で右側に PlantUML Preview というウインドウが現れて画像が生成されます。

```myfirst.pu
@startuml
actor わたし
actor あなた
わたし-->あなた : すこ
あなた-->わたし : すこ
@enduml
```
---

こんな感じに右側に表示されます。

![myfirstpu.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/191291/3d81d6a4-afef-1f71-2256-dd2dd1987e34.png)

内部ではjavaとGraphVizがものすごく高速に画像を生成してくれているようです。日本語も問題なく通ります。

---
ここまでできたら、まずはUMLの基本を「[Visual Studio Codeで自由自在にUMLを描こう](https://blog.okazuki.jp/entry/2016/09/01/215508)」で、一通りUMLでできることを学んでみることをオススメします。
「[リゼロで学ぶUML](https://qiita.com/es-s-sugimoto/items/5314d5dd6902acc2d96e)」なんかも好きな人にはいいかなと思います。

---

##PlantUMLは便利
[PlantUML](https://plantuml.com/ja/stdlib)は幅広い人に使われているようなので、覚えておいて損はないと思います。
例えば、Chrome機能拡張に「[Pegmatite](https://chrome.google.com/webstore/detail/pegmatite/jegkfbnfbfnohncpcfcimepibmhlkldo)」があり、Githubなどに書かれた `@startml ～ @enduml` を自動でサーバ経由で画像化してくれたりもします（[Pegmatite作者のGithub](https://github.com/dai0304/pegmatite)）。

---

### actorでこんな感じに関係が書けます
 
```actor.pu
@startuml 
rectangle VTuberイベントとお客様   {
actor 来場者
actor ファン
actor プロデューサ
actor 演者
来場者-->演者 : すこ
ファン-->演者 : すこ
プロデューサ -> 演者 : 支援
}
@enduml
```

![kawaikunai.pu.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/191291/6a43a148-a12c-9ffb-2812-ed0f663f5f50.png)

---
## actorに着色
actor の後ろに [Webカラーコード](https://htmlcolorcodes.com/)で指定することでデコレーションできるようです。

```HTMLcolor.pu
@startuml 
rectangle かわいくないUML  {
actor 来場者 #AAA
actor ファン #BBB
actor プロデューサ #00A
actor 演者 #A00
来場者-->演者 : すこ
ファン-->演者 : すこ
プロデューサ -> 演者 : 支援
}
@enduml
```
---

このあたりでそろそろ気づくことがあります。

---
# UMLはかわいくない

ところでUMLはかわいくないです。

---

## UMLはキレイだが美しくない
---

UMLといってもフロー図とかクラス図とか、何に使うかなので、人それぞれでいいと思います。
構造的に美しいし、書き下した要素が勝手に清書されて図示されるのはキレイかもしれない。
ですが、サーバの設計書や特許文書を書くならともかく、グラフィックスを扱う資料として画像が扱えないのは致命的です。

---

## 実は任意の画像が扱える
---

任意の画像の扱いについて、解説している人がほとんどいないので、使えないのかと思ってしまいましたが、公式ドキュメント「[PlantUML Language Reference Guide (1.2019.9)](http://plantuml.com/en/guide)」p.131「16.6 Legacy HTML」に言及がありました。

---


```legacy.html.pu
@startuml 
:* You can change <color:red>text color</color>
* You can change <back:cadetblue>background color</back>
* You can change <size:18>size</size>
* You use <u>legacy</u> <b>HTML <i>tag</i></b>
* You use <u:red>color</u> <s:green>in HTML</s> <w:#0000FF>tag</w>
----
* Use image : <img:http://plantuml.com/logo3.png>
;
@enduml
```
---

文字色、背景色、サイズ、アンダーライン、打消し線、そして画像も扱えます。

---

![legacyhtml.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/191291/ca36053e-eab7-80d5-4fe5-2225550a3ec0.png)

---
### ここまでの振り返り

私は Google Slides と Github が便利で好きですが、markdownよりも表現力豊かじゃないですか？~~思ったより使えそう~~。
外部画像が読み込めるのがわかったので、これからは素敵なUML図が作れそうです。
→ 多分使わないと思いました。

---

## 棒人間が怖い

それはそれとして、actorの棒人間が嫌なのです。
シャーロックホームズの「[踊る人形](https://www.amazon.co.jp/puikko-%E3%82%B7%E3%83%A3%E3%83%BC%E3%83%AD%E3%83%83%E3%82%AF%E3%83%BB%E3%83%9B%E3%83%BC%E3%83%A0%E3%82%BA%E3%80%8C%E8%B8%8A%E3%82%8B%E4%BA%BA%E5%BD%A2%E3%80%8D-%E3%82%BF%E3%83%88%E3%82%A5%E3%83%BC%E3%82%B7%E3%83%BC%E3%83%AB/dp/B07DS6GH3G/&tag=amazonas-22)」とか怖いのです。

---

### actor が怖くて使えない

PlanerUMLの `actor` なんて特に使えない。色指定しても頭の部分しか変わらないなんて、設計思想的にヤバくないですか？
![htmlcolor.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/191291/d29b2469-bfc7-6760-84c3-045e75c9fadd.png)

---

## そんなことはなかった
調べてみたら[styleぐらいは](https://plantuml.com/ja/style-evolution)つかえるっぽいです。
しかも、けっこう ``<img>`` タグはそこらじゅうで使えるらしく、こんな表現もできました。

```img.pu
@startuml
Alice -> Bob : Testing <img:http://plantuml.com/logo3.png>
@enduml
```
![img.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/191291/2f81c116-6d59-7e0c-428e-8a3d0dd01303.png)

---

つまりTwitterからアイコンを持ってくることもできます。

```icon.pu
@startuml
Qiita: <img:https://qiita-user-profile-images.imgix.net/https%3A%2F%2Fqiita-image-store.s3.amazonaws.com%2F0%2F191291%2Fprofile-images%2F1543316897?ixlib=rb-1.2.2&auto=compress%2Cformat&lossless=0&w=300&s=473a984797eabaff4f6e30dbb74b6a19{scale=0.25}>
Twitter: <img:https://pbs.twimg.com/profile_images/1225373334122070017/llIKo0PH_400x400.jpg{scale=0.2}>
Qiita->Twitter : Kawaii <img:https://upload.wikimedia.org/wikipedia/commons/f/f3/Twitter_icon.png{scale=0.1}>
@enduml

```
![kawaii.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/191291/a46f5956-e177-5fe1-eea3-ead89034acd4.png)

PNG, JPGはURLでロードできました。SVGはエラーになります。URLの後に ``{scale=0.1} `` といった感じで指定してあげれば、（無粋なリニア縮小ですが） サイズ変更もできます。

---

## つまりUMLが無粋な仕様なのではなく
`actor` だけが無粋なのだった。
使う人が画像を読み込むことを一生懸命になっていなかっただけだった…。
（授業とかでUML教えるときは是非、画像も読み込んであげてみてくださいね！）

※`actor`の棒人間を置き換えることができる人は是非おしえてください。

---

# 楽して かわいくしたい
imgタグ使えばできるのはわかったけど、全部のアイコンを置き換えるのはめんどくさいな…。
（矛盾している感じはしますが）
システム設計の要素はかわいく、それでいて楽したい（わかる）。

----

## AWS labsがアイコンを提供している
PlantUMLの公式サイトを読んでいたら、こんなプロジェクトを見つけました。
**[AWS Icons for PlantUML](https://github.com/awslabs/aws-icons-for-plantuml)**
「公式のAWSアーキテクチャアイコンをPlantUMLとC4モデルと組み合わせて、設計、展開、トポロジをコードとして伝えるのに最適な方法です」とあります。


---

### (復習)C4モデルってなんだっけ

![C4モデル](https://c4model.com/img/c4-overview.png)

[C4モデル](https://c4model.com/)とは、コンテキスト（context）、コンテナ（containers）、コンポーネント（components）、コード（code）の略です。いきなりコードから書き始めたい人にとってはアレなんですが、コンテキスト（前後関係、必要性、それぞれの役割） → コンテナ（アプリケーションやAPI、業務単位、サーバシステムやPCなどのハード） → コンポーネント（それぞれの機能の関係性） → コード（具体的な実装、関数、UMLのクラス図）…という抽象関係にあります。

なおPlantUMLでは公式ライブラリとして組み込まれているようです。また元祖としては[Azure-PlantUML](https://github.com/RicardoNiepel/Azure-PlantUML)のほうが先に存在しているようです。


### 実は簡単に include できた

`includeurl`で `.puml`を読み込むのもVS Codeが手伝ってくれるのですが、もっと短く書きたい！と思いました。
どうやら公式で認定されているライブラリはこんな書き方が許されるようです。

```awslib.pu
@startuml AWSを使った練習  
!include <awslib/AWSCommon>
!include <awslib/General/all>
!include <awslib/Storage/all>
!include <awslib/ARVR/all>
rectangle これからのUML(かわいい) {
User(user, "User", "俺", "おひとり様")
Users(users, "Users","Fans" ,"たくさんの仲間")
ARVR(ARVR, "ARVR","VTuber", "ARVRのおかげで")
user->ARVR : 会いたい
ARVR->users : 集合
}
@enduml
```
![korekara.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/191291/6d6f4dd3-f3e3-16fe-64c3-0a811f08b280.png)

---
### AWSSimplified

個人的には
 ```!includeurl AWSPuml/AWSSimplified.puml```
 を宣言することで、同じUMLがよりシンプルに描画される機能が気に入りました。

ここまででもだいぶ*かわいく*なりましたが、`AWSSimplified`を使って同じコードをさらにシンプルにしてみます。
ついでにStorageも使わないので削っていきます。

```awsSimplified.pu
@startuml AWSを使った練習
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified>
!include <awslib/General/all>
!include <awslib/ARVR/all>
rectangle これからのUML(かわいい) {
User(user, "User", "俺", "おひとり様")
Users(users, "Users","Fans" ,"たくさんの仲間")
ARVR(ARVR, "ARVR","VTuber", "ARVRのおかげで")
user->ARVR : 会いたい
ARVR->users : 集合
}
@enduml
```

---


### Azure-PlantML
Azureっぽいかっこいいアイコンたち

![Azure-PlantUML](https://camo.githubusercontent.com/c20ef77b7ff1743dcea1ac2d777635e87844ccc6/687474703a2f2f7777772e706c616e74756d6c2e636f6d2f706c616e74756d6c2f70726f78793f6964783d30267372633d68747470732533412532462532467261772e67697468756275736572636f6e74656e742e636f6d2532465269636172646f4e696570656c253246417a7572652d506c616e74554d4c2532466d617374657225324673616d706c657325324642617369632532353230757361676525323532302d253235323053747265616d253235323070726f63657373696e672532353230776974682532353230417a757265253235323053747265616d2532353230416e616c79746963732e70756d6c)

（ただし かわいいユーザ に使える スプライトはありませんでした）
Azureはかっこいいし使っていきたいけど、とりあえず提案書を書く時のユーザ関係の処理、つまりC4モデルにおけるコンテキストを整理したいので、ユーザアイコンは必須なんですよね…。

---

# AWS Symbols を使う(更新が止まっているようです)

公式ドキュメントの[サンプル](https://github.com/awslabs/aws-icons-for-plantuml#basic-usage)はこんな感じです。

```
@startuml Basic Usage - AWS IoT Rules Engine

!define AWSPuml https://raw.githubusercontent.com/awslabs/aws-icons-for-plantuml/master/dist
!includeurl AWSPuml/AWSCommon.puml
!includeurl AWSPuml/InternetOfThings/IoTRule.puml
!includeurl AWSPuml/InternetOfThings/IoTAction.puml
!includeurl AWSPuml/Analytics/KinesisDataStreams.puml
!includeurl AWSPuml/ApplicationIntegration/SimpleQueueServiceSQS.puml

left to right direction

agent "Published Event" as event #fff

IoTRule(iotRule, "Action Error Rule", "error if Kinesis fails")
KinesisDataStreams(eventStream, "IoT Events", "2 shards")
SimpleQueueServiceSQS(errorQueue, "Rule Error Queue", "failed Rule actions")

event --> iotRule : JSON message
iotRule --> eventStream : messages
iotRule --> errorQueue : Failed action message

@enduml
```
![出力結果](https://camo.githubusercontent.com/34d258b039d1a2eb420f6be54ceb9dd60516b452/687474703a2f2f7777772e706c616e74756d6c2e636f6d2f706c616e74756d6c2f70726f78793f6964783d30267372633d68747470732533412532462532467261772e67697468756275736572636f6e74656e742e636f6d2532466177736c6162732532466177732d69636f6e732d666f722d706c616e74756d6c2532466d61737465722532466578616d706c65732532464261736963253235323055736167652e70756d6c)

もう一見して何を書いているのか、UMLなのかもわかんない感じですが、カッコいいAWS資料っぽい図ができました。すごい。

### (資料)全アイコン集
PlantUMLで使える全アイコンのリスト
https://github.com/awslabs/aws-icons-for-plantuml/blob/master/AWSSymbols.md

そもそものAWSアーキテクチャのアイコン集
https://aws.amazon.com/jp/architecture/icons/

まずは普段使いで使いそうなアイコン名を探してきましょう。

## (更新)Azureもなかなかいい
[https://github.com/plantuml-stdlib/Azure-PlantUML](https://github.com/plantuml-stdlib/Azure-PlantUML)

```

@startuml
!pragma revision 1

!includeurl https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

!define AzurePuml https://raw.githubusercontent.com/plantuml-stdlib/Azure-PlantUML/master/dist
!includeurl AzurePuml/AzureCommon.puml
!includeurl AzurePuml/AzureC4Integration.puml
!includeurl AzurePuml/Databases/AzureRedisCache.puml
!includeurl AzurePuml/Databases/AzureCosmosDb.puml
!includeurl AzurePuml/Databases/AzureSqlDatabase.puml
!includeurl AzurePuml/Web/AzureWebApp.puml
!includeurl AzurePuml/Web/AzureCDN.puml
!includeurl AzurePuml/Web/AzureSearch.puml
!includeurl AzurePuml/Storage/AzureBlobStorage.puml
!includeurl AzurePuml/Storage/AzureQueueStorage.puml

LAYOUT_WITH_LEGEND()

Person(user, "User")

Container(spa, "Single-Page App", "Angular, JS")
AzureWebApp(webApp, "Web & API App", "ASP.NET Core MVC 2.1, C#", "Delivers the SPA and provides RESTful web APIs which are consumed from the SPA")
AzureCDN(cdn, "CDN", "Akamai S2", "caches publicly available content for lower latency and faster delivery of content")

AzureBlobStorage(staticBlobStorage, "Static Content", "General Purpose v2, Hot, LRS")

AzureQueueStorage(queue, "Queue", "General Purpose v2, LRS")
AzureSearch(search, "Search Index", "Standard S1", "provides search suggestions, fuzzy search, and language-specific search, consolidates a single search index from multiple data stores")
AzureRedisCache(redisCache, "Cache", "Standard C2")

AzureCosmosDb(cosmosDb, "Document DB", "SQL API, 400 RUs")
AzureSqlDatabase(sqlDb, "SQL DB", "Standard S3")

AzureWebApp(webJob, "Web Job", "WebJobs SDK v3, C#", "runs long-running tasks in the background")

Rel(user, spa, "Uses", "HTTPS")
Rel(user, webApp, "Uses", "HTTPS")
Rel(user, cdn, "Uses", "HTTPS")

Rel_Neighbor(spa, webApp, "Uses", "JSON, HTTPS")
Rel_Back_Neighbor(spa, webApp, "Delivers")

Rel_Neighbor(cdn, staticBlobStorage, "Reads from")

Rel(webApp, queue, "Puts background jobs into")
Rel(webApp, sqlDb, "Reads from and writes to", "ADO.NET")
Rel(webApp, cosmosDb, "Reads from and writes to", "SQL API")
Rel(webApp, redisCache, "Reads from and writes to")
Rel(webApp, search, "Reads from")

Rel_U(webJob, queue, "Gets next job from")
Rel_U(webJob, sqlDb, "Reads from and writes to", "ADO.NET")
Rel_U(webJob, cosmosDb, "Reads from and writes to", "SQL API")
Rel_U(webJob, redisCache, "Reads from and writes to")

Rel_Back_Neighbor(cosmosDb, search, "Builds index from")
Rel_Neighbor(search, sqlDb, "Builds index from")

Lay_D(search, webJob)

@enduml
```

## PlantUML Standard Library

[Unofficial PlantUML Standard Library Repositories](https://github.com/plantuml-stdlib/)

---

---

だいぶ短くてかわいくなりました。

![korekara2.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/191291/d52b5469-a32b-8a64-db84-b1fd86367b2e.png)

---
# どうやって実装されているの？

ちなみに `User()` はマクロで実装された component ぽいのですが、

```
component "俺" as user2
user: <img:http://plantuml.com/logo3.png>
```
と書いてもエラーにしかなりませんでした。
[ソース](https://github.com/awslabs/aws-icons-for-plantuml/blob/master/dist/AWSRaw.puml)を読んでみると

```
!definelong AWSEntity(e_alias, e_label, e_techn, e_color, e_sprite, e_stereo)
rectangle "==e_label\n<color:e_color><$e_sprite></color>\n//<size:TECHN_FONT_SIZE>[e_techn]</size>//" <<e_stereo>> as e_alias
!enddefinelong
```
という感じでe_spriteとして埋め込んでいます。色指定はできますが画像データそのものはエンコードされているようです。
後学のために任意のスプライト埋め込みについての [PlantUMLの仕様](https://plantuml.com/ja/sprite)を引用しておきます。


```Defining_and_using_Sprites.pu
@startuml
sprite $foo1 {
  FFFFFFFFFFFFFFF
  F0123456789ABCF
  F0123456789ABCF
  F0123456789ABCF
  F0123456789ABCF
  F0123456789ABCF
  F0123456789ABCF
  F0123456789ABCF
  F0123456789ABCF
  FFFFFFFFFFFFFFF
}
Alice -> Bob : Testing <$foo1{scale=3}>
@enduml
```

こんな風に出力されます。
![Defining and using sprites](https://s.plantuml.com/imgw/sprite-sw2ky19k.png)

（ネタバレ）ここまでソース解析してみて、やっと前半に解説していた<img>の使い方が分かった次第です。
日本語でここまで解説したドキュメントもないし、画像使いこなしたUML図も出てこないから遠回りしてしまいました。

---

### ちなみに
いろいろインストールすることなくブラウザ上でPlantUMLをコンパイルする環境もあります。
https://plantuml-editor.kkeisuke.com/

ここまで紹介したスクリプトも動きました。
![webeditor.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/191291/e7017b08-8904-fa6b-8cb7-512d8e78aa6b.png)

こちらに作者さんの解説記事がありました。

・[vue-cli (vuex) で PlantUML エディターを作ってみた](https://qiita.com/kkeisuke/items/45f4725d41dd789061a2)

---


# 最後まで読んでいただき ありがとうございました

以上、正直UMLは食わず嫌いだったのですが、やってみればできた。見た目が変わるって大事ですよね～。
という発見がいろいろありましたのでまとめておきました。

役に立った！こんな使い方できたよ！というコメントや加筆など歓迎です。


# 後日談(2020/3/16)

この記事を読んだ[GREE VR Studio Lab](https://vr.gree.net/lab/)のインターンKさんが、さらに魔改造を進めてくれましたので紹介します。
![kawaii-PlantUML.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/191291/f7f1f124-9dbf-2acc-9b13-53dad8b56688.png)


```
@startuml

'一行コメント

/'
複数行コメント
'/

'allow_mixingを使うとクラス図とユースケース図の共存が可能
allow_mixing

'methodを非表示
hide members
show fields

rectangle クラス図を魔改造してかわいくなった{
  /'classの内部にあるものはプロパティとメソッドに自動で分けられ、
  class_name
  property（画像など'()'がついてないものはこちら）
  method()
  上のように分割される
  '/
  class カワボちゃん <<vtuber>>{
    <img:https://vr.gree.net/lab/vc/img/10.768c4c29.png{scale=0.3}>
    ファンネーム
    ・カワとも
    得意
    ・ボイチェン
  }

  'class を非表示代わりに<<ステレオタイプ>>が表示されてしまう
  hide <<vtuber>> circle
  show <<vtuber>> fields

  '以下でステレオタイプも消せる
  hide <<vtuber>> stereotype
  /'allow_mixingで使えるようになったがusecaseを使って宣言する必要がある
  (sing)はだめ
  '/
  usecase speak <<ing>>
  カワボちゃん  -- speak
  usecase dance <<after>>
  カワボちゃん -- dance
  usecase sing <<before>>
  カワボちゃん -- sing

  /'ノート（コメント的な）が使える
  対象
  note 場所: 内容
  '/
  class カワボちゃん
  note right: 「転声こえうらない」\n（https://vr.gree.net/lab/vc）より
  usecase sing
  note top : クラス図中でもusecase要素が使えます

}

/'色の変換が行える
色によって時間の区別や強調等が行える
'/
skinparam usecase {
	BackgroundColor<<before>> powderblue
	BorderColor slateblue

	BackgroundColor<< ing >> darkseagreen
	BorderColor<< ing >> DarkSlateGray

  BackgroundColor<< after >> darksalmon
	BorderColor<< after >> maroon
}
hide <<before>> stereotype
hide <<ing>> stereotype
hide <<after>> stereotype

@enduml
```

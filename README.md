# PlantUML-Study

## PlantUMLの勉強のためのリポジトリです。

## 準備するもの

* Visual Studio Code
* [GraphViz 2.38](https://www.graphviz.org/)
* [PlantUML Visual Studio Code Extention](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml)

## 使い方

[サンプルファイル](Class-Usecase.md)を用意しておきました。
GraphVizとPlantUML機能拡張がインストールされていれば、
Visual Studio内では `Alt + D` で画像生成されます。

![サンプルファイルのレンダリング結果](https://github.com/kaitas/PlantUML-Study/blob/images/kawaiiPlantUML.png?raw=true "サンプル画像のレンダリング結果")

## 詳細ドキュメント

Qiita記事を書いておきました

[https://qiita.com/drafts/c955e29c1638efafc5eb/](https://qiita.com/drafts/c955e29c1638efafc5eb/)

なおPlantUML、記事中の拡張子は `.pu` ですが、中身はテキストです。


## PlantUML Viewer  (Chrome機能拡張)
Chrome機能拡張[PlantUML Viewer](https://chrome.google.com/webstore/detail/plantuml-viewer/legbfeljfbjgfifnkmpoajgpgejojooj?hl=en)をインストールすると `.md` 内でも画像化することができます。

下にサンプルコードがあります。上記の機能拡張がインストールされていると、自動で画像化されているはずです。

### サンプルコード
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

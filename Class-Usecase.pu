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
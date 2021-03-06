![](../_media/top_image.png)


# 使用方法

## 既存のPlantUML fileを認識させる

拡張子を元の `puml` や `pu` から本プラグインの拡張子に変更してください。

本プラグインの拡張子は図ごとに定義されていて、例えばクラス図の場合は `puclass` , シーケンス図の場合は `pusequence` です。
下記の表に対応している全ての図の拡張子を記載しています。

## 新しくfileを作る

ファイル作成時の形式の選択を本プラグインのアイコンが付いた `PlantUML File` か各ダイアグラムごとの形式を選択してください。(ex: PlantUML Class)

# PlantUML各図の対応状況
PlantUMLの公式サイトに掲載されている全ての図を順次対応していく予定です。
直近では2020/09/16にtiming図のサポートをリリースしました。

| Diagram type        | Supported | Extension           | Original diagram type |
| ------------- |:-:|:-------------:| :-----:|
| [sequence](https://plantuml.com/en/sequence-diagram)| o | pusequence | - |
| [usecase](https://plantuml.com/en/use-case-diagram)| o | puusecase | - |
| [class](https://plantuml.com/en/class-diagram)| o | puclass | - |
| [activity](https://plantuml.com/en/activity-diagram-beta)| o | puactivity | - |
| [component](https://plantuml.com/en/component-diagram)| o | pucomponent | usecase |
| [state](https://plantuml.com/en/state-diagram)| o | pustate | - |
| [object](https://plantuml.com/en/object-diagram)| o | puobject | class |
| [deployment](https://plantuml.com/en/deployment-diagram)| o | pudeployment | usecase |
| [timing](https://plantuml.com/en/timing-diagram)| o | putiming | - |
| [network](https://plantuml.com/en/nwdiag)| o | punetwork | - |
| [wireframe](https://plantuml.com/en/salt)| not yet | - | - |
| [archmate](https://plantuml.com/en/archimate-diagram)| not yet | - | - |
| [gantt](https://plantuml.com/en/gantt-diagram)| not yet | - | - |
| [mindmap](https://plantuml.com/en/mindmap-diagram)| not yet | - | - |
| [WBS](https://plantuml.com/en/wbs-diagram)| not yet | - | - |


※ activity図は[新バージョン](https://plantuml.com/en/activity-diagram-beta)のみ対応しています。

※ 「Original diagram typeとは？」 図の種類は別でも構文は同じものを使用している図があります。その場合に元の図を "Original diagram type" として表しています。

（例えばobject図はclass図と同じ構文なので、object図の "Original diagram type" はclassになっています）


# ファイル種別と拡張子について

PlantUMLは全ての図を同じファイル形式（pumlやplantuml）で表現できますが、PlantUML Studioではきちんと構文をサポートするために、それぞれ図を別のファイル形式（別の言語）として扱っています。

この方式によって、既存の運用との整合性が取りづらくなってしまったり、他のツールとの連携が難しくなったりするケースが考えられますが、きちんと構文をサポートすることがこのプラグインの価値の主なところと思いまして、こういった形をとっています。

---


# markdown内の機能

コードブロックの言語に`puclass`のような本プラグインの形式を指定するとエディター機能が使用できます。
図を描画させるためには、コードブロックの言語に`puml`を指定し、
Preferencesの「Languages & Frameworks」>「Markdown」>「Plantuml   isn't installed -> install」の所からPlantUmlをインストールすることで、プレビュー画面に図がレンダリングされるようになります。

![](../_media/markdown_preference.png)


---


# File list viewer

プロジェクト内にあるPlantUML Studio形式のファイルが一覧で表示され、ファイルを選択すると図を閲覧することができます。

## Sort

デフォルトでは更新日時が新しい順にソートされていて、下記のボタンを押すことでソート方式を変更できます。
- ![](../_media/file_list_viewer/sort_by_name.png) 名前順
- ![](../_media/file_list_viewer/sort_by_file_type.png) 図の種類ごと


## Others

ファイルリストをダブルクリックするとそのファイルを開くことができます。

---


# 設定

Tool windowのツールバーにある ![](/_media/tool_icon.png)  ボタンから各種設定が行えます。

## Tool Window

### Auto Render Diagram

開いているPlantUMLのコードが変更された場合に自動的に図を更新するかどうかの設定です。

### Auto Show Tool Window

PlantUML STUDIO形式のファイルを開いた際に自動的にTool windowを開くかどうかの設定です。

### Auto Hide Tool Window

PlantUML STUDIO形式のファイルを開いている状態で、それ以外のファイルを開いた際に自動的にTool windowを閉じるかどうかの設定です。


## Tools Panel

### Delay between typing and rendering(ms)

PlantUMLのコードが変更されてから図が更新されるまでの遅延時間（ミリ秒）の設定です。

### Graphviz dot executable

PlantUMLは[Graphviz](https://graphviz.org/)のdotコマンドに依存しています。
デフォルトではpathが通っている場所に配置されているものを使用しますが、任意のものを指定したい場合はこの設定で指定することができます。


### PlantUML config(equivalent of cmd param '-config config.txt')

図を描画する際に `@startuml` の直後に入れ込むコードを指定できます。
skinparamで全ての図のスタイルを調整するなどの用途に利用できます。

### Enable the diagram rendering feature in markdown (※ since version 2020.2.3)

markdown内のコードブロックに `puml`, `plantuml`, `puclass形式`を指定した際に、プレビュー画面に図を描画するかの設定です。


# 各図の対応状況
PlantUMLの公式サイトに掲載されている全ての図を順次対応していく予定です。
直近では2020/08/20にnetwork図とdeployment図のサポートをリリースしました。

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
| [timing](https://plantuml.com/en/timing-diagram)| not yet | - | - |
| [network](https://plantuml.com/en/nwdiag)| o | punetwork | - |
| [wireframe](https://plantuml.com/en/salt)| noet yet | - | - |
| [archmate](https://plantuml.com/en/archimate-diagram)| noet yet | - | - |
| [gantt](https://plantuml.com/en/gantt-diagram)| noet yet | - | - |
| [mindmap](https://plantuml.com/en/mindmap-diagram)| noet yet | - | - |
| [WBS](https://plantuml.com/en/wbs-diagram)| noet yet | - | - |


※ activity図は[新バージョン](https://plantuml.com/en/activity-diagram-beta)のみ対応しています。

※ 「Original diagram typeとは？」 図の種類は別でも構文は同じものを使用している図があります。その場合に元の図を "Original diagram type" として表しています。

（例えばobject図はclass図と同じ構文なので、object図の "Original diagram type" はclassになっています）


# ファイル種別と拡張子について

PlantUMLは全ての図を同じファイル形式（pumlやplantuml）で表現できますが、PlantUML Studioではきちんと構文をサポートするために、それぞれ図を別のファイル形式（別の言語）として扱っています。

この方式によって、既存の運用との整合性が取りづらくなってしまったり、他のツールとの連携が難しくなったりするケースが考えられますが、きちんと構文をサポートすることがこのプラグインの価値の主なところと思いまして、こういった形をとっています。


# markdown内の機能について

※ 以後、 `puclass` や `pusequence` などの本プラグイン独自の拡張子を `puclass形式` と表現しています。

プラグインからのmarkdown表示部分のカスタマイズがIntelliJ IDEのバージョン2020.2から可能になったため、2020.2以前では限定的なサポートとなっています。

## 2020.2.3以降の機能

- `puml`, `plantuml`, `puclass形式`のいずれの指定でも図が表示される
- `puclass形式`の指定でエディター機能が使用できる

標準的な指定である `puml`, `plantuml` ではエディター機能が使えないため、編集する際のみ puclass形式に変更するのがお勧めです。


## 2020.2.2以前の機能

- `puclass形式`の指定でエディター機能が使用できる
  - ただし、`puobjec`tや`pucomponent`などのオリジナルの構文を持っていない図は指定できない。（上記の表を参考に、オリジナルの図を指定していただければと思います。）



# file list viewerについて

プロジェクト内にあるPlantUML Studio形式のファイルが一覧で表示され、ファイルを選択すると図を閲覧することができます。

## ソート機能

デフォルトでは更新日時が新しい順にソートされていて、下記のボタンを押すことでソート方式を変更できます。
- <img src='/_media/file_list_viewer/sort_by_name.png' alt='sort by name button' /> 名前順
- <img src='/_media/file_list_viewer/sort_by_file_type.png' alt='sort by file type button' /> 図の種類ごと


## その他

ファイルリストをダブルクリックするとそのファイルを開くことができます。


# 設定

Tool windowのツールバーにある <img src='/_media/tool_icon.png' alt='tool icon' />  ボタンから各種設定が行えます。

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
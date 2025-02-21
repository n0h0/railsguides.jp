Ruby on Rails のメンテナンスポリシー
====================================

Railsフレームワークのサポートは、新機能（New feature）、バグ修正（bug fixes）、セキュリティ問題（security issues）、重大なセキュリティ問題（severe security issue）の4つのグループに分かれています。セキュリティリリースを除いて、すべてのバージョン表記は`X.Y.Z`の形式に従います。

--------------------------------------------------------------------------------


Railsのバージョン命名は[semver](http://semver.org/)のSemantic Versioningをシフトしたものに従っています。

**パッチ`Z`**

このパッチではバグ修正のみを行います。API変更や機能追加はこのパッチでは行いません。ただし、必要に応じてセキュリティ修正が行われることもあります。

**マイナー`Y`**

新機能にAPIの変更が含まれることもあります（Semverで言うメジャーバージョンに相当）。破壊的変更（breaking changes）の場合は、必ず事前にマイナーリリースまたはメジャーリリースで非推奨通知を行います。

**メジャー`X`**

新機能にAPIの変更も含まれる可能性が高まります。Railsにおけるマイナーリリースとメジャーリリースの違いは、破壊的変更の大きさの違いであり、通常は特別な場合にのみ行われます。

新機能
------------

新機能はmainブランチにのみ追加されます。ポイントリリース（=Railsの場合はパッチリリース）で新機能を追加することはありません。

バグ修正
---------

バグ修正は最新リリースのシリーズにのみ適用されます。通常、バグ修正はmainブランチに追加され、必要であればx-y-stableブランチにバックポートされます。
十分な数のバグ修正がx-y-stableブランチに追加されると、そのブランチから新しいパッチリリースがビルドされます。
たとえば、1.2.2パッチは理論上1-2-stableブランチからビルドされます。

特殊な状況として、サポート対象となるシリーズを拡大することにCore Teamメンバーの誰かが賛成した場合は、それらはサポート対象のシリーズに追加されます。

**現在対象となっているシリーズ:** `7.0.Z`。

セキュリティ問題
---------------

現在のリリースシリーズ、および１つ前のリリースシリーズには、セキュリティ問題発生時にパッチや新バージョンが提供されます。

これらのリリースは、直近にリリースされたバージョンにセキュリティパッチを適用してリリースされます。続いて、それらのパッチはx-y-stable（安定版）ブランチの最後に適用されます。たとえば、1.2.3というセキュリティリリースは、理論上1.2.2を元にビルドされ、1-2-stableの最後に追加されます。つまり、最新のRailsを利用していればセキュリティリリースへのアップグレードを容易に行えます。

セキュリティリリースには、直接的なセキュリティパッチ（修正プログラム）のみが含まれます。セキュリティパッチが原因で発生したセキュリティと無関係なバグの修正は、リリースのx-y-stableブランチで公開され、バグ修正ポリシーに基づいて新しいgemとしてのみリリースされます。

**現在対象となっているシリーズ:** `7.0.Z`、`6.1.Z`。

重大なセキュリティ問題
----------------------

重大なセキュリティ問題については、最新のメジャーなシリーズにおけるすべてのリリースと、前回のメジャーなシリーズの最新リリースに対してセキュリティパッチと新バージョンを提供します。セキュリティ問題の重大性の判定はコアチームによって行われます。

**現在対象となっているシリーズ:** `7.0.Z`、`6.1.Z`。

サポート対象外となるリリースシリーズ
--------------------------

あるリリースシリーズがサポート対象外になった場合、バグ修正とセキュリティ問題の対応は各自の責任となります。場合によっては修正のバックポートの提供とgitへの公開が行われる可能性もありますが、新バージョンがリリースされることはありません。アプリケーションで使われているバージョンのメンテナンスが難しい場合は、サポート対象のバージョンにアップグレードしてください。

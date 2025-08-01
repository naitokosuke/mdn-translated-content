---
title: Django の紹介
slug: Learn_web_development/Extensions/Server-side/Django/Introduction
original_slug: Learn/Server-side/Django/Introduction
l10n:
  sourceCommit: 904cdf09c7e328b7a15a6a4db6bc6bd31f969cce
---

{{LearnSidebar}}{{NextMenu("Learn/Server-side/Django/development_environment", "Learn/Server-side/Django")}}

この最初の Django の記事では、「Django とは何か」 という問いに答え、このウェブフレームワークの特徴と概要を説明します。

ここでは、このモジュールで詳しく説明する時間がない高度な機能を含む、主な機能の概要を説明します。また、Django アプリケーションの主要な構成要素をいくつか紹介します（ただし、この時点ではまだテストするための開発 環境は持っていないでしょう）。

<table>
  <tbody>
    <tr>
      <th scope="row">前提条件:</th>
      <td>
        基本的なコンピューターリテラシー。
       <a href="/ja/docs/Learn/Server-side/First_steps">サーバーサイドのウェブサイトプログラミング</a>の一般的な理解、特に、<a href="/ja/docs/Learn/Server-side/First_steps/Client-Server_overview">ウェブサイトにおけるクライアントとサーバーとのやり取り</a>の仕組みを理解していること。
      </td>
    </tr>
    <tr>
      <th scope="row">目標:</th>
      <td>
        Django とは何か、艇庫湯する機能、 Django アプリケーションの主要要素に精通すること。
      </td>
    </tr>
  </tbody>
</table>

## Django とは何か

Django は高水準の Python のウェブフレームワークで、安全で保守可能なウェブサイトを迅速に開発することができます。経験豊富な開発者によって作られた Django は、ウェブ開発の面倒な部分の多くを引き受けるので、車輪を再発明する必要なく、アプリを書くことに集中することができます。Django はフリーでオープンソースであり、活発なコミュニティと素晴らしいドキュメントがあり、フリーと有償のサポートがあります。

Django は次のようなソフトウェアを書くのに役立ちます。

- 完全性
  - : Django は「電池入り」の哲学に従い、開発者が「箱から出して」やりたいことはほとんどすべて提供しています。必要なもの全てが一つの「製品」の一部であるため、全てがシームレスに連動し、一貫した設計原理に従っており、広範で[最新のドキュメント](https://docs.djangoproject.com/en/stable/)が備わっています。
- 多様性
  - : Django は、コンテンツマネジメントシステムや Wiki からソーシャルネットワークやニュースサイトまで、ほとんど全てのタイプのウェブサイトを構築するのに使うことができます（そしてこれまでも使ってきました）。どんなクライアントサイドフレームワークでも動作し、ほとんどどんな形式のコンテンツでも配信できます（HTML、RSS フィード、JSON、XML を含む）。

    内部的には、必要となるほとんどの機能（人気のあるデータベースやテンプレートエンジンなど）の選択肢を提供していますが、他のコンポーネントを使用するように拡張もできます。

- 安全性
  - : Django は、ウェブサイトを自動的に保護するために「正しいことをする」ように設計されたフレームワークです。多くの一般的なセキュリティミスを開発者が避けるのに役立ちます。 Django はユーザーアカウントとパスワードを安全に管理する方法を提供しており、セッション情報を脆弱なクッキーに入れたり（代わりにクッキーにはキーを入れるだけで、実際のデータはデータベースに保存されます）、パスワードハッシュではなくパスワードを直接保存するなどのよくある間違いを回避しています。

    _パスワードハッシュは、送信されたパスワードから [暗号化ハッシュ関数](https://ja.wikipedia.org/wiki/%E6%9A%97%E5%8F%B7%E5%AD%A6%E7%9A%84%E3%83%8F%E3%83%83%E3%82%B7%E3%83%A5%E9%96%A2%E6%95%B0)を介して生成された固定長の値です。 Django は入力されたパスワードが正しいかどうかを、ハッシュ関数を介した値と保存されたハッシュ値を比較することでチェックできます。これは「一方向性」の機能であり、もし保存されているハッシュ値が侵害されても、攻撃者が元のパスワードを解読するのは困難です。_

    Django は、SQL インジェクション、クロスサイトスクリプティング (XSS)、クロスサイトリクエストフォージェリー (CSRF)、[クリックジャッキング](/ja/docs/Web/Security/Attacks/Clickjacking)などの多くの脆弱性に対する保護が有効です（これらの攻撃についての詳細は、[ウェブサイトのセキュリティ](/ja/docs/Learn_web_development/Extensions/Server-side/First_steps/Website_security)を参照してください）。

- スケーラブル
  - : Django はコンポーネントベースの「[シェアードナッシング](https://ja.wikipedia.org/wiki/%E3%82%B7%E3%82%A7%E3%82%A2%E3%83%BC%E3%83%89%E3%83%BB%E3%83%8A%E3%83%83%E3%82%B7%E3%83%B3%E3%82%B0%E3%83%BB%E3%82%A2%E3%83%BC%E3%82%AD%E3%83%86%E3%82%AF%E3%83%81%E3%83%A3)」アーキテクチャを採用しています（アーキテクチャの各部分は他と独立しており、必要に応じて置き換え、変更できます）。異なる部分を明確に分離しているため、キャッシュサーバー、データベースサーバー、アプリケーションサーバーの各ハードウェアをそれぞれ追加することによって、トラフィックの増加に合わせてスケールできるようになっています。いくつかの最も忙しいサイトは、ニーズを満たすために Django を適切にスケールさせています（Instagram や Disqus など）
- メンテナンス可能
  - : Django のコードは、保守可能で再利用可能になるような設計原則、デザインパターンを使って書かれています。特に、Do not Repeat Yourself (DRY) 原則によって不要な複製がなく、コード量を削減します。Django は、関連する機能を再利用可能な「アプリケーション」にグループ化し、低いレベルでは関連するコードをモジュールにグループ化します（[モデルビューコントローラー (MVC)](/ja/docs/Glossary/MVC) パターンに沿っています）。
- ポータブル
  - : Django のコードは多くのプラットフォームで動作する Python で書かれています。これはプラットフォームに縛られないことを意味します。アプリケーションは多くの種類の Linux、Windows、macOS で実行することができます。さらに、 Django は多くのウェブホスティングプロバイダーが広く対応しており、しばしば Django のサイトをホスティングするための特定のインフラとドキュメントが提供されています。

## どこから来たの？

Django は当初、2003 年から 2005 年の間に、新聞のウェブサイトの作成とメンテナンスを担当するウェブチームによって開発されました。いくつかのサイトを作成した後、チームは多くの共通コードとデザインパターンを除外、再利用するようになりました。この共通コードは、"Django" プロジェクトとして 2005 年 7 月にオープンソース化され、汎用のウェブ開発フレームワークに発展しました。

Django は、2008 年 9 月の最初のマイルストーンリリース (1.0) から、最新のリリースバージョンである 4.0 (2022) まで、成長を続けています。 各リリースでは、新しい種類のデータベース、テンプレートエンジン、キャッシュのサポートから、「汎用」ビュー機能とクラスの追加（プログラミングタスクで開発者が記述しなければならないコード量を削減します）などの新機能追加やバグフィックスがありました。

> [!NOTE]
> Django のウェブサイトの[リリースノート](https://docs.djangoproject.com/en/stable/releases/)をチェックして、最近のバージョンで何が変わったのか、どのような作業が Django を改善しているのか確認してください。

Django は現在、活発なオープンソースプロジェクトであり、何千人ものユーザーと協力者がいます。元々の起源に関連するいくつかの機能はまだありますが、Django はあらゆる種類のウェブサイトを開発できる汎用フレームワークに進化しました。

## Django はどれくらい普及していますか？

サーバーサイドのフレームワークの普及率を決定的に測定する、すぐに利用できるものはありません （[Hot Frameworks](http://hotframeworks.com/) のようなサイトでは、GitHub プロジェクトの数や、各プラットフォームの StackOverflow の質問数をカウントするなどのメカニズムを使用して人気を評価しています） より良い質問は、「人気のないプラットフォームで問題を避けるために、Django は "人気がある" かどうか」、「それは進化し続けていますか？」「必要なときに助けを得ることができますか？」「Django を学べば、仕事を得る機会がありますか？」などです。

Django を使用している有名なサイトの数、コードベースに協力する人数、無料と有料の両方でサポートを提供する人数に基づけば、Django は普及しているフレームワークと言えるでしょう。

Django を使用している有名なサイトは、Disqus、Instagram、Knight Foundation、MacArthur Foundation、Mozilla、National Geographic、Open Knowledge Foundation、Pinterest、Open Stack などです（ソース: [Django ホームページ](https://www.djangoproject.com/)）

## Django はこだわりが強いですか?

ウェブフレームワークは、自身を「こだわりが強い (opinioned)」か「こだわりが強くない」と呼ぶことがあります。

こだわりが強いフレームワークは、特定のタスクを処理するための「正しい方法」についてこだわりを持っています。特定の分野（特定の種類の問題の解決）は、どのように扱うと正しいか、広く知られており、文書化もされているため、迅速な開発をサポートします。 しかし、主要分野以外の問題解決において柔軟性を欠き、使用できるコンポーネントのやアプローチの選択肢が少なくなる傾向があります。

対照的に、こだわりの強くないフレームワークは、目的を達成するための最善の結合されたコンポーネントの提供や、使用するコンポーネントを制限することが非常に少ないです。開発者は、特定のタスクを完了するために最も適したツールを簡単に使用できます。ただし、それらのコンポーネントを自分で見つける必要があります。

Django は「いくらかこだわりがある」ので、「両方の世界のベスト」を提供します。 ほとんどのウェブ開発タスクを処理するための一連のコンポーネントと、それを使う 1 つ（または 2 つ）の正しい方法を提供します。Django の分離アーキテクチャでは、通常、さまざまなオプションから選択しますが、必要に応じて新しいオプションを追加できます。

## Django コードはどのように見えますか?

昔ながらのデータ駆動型ウェブサイトでは、ウェブアプリケーションはウェブブラウザー（または他のクライアント）からの HTTP リクエストを待ちます。リクエストを受信すると、アプリケーションは、URL および、`GET` や `POST` データの情報に基づいて必要な処理を行います。 必要に応じてデータベースの情報を読み書きしたり、要求を満たすために必要なタスクを実行できます。 アプリケーションはウェブブラウザーにレスポンスを返す際、検索したデータを HTML テンプレートのプレースホルダーに挿入し、動的に HTML ページを生成することがよくあります。

Django のウェブアプリケーションは、通常、これらの各ステップを処理するコードを別々のファイルにグループ化します。

![Django - ビューとモデルのファイル、URL、テンプレート](basic-django.png)

- **URL:** 単一 URL から単一の関数を介してすべてのリクエストを処理することは可能ですが、各リソースを処理する別々のビュー関数を作成する方がはるかにメンテナンスが容易です。 URL マッパーは、URL に基づいて HTTP リクエストを適切なビューにリダイレクトするために使われます。 URL マッパーは、URL に含まれる特定のパターンの文字列または数字を照合し、これらをデータとしてビュー関数に渡すこともできます。
- **ビュー:** ビューは、HTTP リクエストを受け取り、HTTP レスポンスを返すリクエストハンドラー関数です。ビューは、モデルを介してリクエストを満たすために必要なデータにアクセスし、レスポンスのフォーマットをテンプレートに委任します。
- **モデル:** モデルは、アプリケーションのデータ構造を定義し、データベース内のレコードを管理（追加、変更、削除）および照会するための機能を提供する Python オブジェクトです。
- **テンプレート:** テンプレートは、ファイルの構造やレイアウト（HTML ページなど）を定義するテキストファイルで、プレースホルダーを使用して実際のコンテンツを表します。 ビューは、モデルから取得したデータと HTML テンプレートを使用して動的に HTML ページを作成できます。 テンプレートを使用して、あらゆる種類のファイル（HTML である必要はありません!）の構造を定義できます。

> [!NOTE]
> Django はこの構成を「モデルビューテンプレート (Model View Template, MVT)」アーキテクチャと呼んでいます。これは[ビューモデルコントローラー (MVC)](/ja/docs/Glossary/MVC) アーキテクチャとよく似ています。

以下の節は、Django アプリのこれらの主要な部分がどのようなものかを示すものです（コースの後半で開発環境を整えた後、より詳しく説明します）。

### リクエストを正しいビューに送信する (urls.py)

URL マッパーは通常、 **urls.py** という名前のファイルに格納されます。以下の例では、マッパー (`urlpatterns`) はルート（特定の URL パターン） と対応するビュー関数のマッピングのリストを定義します。
指定されたパターンと一致する URL を持つ HTTP リクエストが受信されると、関連するビュー関数が呼び出され、リクエストを渡します。

```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('book/<int:id>/', views.book_detail, name='book_detail'),
    path('catalog/', include('catalog.urls')),
    re_path(r'^([0-9]+)/$', views.best),
]
```

`urlpatterns`オブジェクトは`path()`や`re_path()`関数のリストです（Python のリストは角括弧を使って定義され、アイテムはカンマ区切りです。[末尾のカンマは任意です](https://docs.python.jp/3/faq/design.html#why-does-python-allow-commas-at-the-end-of-lists-and-tuples)。例: `[item1, item2, item3,]`）

両方の関数の最初の引数は、一致させたいルート（パターン）です。 `path()` 関数では、かぎ括弧を使って、ビュー関数に名前付き引数として渡される URL の部分を定義します。 `re_path()` 関数では、柔軟なパターンマッチング方法として知られている正規表現を使います。 これらについては後の記事で説明します。

2 つ目の引数は、パターンに一致したときに呼び出される別の関数です。 `views.book_detail` という表記は、呼び出された `views` モジュール内（`views.py` という名前のファイル内部）で見つかる `book_detail()` 関数が呼び出されることを示します。

### リクエストの処理 (views.py)

ビューは、ウェブアプリケーションの中心であり、ウェブクライアントから HTTP リクエストを受け取り、HTTP レスポンスを返します。その中では、データベースにアクセスしたり、テンプレートをレンダリングしたりして、フレームワークの他のリソースを変換します。

以下の例は、前の節の URL マッパーによって呼び出される最小限の `index()` ビュー関数を示しています。すべてのビュー関数と同様に、 `HttpRequest` オブジェクトを引数 (`request`) として受け取り、 `HttpResponse` オブジェクトを返却します。この場合、リクエストには何もしません。レスポンスはハードコードされた文字列を返します。後の節で、もっと興味深いことをするリクエストを示します。

```python
# filename: views.py (Django view functions)

from django.http import HttpResponse

def index(request):
    # Get an HttpRequest - the request parameter
    # perform operations using information from the request.
    # Return HttpResponse
    return HttpResponse('Hello from Django!')
```

> [!NOTE]
> Python についての豆知識:
>
> - [Python モジュール](https://docs.python.org/3/tutorial/modules.html)は、コードで使用したい関数を別々のファイルに格納した「ライブラリー」です。ここでは、`from django.http import HttpResponse` によって `HttpResponse` オブジェクトを `django.http` モジュールからインポートし、ビューで使用できるようにします。モジュールからオブジェクトの一部または全部をインポートする方法は他にもあります。
> - 関数は、上記のように `def` キーワードを使用して宣言し、名前付きの引数は関数の名前の後に括弧内に列挙します。行全体はコロンで終わります。次の行がどのように**インデント**されているかに注意してください。インデントは重要です。コード行が特定のブロックの内側にあることを指定しています（必須のインデントは、 Python の重要な機能であり、 Python コードが読みやすい理由の 1 つです）。

ビューは通常 **views.py** ファイルに格納します。

### データモデルの定義 (models.py)

Django のウェブアプリケーションは、モデルと呼ばれる Python オブジェクトを通じてデータを管理し、クエリーを実行します。モデルは、フィールドのタイプや、最大サイズ、既定値、選択リストのオプション、ドキュメントのヘルプテキスト、フォームのラベルテキストなど、格納されるデータの構造を定義します。モデルの定義は、下層のデータベース（プロジェクト設定でいくつかから選択できます）からは独立しています。使用したいデータベースを選択したあとは、直接そのデータベースとやりとりする必要はありません。モデル構造と他のコードを書くだけで、Django はデータベースとのやりとりのすべての面倒な作業を処理します。

以下のコードスニペットは、 `Team` オブジェクトの非常に単純な Django モデルを示しています。 `Team` クラスは、 Django の `models.Model` クラスを継承しています。これは、チーム名とチームレベルを文字列フィールドとして定義し、各レコードに格納する最大文字数を指定します。 `team_level` はいくつかの値の一つになる可能性があります。したがって、この値を選択フィールドとして定義し、表示する選択項目と保存するデータの間のマッピングを既定値とともに提供します。

```python
# filename: models.py

from django.db import models

class Team(models.Model):
    team_name = models.CharField(max_length=40)

    TEAM_LEVELS = (
        ('U09', 'Under 09s'),
        ('U10', 'Under 10s'),
        ('U11', 'Under 11s'),
        # …
        # list other team levels
    )
    team_level = models.CharField(max_length=3, choices=TEAM_LEVELS, default='U11')
```

> [!NOTE]
> Python についての豆知識:
>
> - Python は「オブジェクト指向プログラミング」に対応しています。これは、データとそのデータを操作するための関数を含むオブジェクトにコードを組み上げるプログラミングのスタイルです。オブジェクトは、他のオブジェクトから継承/拡張/派生することができ、関連するオブジェクト間の共通の動作を共有できます。 Python では `class` キーワードを使用してオブジェクトの「青写真」を定義します。クラス内のモデルに基づくオブジェクトタイプの複数のインスタンスを作成できます。
>
>   たとえば、ここでは `Model` クラスから派生した `Team` クラスがあります。 これは、それがモデルであり、モデルのすべてのメソッドを含むことを意味しますが、独自の特別な機能も提供できます。我々のモデルでは、データベースにデータを格納するために必要なフィールドを定義し、名前を付けます。Django は、フィールド名を含むこれらの定義を使用して、下層のデータベースを作成します。

### データの問い合わせ (views.py)

Django モデルは、データベースを検索するための簡単なクエリー API を提供します。これは、さまざまな照合基準（例：完全一致、大文字小文字を区別しない、大なりなど）を使用して一度にいくつかのフィールドと照合でき、複雑な文に対応できます（たとえば、「U11 チームのうち、 "Fr" で始まるか"al"で終わる名前」）。

コードスニペットには、 U09 チームのすべてを表示するためのビュー機能（リソースハンドラー）が示されています。太字の線は、モデルクエリー API を使用して、 `team_level` フィールドに完全一致でテキスト '`U09`' があるすべてのレコードをフィルタリングする方法を示しています。 （`filter()` 関数には、照合基準としてフィールド名と一致種別を **`team_level__exact`** のようにダブルアンダースコアで区切った引数で渡していることに注意してください）。

```python
## filename: views.py

from django.shortcuts import render
from .models import Team

def index(request):
    list_teams = Team.objects.filter(team_level__exact="U09")
    context = {'youngest_teams': list_teams}
    return render(request, '/best/index.html', context)
```

この関数は、ブラウザーに返信される `HttpResponse` を生成するために `render()` 関数を使います。この関数はショートカットです。指定された HTML テンプレートとテンプレートに挿入するいくつかのデータ（"`context`" という名前の変数で提供される）を組み合わせて HTML ファイルを作成します。次の節では、HTML を作成するためにテンプレートにデータがどのように挿入されているかを示します。

### データのレンダリング（HTML テンプレート）

テンプレートシステムでは、出力文書の構造を指定できます。ページの生成時に埋められるデータはプレースホルダーを使用します。テンプレートは HTML を作成するためによく使われますが、他の種類の文書も生成できます。 Django はネイティブのテンプレートシステムと、 Jinja2 と呼ばれる一般的な Python ライブラリーの両方に対応しています。（必要に応じて他のシステムも対応できます）

コードスニペットは、前のセクションの `render()` 関数で呼び出される HTML テンプレートの外観を示しています。 このテンプレートは、レンダリング時に`youngest_teams` というリスト変数（上記の `render()` 関数によってコンテキスト変数に含まれます）にアクセスできる前提で作成されています。 HTML スケルトンでは、 `youngest_teams` 変数が存在するかどうかを最初にチェックし、それを `for` ループで繰り返す式があります。各繰り返しにおいて、テンプレートは各チームの `team_name` 値を {{htmlelement("li")}} 要素に表示します。

```python
## filename: best/templates/best/index.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Home page</title>
</head>
<body>
  {% if youngest_teams %}
    <ul>
      {% for team in youngest_teams %}
        <li>\{{ team.team_name }}</li>
      {% endfor %}
    </ul>
  {% else %}
    <p>No teams are available.</p>
  {% endif %}
</body>
</html>
```

## 他に何ができますか？

前の節では、ほとんどのウェブアプリケーションで使用する主な機能（URL マッピング、ビュー、モデルおよびテンプレート）を示しました。Django が提供する他の機能のいくつかを紹介します。

- **フォーム**: HTML フォームはユーザーデータを集めて、サーバー上で処理するために使われます。 Django は、フォームの作成、検証、および処理を簡素化します。
- **ユーザー認証と権限**: Django は、セキュリティを考慮して構築された強固なユーザー認証および権限システムを含んでいます。
- **キャッシュ**: コンテンツを動的に作成することは、静的なコンテンツを提供するよりもはるかに計算処理が多い（かつ低速）です。 Django は、レンダリングされたページのすべて、または一部を保存できるように、柔軟なキャッシュを提供し、必要な場合を除いて再レンダリングされないようにします。
- **管理サイト**: Django の管理サイトは、基本的な骨組みを使ってアプリケーションを作成すると、既定で含まれています。サイト管理者がサイト内のデータモデルを作成、編集、表示するための管理ページを簡単に提供できます。
- **データのシリアライズ**: Django を使用すると、簡単に XML や JSON としてデータをシリアライズして提供できます。これは、ウェブサービス（他のアプリケーションやサイトで使われるデータを純粋に提供し、何も表示しないウェブサイト）を作成する場合や、クライアントサイドのコードがすべてのデータのレンダリングする場合に便利です。

## まとめ

おめでとうございます。あなたは Django の旅の最初のステップを完了しました! これで、Django の主な利点と、その歴史について少し理解し、Django アプリの主な部分がそれぞれどのようなものか、おおよそ理解できたことでしょう。また、リスト、関数、クラスの構文など、Python プログラミング言語について も少し学んだことでしょう。

上記では実際の Django コードをいくつか見ましたが、クライアントサイドのコードとは異なり、実行するための開発環境をセットアップする必要があります。それが次のステップです。

{{NextMenu("Learn/Server-side/Django/development_environment", "Learn/Server-side/Django")}}

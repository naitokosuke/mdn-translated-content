---
title: "resource: URL"
short-title: "resource:"
slug: Web/URI/Reference/Schemes/resource
l10n:
  sourceCommit: 466ca1db767535c1aa9984b4e6c0db41b3a53475
---

{{non-standard_header}}

`resource:` というスキームの接頭辞が付いたリソース URL は、Firefox と Firefox のブラウザー拡張機能によってリソースを内部的に読み込むために使用されますが、情報の一部はブラウザーが接続するサイトでも利用できます。

## 構文

```url
resource://<path>
```

- `resource:`
  - : この URL のスキームです。
- `<path>`
  - : 読み込むリソースを指すパス。

例を示します。

```url
resource://gre/res/svg.css
```

リソース URL に矢印 ('->') がある場合は、最初のファイルが次のファイルを読み込むことを意味します。

```url
resource://<File-loader> -> <File-loaded>
```

より一般的な詳細については、[ウェブ上のリソースの識別](/ja/docs/Web/URI)を参照してください。

この記事では、組み込みのリソースを指すために Firefox が内部的に使用するリソース URI に焦点を当てます。

## 脅威

`resource:` URL によって共有される情報の一部はウェブサイトで利用できるため、ウェブページは内部スクリプトを実行し、デフォルトの設定を含む Firefox の内部リソースを調べることができます。

たとえば、[Browserleaks のスクリプト](https://browserleaks.com/resource-urls)は、サイトで実行されている簡単なスクリプトでクエリーが実行されたときに Firefox が表示する内容を強調表示します（コードは <https://browserleaks.com/resource-urls#more> にあります）。

ファイル firefox.js は、プリファレンス名と値を pref() 関数に渡します。 例えば、

```url
http://searchfox.org/mozilla-central/rev/48ea452803907f2575d81021e8678634e8067fc2/browser/app/profile/firefox.js#575
```

ウェブサイトではこの `pref()` 関数をオーバーライドし、スクリプト`resource:///defaults/preferences/firefox.js` を使用して、 Firefox のデフォルト設定を簡単に収集できます。

さらに、プラットフォームやロケールなどのビルド構成によっては、ウェブサイトがこの情報を使用して個々のユーザーを識別できるという意味で、いくつかのデフォルト設定値が異なります。

## 解決方法

この問題を解決するために、 Mozilla は [Firefox バグ 863246](https://bugzil.la/863246) のリソースを読み込む動作を変更しました。これは [Firefox 57 (Quantum)](/ja/docs/Mozilla/Firefox/Releases/57) で登場しました。

過去には、ウェブコンテンツは、 Firefox の内部リソースだけでなく、拡張機能の資産も含め、URI が必要とするあらゆるリソースにアクセスすることができました。 現在、この動作はデフォルトでは禁止されています。

しかし、特定の状況下で Firefox がウェブコンテンツにリソースを読み込む必要があります。
たとえば、ソース表示ページ（「ページのソースを表示」または「選択した部分のソースを表示」）を開くと、このページが `viewsource.css` を `resource:` URL を介してが要求していることが分かります。
ウェブコンテンツに公開する必要があるリソースは、 `resource://content-accessible/`という名前の新しい場所に移動されました。
これは隔離されており、重要ではないリソースのみが含まれています。
このようにして、重要なリソースを公開し、ほとんどの脅威を排除できます。

> [!NOTE]
> ウェブと拡張機能の開発者がリソース URL をもう使用しようとしないことをお勧めします。彼らの使い方はうまくいきませんでした。そしてほとんどの使用法はこれ以上動作しません。

## 仕様書

resource: はどの仕様書にも定義されていません。

## ブラウザーの互換性

resource: は Firefox のみ対応しています。

## 関連情報

- [URI](/ja/docs/Web/URI)
- [URL とは何か](/ja/docs/Learn_web_development/Howto/Web_mechanics/What_is_a_URL)
- [IANA list of URI schemes](https://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml) （`resource:` は[ここで扱っています](https://www.iana.org/assignments/uri-schemes/prov/resource)）

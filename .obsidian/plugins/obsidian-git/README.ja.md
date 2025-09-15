# Obsidian Git プラグイン
[Obsidian.md](Obsidian.md) 用の強力なコミュニティプラグインで、Git 統合をあなたの Vault に直接もたらします。自動的にコミット、プル、プッシュを行い、変更を確認できます — すべて Obsidian 内で完結します。

## 📚 ドキュメント
すべてのセットアップ手順（モバイルを含む）、一般的な問題、ヒント、および高度な設定は、📖 [完全なドキュメント](https://publish.obsidian.md/git-doc)に記載されています。

> 👉 モバイルユーザーへ：このプラグインは**非常に不安定です ⚠️！** 以下の専用の[モバイル](#-mobile-support-%EF%B8%8F--experimental)セクションを確認してください。

## ✨ 主な機能
- 🔁 **自動コミットと同期**（コミット、プル、プッシュ）をスケジュールに基づいて実行。
- 📥 **Obsidian 起動時の自動プル**
- 📂 複数のリポジトリを管理するための**サブモジュールサポート**（デスクトップのみ、オプトイン）
- 🔧 ファイルのステージ/アンステージ、コミット、差分表示を行う**ソースコントロールビュー**
  - `Open source control view` コマンドで開きます。
- 📜 コミットログと変更されたファイルを閲覧するための**履歴ビュー**
  - `Open history view` コマンドで開きます。
- 🔍 ファイルの変更を表示するための**差分ビュー**
  - `Open diff view` コマンドで開きます。
- 🔗 ブラウザでファイルと履歴を開く GitHub 統合
> 🧩 詳細なファイル履歴については、このプラグインを [Version History Diff](obsidian://show-plugin?id=obsidian-version-history-diff) プラグインと組み合わせて使用することを検討してください。

## UI プレビュー
### 🔧 ソースコントロールビュー
個々のファイルをステージ/アンステージしたり、コミットしたりするなど、ファイル変更を Obsidian 内で直接管理します。
![Source Control View](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/source-view.png)

### 📜 履歴ビュー
リポジトリのコミット履歴を表示します。コミットメッセージ、作成者、日付、変更されたファイルを表示できます。作成者と日付はスクリーンショットのようにデフォルトで無効になっていますが、設定で有効にできます。
![History View](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/history-view.png)

### 🔍 差分ビュー
明確で簡潔な差分ビューアでバージョンを比較します。ソースコントロールビューから、または `Open diff view` コマンドで開きます。
![Diff View](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/diff-view.png)

## ⚙️ 利用可能なコマンド
> すべてではありません — これらは最も一般的なコマンドの一部です。完全なリストは Obsidian のコマンドパレットを参照してください。

- 🔄 変更
  - `List changed files`: モーダルですべての変更をリスト表示
  - `Open diff view`: 現在のファイルの差分ビューを開く
  - `Stage current file`: 現在のファイルをステージング
  - `Unstage current file`: 現在のファイルをアンステージング
  - `Discard all changes`: リポジトリ内のすべての変更を破棄
- ✅ コミット
  - `Commit`: ファイルがステージされている場合はそれらのみをコミットし、そうでない場合はステージされたファイルのみをコミット
  - `Commit with specific message`: 上記と同じですが、カスタムメッセージ付き
  - `Commit all changes`: プッシュせずにすべての変更をコミット
  - `Commit all changes with specific message`: 上記と同じですが、カスタムメッセージ付き
- 🔀 コミットと同期
  - `Commit-and-sync`: デフォルト設定では、すべての変更をコミットし、プルし、プッシュします
  - `Commit-and-sync with specific message`: 上記と同じですが、カスタムメッセージ付き
  - `Commit-and-sync and close`: `Commit-and-sync` と同じですが、デスクトップで実行している場合は Obsidian ウィンドウを閉じます。モバイルでは Obsidian アプリを終了しません。
- 🌐 リモート
  - `Push`, `Pull`
  - `Edit remotes`: 新しいリモートを追加または既存のリモートを編集
  - `Remove remote`: リモートを削除
  - `Clone an existing remote repo`: リモートリポジトリをクローンするための URL と認証を求めるダイアログを開きます
  - `Open file on GitHub`: 現在のファイルのファイルビューを GitHub でブラウザウィンドウで開きます。注：デスクトップでのみ動作します
  - `Open file history on GitHub`: 現在のファイルのファイル履歴を GitHub でブラウザウィンドウで開きます。注：デスクトップでのみ動作します
- 🏠 ローカルリポジトリの管理
  - `Initialize a new repo`: 新しいリポジトリを初期化
  - `Create new branch`: 新しいブランチを作成
  - `Delete branch`: ブランチを削除
  - `CAUTION: Delete repository`: 注意：リポジトリを削除
- 🧪 その他
  - `Open source control view`: [ソースコントロールビュー](#sidebar-view)を表示するサイドペインを開きます
  - `Open history view`: [履歴ビュー](#history-view)を表示するサイドペインを開きます
  - `Edit .gitignore`: `.gitignore` を編集
  - `Add file to .gitignore`: 現在のファイルを `.gitignore` に追加

## 💻 デスクトップに関する注意
### 🔐 認証
一部の Git サービスでは、HTTPS/SSH 認証のためにさらなる設定が必要になる場合があります。[認証ガイド](https://publish.obsidian.md/git-doc/Authentication)を参照してください。

### Linux 上の Obsidian
- ⚠️ Snap はサンドボックスの制限によりサポートされていません。
- ⚠️ Flatpak はすべてのシステムファイルにアクセスできないため推奨されません。多くの問題が積極的に修正されていますが、まだ問題があります。特に高度なセットアップでは。
- ✅ 代わりに AppImage またはシステムパッケージマネージャーのフルアクセスインストールを使用してください（[Linux インストールガイド](https://publish.obsidian.md/git-doc/Installation#Linux)）。

## 📱 モバイルサポート (⚠️ 実験的)
モバイルでの Git 実装は**非常に不安定です**！モバイルでこのプラグインを使用することはお勧めしません。他の同期サービスを試してください。そのような代替手段の1つは、Android と iOS の両方で利用可能な [GitSync](https://github.com/ViscousPot/GitSync) です。これはこのプラグインとは関連していませんが、モバイルユーザーにとってはより良い選択肢かもしれません。セットアップのチュートリアルは[こちら](https://viscouspotenti.al/posts/gitsync-all-devices-tutorial)で見つけることができます。

> 🧪 Git プラグインは、Git の JavaScript ベースの再実装である [isomorphic-git](https://isomorphic-git.org/) のおかげでモバイルで動作しますが、深刻な制限と問題があります。Obsidian プラグインが Android または iOS でネイティブの Git インストールを使用することはできません。

### ❌ モバイル機能の制限
- **SSH 認証**なし（[isomorphic-git の問題](https://github.com/isomorphic-git/isomorphic-git/issues/231)）
- メモリ制限のため、リポジトリサイズが制限される
- リベースマージ戦略なし
- サブモジュールサポートなし

### ⚠️ パフォーマンスに関する注意
> [!caution]
> デバイスと利用可能な空き RAM の量によっては、Obsidian が
>
> - クローン/プル時にクラッシュする
> - バッファオーバーフローエラーを生成する
> - 無限に実行される
>
> 可能性があります。これは、モバイルの基盤となる git 実装が効率的ではないために発生します。これを修正する方法はわかりません。もしあなたの場合にこれが当てはまるなら、このプラグインはあなたには機能しないことを認めざるを得ません。したがって、問題にコメントしたり、新しい問題を作成したりしても解決にはなりません。申し訳ありません。

### モバイル使用のヒント：
大規模なリポジトリ/Vault をお持ちの場合は、個々のファイルをステージングし、ステージングされたファイルのみをコミットすることをお勧めします。

## 🙋 連絡先とクレジット
- 行の作成者機能は [GollyTicker](https://github.com/GollyTicker) によって開発されたため、質問があれば彼女が最もよく答えることができます。
- このプラグインは当初 [denolehov](https://github.com/denolehov) によって開発されました。2021年3月以降、このプラグインを開発しているのは私 [Vinzent03](https://github.com/Vinzent03) です。そのため、GitHub リポジトリは2024年7月に私のアカウントに移動されました。
- フィードバックや質問があれば、GitHub Issues を通じてお気軽にお問い合わせください。

## ☕ サポート
このプラグインが役に立ち、その開発をサポートしたい場合は、Ko-fi で私をサポートできます。
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/F1F195IQ5)

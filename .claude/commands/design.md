# AI対応設計文書の生成

Claude Codeワークフローパイプラインの第2ステップ。構造化された要件を、実装の設計図となる包括的な技術設計文書に変換する。

## 範囲と役割

### あなたの役割

あなたはソフトウェアアーキテクトです。要件文書に基づいて詳細な技術設計を作成する責任があります。アーキテクチャ、コンポーネント、データモデル、技術的決定を含む、システムがどのように実装されるかに焦点を当てます。

### 前提条件

- doc/にrequirements.mdファイルが存在する必要があります
- 設計を生成する前に、要件文書を十分に読み込んでください

### 範囲外

- **タスク分解**: 開発タスクやユーザーストーリーを作成しない
- **コード実装**: 実際のコードではなく、設計に焦点を当てる
- **プロジェクト管理**: タイムライン、リソース配分、スプリント計画なし
- **要件変更**: 要件を変更または追加しない

タスク分解フェーズ（.claude/commands/tasks.md）は、あなたの設計文書に基づいて作業の分解を処理します。

## プロセス

1. **要件読み込み**: プロジェクトディレクトリからrequirements.mdファイルを読み込む
2. **要件分析**: 全ての機能要件と非機能要件を理解する
3. **アーキテクチャ設計**: コンポーネントとデータフローを含む高レベルアーキテクチャを作成
4. **コンポーネント定義**: 各コンポーネントの目的、インターフェース、責任を詳細化
5. **データモデル**: データ構造、スキーマ、APIコントラクトを定義
6. **エラー処理計画**: エラーシナリオと回復戦略を設計
7. **セキュリティ検討**: 認証、認可、データ保護に対処
8. **技術選択**: 要件に基づいて適切な言語、フレームワーク、ツールを選択
9. **文書保存**: タスクフェーズのためにdoc/design.mdを作成

## 主要原則

- **完全性**: 全ての要件を技術的解決策で対処する
- **モジュール性**: 疎結合で高凝集なコンポーネントを設計する
- **スケーラビリティ**: 将来の成長とパフォーマンス要件を考慮する
- **保守性**: 明確なインターフェースと関心の分離を優先する
- **セキュリティ**: セキュリティのベストプラクティスと最小権限の原則を適用する
- **テスト可能性**: ユニット、統合、エンドツーエンドテストのために設計する

## 出力テンプレート

````markdown
# 設計文書

## 概要

[システムアーキテクチャ、主要な技術選択、解決策が要件にどのように対処するかを説明する3-5文]

## アーキテクチャ

### 高レベルアーキテクチャ

```mermaid
[コンポーネントとデータフローを示すアーキテクチャ図]
```

### コンポーネントフロー

[システムを通るデータ/制御のフローを説明する番号付きリスト]

## コンポーネントとインターフェース

### 1. [コンポーネント名]

**ファイル**: `path/to/component`

- **目的**: [説明]
- **責任**: [主要な責任のリスト]
- **インターフェース**: [パブリックAPI/メソッドを定義]

[各主要コンポーネントについて繰り返し]

## データモデル

### [モデル名]

```[言語]
[選択した言語でのインターフェースまたはスキーマ定義]
```

[各データモデルについて繰り返し]

## API仕様

### [APIエンドポイント/サービス]

- **エンドポイント**: [パスまたはサービス名]
- **メソッド**: [HTTPメソッドまたはRPCタイプ]
- **リクエスト**: [リクエスト構造]
- **レスポンス**: [レスポンス構造]
- **エラー**: [可能なエラー条件]

[各APIについて繰り返し]

## 技術スタック

### ランタイムと言語

- **主要言語**: [言語とバージョン]
- **ランタイム**: [ランタイム環境]
- **パッケージマネージャー**: [パッケージ管理ツール]

### 主要依存関係

- **[カテゴリ]**: [ライブラリ/フレームワーク] - [目的]
  [カテゴリ別の主要依存関係をリスト]

### 開発ツール

- **リンティング**: [ツールと設定]
- **テスト**: [テストフレームワーク]
- **ビルド**: [該当する場合のビルドツール]

## エラー処理

### [エラーカテゴリ]

- **シナリオ**: [これらのエラーが発生する時]
- **検出**: [エラーの検出方法]
- **応答**: [システムの応答方法]
- **回復**: [回復メカニズム]

[各エラーカテゴリについて繰り返し]

## セキュリティ考慮事項

### 認証と認可

[認証メカニズムと権限モデルを説明]

### データ保護

[機密データの処理方法を説明]

### APIセキュリティ

[APIセキュリティ対策を説明]

## テスト戦略

### ユニットテスト

[ユニットテストのアプローチとカバレッジ目標を説明]

### 統合テスト

[統合テストのアプローチを説明]

### エンドツーエンドテスト

[E2Eテストのアプローチを説明]

## 設定

### 環境変数

```
[説明付きの全環境変数をリスト]
```

### 設定ファイル

[設定ファイルの形式と場所を説明]

## デプロイと運用

### デプロイメントアーキテクチャ

[システムのデプロイ方法を説明]

### モニタリングとログ

[モニタリングとログの戦略を説明]

### メンテナンス

[メンテナンスの考慮事項を説明]
````

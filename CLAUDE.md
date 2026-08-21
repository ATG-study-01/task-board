# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## プロジェクト概要

task-board プロジェクト。テキスト入力でのタスク追加、チェックボックスによる完了/未完了の切り替え、削除、完了済みタスクのグレー表示ができるタスクボードアプリ。タスクは localStorage に保存され、ページをリロードしても消えない。

## デプロイ先

https://atg-study-01.github.io/task-board/

main ブランチに push すると、GitHub Actions（`.github/workflows/deploy.yml`）が自動でビルドしてこの URL に GitHub Pages としてデプロイする。手動でのデプロイ操作は不要。

## 技術スタック

- React 19 + TypeScript
- Vite 8（ビルド・開発サーバー）
- oxlint（Lint）
- ホスティング: GitHub Pages（GitHub Actions によるビルド・デプロイ）

## コンポーネントの命名規約

- コンポーネントファイルは `PascalCase.tsx`（例: `App.tsx`）。1ファイル1コンポーネントとし、対応するスタイルは同名の `PascalCase.css`（例: `App.css`）に置く。
- コンポーネント関数・interface（型）は `PascalCase`（例: `App`, `Task`）。
- 変数・関数・イベントハンドラは `camelCase`（例: `addTask`, `toggleTask`, `inputValue`）。イベントハンドラは `handleX` ではなく動詞から始まる名前（`addTask` 等）で統一する。
- CSS クラス名は `kebab-case`（例: `task-form`, `task-list`, `delete-button`）。状態を表すクラスは対象要素のクラス名に接頭辞を付ける形にする（例: `task` に対して完了状態は `task-completed`）。
- グローバル定数は `UPPER_SNAKE_CASE`（例: `STORAGE_KEY`）。

## Git 運用ルール

- **コードを変更するたびに、コミットして GitHub にプッシュすること。** 変更を未プッシュのままローカルに溜めない。
- 1つの変更（機能追加・修正・リファクタなど）ごとに、意味のある単位でコミットを分ける。まとめて大きな差分を一度にコミットしない。
- コミットメッセージは変更内容が分かるように簡潔に書く。
- リモート（origin）が未設定の場合は、プッシュ前にユーザーに確認する。
- 破壊的な操作（force push、履歴の書き換えなど）は、ユーザーの明示的な許可なく行わない。
- push 前に `git status` / `git diff` で差分を確認し、意図しないファイル（認証情報や秘密情報を含むファイルなど）が含まれていないことを確認する。

## 開発コマンド

- `npm run dev` — 開発サーバーを起動
- `npm run build` — 型チェック（`tsc -b`）してから本番ビルド
- `npm run preview` — ビルド成果物をローカルでプレビュー
- `npm run lint` — oxlint による Lint

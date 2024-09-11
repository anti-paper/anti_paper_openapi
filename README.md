# 要件定義書
## 目次
1. [システム開発の目的](#1-システム開発の目的)
1. [システム導入環境](#2-システム導入環境)
1. [現状の問題点](#3-現状の問題点)
1. [システム全体像](#4-システム全体像)
1. [機能要件](#5-機能要件)
1. [非機能要件](#6-非機能要件)
1. [工数](#7-工数)
1. [予算](#8-予算)
1. [スケジュール](#9-スケジュール)
1. [メンバー](#10-メンバー)
1. [開発者と発注者の連絡方法、頻度](#11-開発者と発注者の連絡方法頻度)
1. [セキュリティ対策の方法](#12-セキュリティ対策の方法)
### 1. システム開発の目的
日常生活を効率化<br>
テキストの変換
### 2. システム導入環境
- ユーザ画面<br>
Android端末（AQUOS sense7）
- 管理画面<br>
PC（Mac）
### 3. 現状の問題点
情報が全て記憶又は別々のアプリケーションによるメモ頼りになっているため、情報の抜け漏れや分散が発生し、日常生活において発生する作業の効率が悪い<br>
ちょっとしたテキストの変換・プレビュー表示のためにツールを導入する必要があり、変換・整形結果を見ながらテキストを編集するとなるとウィンドウ切り替えも頻繁に発生するため効率が悪い
### 4. システム全体像
- [業務一覧](./requirements_definition/business_list.csv)
### 5. 機能要件
- infra
  - host
    - localhost
  - database
    - localhost
  - mailer
    - localhost
  - assets
    - local PC
  - storage
    - BE
      - local PC
    - FE
      - Admin
        - BE
      - User
        - local device
  - env
    - .env
  - back up
    - bash(自動)
    - daily
- BE
  - API
    - PHP
    - Laravel
    - ソフトデリート
      - ソフトデリートされて1年経過したらハードデリート
        - バッチ自動実行
- FE
  - Admin
    - typescript
    - React
  - User
    - C#
    - Unity
- データ
  - 管理画面で使用するデータはWi-Fi環境下で同期
    - Wi-Fi環境下かどうか判定可能であればシステムに判定させ、不可であれば自己判断する（運用でカバー）
  - 管理画面で使用しないデータはスマホのローカルストレージでのみ管理
- [機能一覧](./requirements_definition/function_list.csv)
- [業務と機能の関連付け](./requirements_definition/business_function_list.csv)
### 6. 非機能要件
- 機能以外の性能
  - パフォーマンス
    - 個人利用に留まるため特に考慮しない（ループを減らすなど最低限の考慮のみ）
- ユーザビリティ
  - レスポンシブ不要
    - 管理画面はPCでしか見ない想定
    - ユーザ画面はAndroidネイティブアプリしか提供しない
  - 音声ガイド不要
    - 盲目あるいは色盲の者は利用者として想定していない
- 拡張性
  - 自サービスに関する拡張性必要
    - 随時機能拡張する想定
  - 他サービスに関する拡張性不要
    - 外部サービスは利用しない想定
- 保守・運用
  - 保守
    - 担当者
      - anti-paper
    - 内容
      - 不具合対応
        - 調査
        - 修正
    - 頻度
      - 都度
        - 自分意外に利用者がいないため、ダウンタイムに関する考慮（発生しない構成にする、アップデート・メンテナンス時間帯の調整等）不要
    - 方法
      - 内容により異なる
        - 基本的には以下の順番で調査していく
          1. infra
          1. BE
          1. FE
  - 運用
    - 担当者
      - anti-paper
    - 内容
      - サーバ起動端末でシステムアップデートかける
    - 頻度
      - 都度
        - 自分意外に利用者がいないため、ダウンタイムに関する考慮（発生しない構成にする、アップデート・メンテナンス時間帯の調整等）不要
    - 方法
      - dockerコンテナ立ち上げ直し
- 移行性
  - 考慮不要
    - 移行の可能性なし
- セキュリティ
  - infra
    - localhostを使用するため特に考慮しない
      - 同一Wi-Fi環境下でしか通信できない
      - Wi-Fiは長く複雑なパスワードによって管理している
  - BE
    - バリデーションチェック（許可不要な文字は弾く）
  - FE
    - なし
      - 自分しか使わないかつ一般公開しないため考慮する必要がない
### 7. 工数
- 195時間
### 8. 予算
- 0円
  - 個人利用であり、サーバ側はlocalhostを使用するためコストもかからない
### 9. スケジュール
- 1日あたり作業時間（目安）
  - 3時間
- 1月あたり作業可能日数（目安）
  - 30日
- 所要期間（目安）
  - 2ヶ月強
  - 自分しか使わないため納期の概念がなく、スケジュールも特に考慮する必要がない
### 10. メンバー
- anti-paper
### 11. 開発者と発注者の連絡方法、頻度
- 自社開発のため該当なし
### 12. セキュリティ対策の方法
[非機能要件](#6-非機能要件)参照
# Toggl Track to Google Calendar Sync

Toggl Track のタイムエントリを取得し、Google カレンダーに自動的に同期する Google Apps Script (GAS) ツールです。
個別の作業ログだけでなく、特定プロジェクトの合計時間を集計した「日次サマリー」を作成する機能も備えています。

## 🚀 特徴

- **作業ログの自動同期**
  - Toggl の記録を Google カレンダーのイベントとして登録します。
  - タイトル生成ロジック: `Description` がある場合はそれを優先し、空の場合は `Project Name` を使用します。
- **プロジェクトごとの色分け**
  - Toggl の Project ID に基づいて、Google カレンダー上のイベント色（全11色）を自動で振り分けます。同じプロジェクトは常に同じ色になります。
- **日次サマリー（集計）機能**
  - 指定したプロジェクト（例: "QC"）の1日の合計作業時間を計算し、終日イベントとしてカレンダーの上部にまとめて表示します。
  - 集計対象のプロジェクトはリスト形式で簡単に追加・変更可能です。

## 🛠 事前準備

- **Google アカウント**: Google Apps Script と Google カレンダーを使用するために必要です。
- **Toggl Track アカウント**:
  - **API Key**: Toggl の Profile 設定ページ ([https://track.toggl.com/profile](https://track.toggl.com/profile)) の最下部から取得してください。
  - **Project**: 事前に Toggl 上でプロジェクトを作成し、タイムログが存在する状態にしてください。

## ⚙️ セットアップ手順

### 1. スクリプトの作成
Google ドライブまたはスプレッドシートから「Apps Script」を開き、以下のコードを貼り付けます。

### 2. 設定項目の入力
コード内の以下の変数を、自身の環境に合わせて書き換えてください。

```javascript
// APIキー（取り扱い注意）
var togglApiKey = 'YOUR_TOGGL_API_KEY';

// 同期先のGoogleカレンダーID（通常は自身のGmailアドレス）
var calendarId = 'your_email@gmail.com'; 

// 1日のまとめに合計時間を表示したいプロジェクト名（配列形式で追加可能）
var TARGET_PROJECTS_FOR_SUMMARY = ['プロジェクト名'];

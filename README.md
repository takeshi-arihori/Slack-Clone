# Slack-Clone

RecursionCS の React カリキュラム、Slack の基本機能を模倣したチームコミュニケーションアプリを開発します。

## このアプリは、以下の基本要件を満たす必要があります。

1. ユーザー登録と認証
   ユーザーはアカウントを作成し、ログインすることが必須です。Google 認証を利用する形での登録が必要です。

2. メッセージの送受信
   ユーザーはテキストメッセージを送受信できるようにする必要があります。これはリアルタイムで行われます。

3. チャンネルの作成と管理
   ユーザーはチャンネルを作成し、管理できるようにする必要があります。これにより、特定のトピックやグループに関連するディスカッションを異なるチャンネルで実施できます。

## ディレクトリ構造

```
src/
├─ app/                        # Redux設定
│  ├─ hooks.ts                 # Reduxのカスタムフック
│  └─ store.ts                 # Reduxストアの設定
│
├─ components/
│  ├─ ChatContainer/
│  │  ├─ ChannelAddModal.tsx   # チャンネルを追加するモーダル
│  │  ├─ ChannelCell.tsx       # チャンネル名の表示
│  │  ├─ ChannelList.tsx       # チャンネルリスト、チャンネルを追加ボタン
│  │  ├─ MessageArea.tsx       # メッセージリスト、メッセージのフォーム
│  │  └─ MessageTile.tsx       # メッセージ1つの表示
│  ├─ ChatContainer.tsx        # 右側部分の表示
│  ├─ Login.tsx                # Googleでログイン
│  └─ Sidebar.tsx              # サイドバーの表示
│
├─ features/                   # 機能ごとのReduxロジックとコンポーネント
│  ├─ auth/
│  │  ├─ auth.ts               # Firebase認証関連の関数（Googleログイン等）
│  │  └─ useAuthState.tsx      # 自動ログイン機能
│  ├─ channel/
│  │  ├─ channelAPI.ts         # チャンネルに関するAPI呼び出しの定義
│  │  └─ channelSlice.ts       # state管理に関するRedux Sliceの定義
│  ├─ message/
│  │  └─ messageAPI.ts         # メッセージに関するAPI呼び出しの定義
│  └─ user/
│     ├─ userAPI.ts            # ユーザー情報に関するAPI呼び出しの定義
│     └─ userSlice.ts          # state管理に関するRedux Sliceの定義
│
├─ firebase/                   # Firebase設定
│  └─ firebaseconfig.ts
│
├─ type/                      # TypeScriptの型定義
│  ├─ Channel.ts
│  ├─ Message.ts
│  └─ User.ts
│
├─ index.css                   # グローバルスタイルシート
├─ index.tsx                   # アプリケーションのエントリポイント
└─ App.tsx                     # アプリケーションのルートコンポーネント
```

## 要件

このプロジェクトでは、Slack のようなインターフェースを持つチャットアプリケーションの開発を目指しましょう。アプリケーションは、主に以下の 2 つの主要な部分で構成されます。

Sidebar: アプリケーション内のナビゲーションを提供します。
ChatContainer: ユーザーの会話を表示する場所です。
ChatContainer はさらに 2 つのセクションに分かれています。

ChatList: ユーザーが参加しているチャットチャンネルのリストを表示します。
MessageArea: 選択したチャンネルのメッセージを表示し、新しいメッセージを送信するためのテキストエリアが含まれています。

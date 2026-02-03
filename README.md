# Expoアプリへようこそ 👋

これは [`create-expo-app`](https://www.npmjs.com/package/create-expo-app) で作成された [Expo](https://expo.dev) プロジェクトです。

## はじめに

1. 依存関係をインストール

   ```bash
   npm install
   ```

2. アプリを起動

   ```bash
   npx expo start
   ```

出力には、以下の方法でアプリを開くオプションが表示されます：

- [development build](https://docs.expo.dev/develop/development-builds/introduction/)
- [Android エミュレータ](https://docs.expo.dev/workflow/android-studio-emulator/)
- [iOS シミュレータ](https://docs.expo.dev/workflow/ios-simulator/)
- [Expo Go](https://expo.dev/go) - Expoでアプリ開発を試すための限定サンドボックス

**app** ディレクトリ内のファイルを編集して開発を始めることができます。このプロジェクトは [file-based routing](https://docs.expo.dev/router/introduction) を使用しています。

## アプリの起動方法

### 基本的な起動方法

開発サーバーを起動：

```bash
npx expo start
```

このコマンドを実行すると、Metroバンドラーが起動し、以下のオプションが表示されます：

- `a` - Androidエミュレータで開く
- `i` - iOSシミュレータで開く（macOSのみ）
- `w` - Webブラウザで開く
- QRコードをスキャンして実機で開く（Expo Goアプリを使用）

### プラットフォームを直接指定

```bash
# Androidエミュレータで起動
npm run android
# または
npx expo start --android

# iOSシミュレータで起動（macOSのみ）
npm run ios
# または
npx expo start --ios

# Webブラウザで起動
npm run web
# または
npx expo start --web
```

### 開発ビルドを使用する場合

`npx expo run:android` や `npx expo run:ios` でビルドした開発ビルドを使用する場合：

1. **開発サーバーを起動**（別のターミナルで）：

   ```bash
   npx expo start --dev-client
   ```

2. **エミュレータ/シミュレータでアプリを開く**：
   - エミュレータ/シミュレータが起動していれば、アプリが自動的に接続されます
   - または、デバイスのアプリ一覧からアプリを手動で起動

### 起動方法の違い

- **Expo Go**: 最も簡単な方法。Expo GoアプリをインストールしてQRコードをスキャンするだけ。ただし、一部のネイティブモジュールは使用できません。
- **開発ビルド**: カスタムネイティブコードやすべてのExpoモジュールを使用できます。初回はビルドが必要ですが、その後は高速に起動できます。
- **Web**: ブラウザで直接アプリを確認できます。デバッグが簡単です。

## 新しいプロジェクトを取得

準備ができたら、次を実行してください：

```bash
npm run reset-project
```

このコマンドは、スターターコードを **app-example** ディレクトリに移動し、開発を始められる空の **app** ディレクトリを作成します。

## アプリのビルド

### EAS Build（推奨）

[EAS Build](https://docs.expo.dev/build/introduction/) を使用すると、クラウドでアプリをビルドできます。これが最も簡単で推奨される方法です。

1. EAS CLIをインストール

   ```bash
   npm install -g eas-cli
   ```

2. Expoアカウントにログイン

   ```bash
   eas login
   ```

3. プロジェクトを設定

   ```bash
   eas build:configure
   ```

4. ビルドを実行

   - Android APK/AAB:
     ```bash
     eas build --platform android
     ```
   - iOS IPA:
     ```bash
     eas build --platform ios
     ```
   - 両方:
     ```bash
     eas build --platform all
     ```

### ローカルビルド（開発ビルド）

開発ビルドをローカルで作成する場合：

1. 必要な環境をセットアップ
   - Android: [Android Studio](https://developer.android.com/studio) と Android SDK、**Java Development Kit (JDK)**
   - iOS: [Xcode](https://developer.apple.com/xcode/)（macOSのみ）

2. ビルドを実行

   - Android:
     ```bash
     npx expo run:android
     ```
   - iOS:
     ```bash
     npx expo run:ios
     ```

### Webビルド

Webアプリとしてビルドする場合：

```bash
npx expo export:web
```

ビルドされたファイルは `web-build` ディレクトリに出力されます。

詳細については、[Expo ビルドドキュメント](https://docs.expo.dev/build/introduction/)を参照してください。

## トラブルシューティング

### Androidビルドで「Unable to locate a Java Runtime」エラーが発生する

AndroidのローカルビルドにはJava Development Kit (JDK)が必要です。

**macOSでのインストール方法：**

1. Homebrewを使用してOpenJDKをインストール（推奨）

   ```bash
   brew install openjdk@17
   ```

   または最新版：

   ```bash
   brew install openjdk
   ```

2. 環境変数を設定

   ```bash
   echo 'export PATH="/opt/homebrew/opt/openjdk@17/bin:$PATH"' >> ~/.zshrc
   echo 'export JAVA_HOME="/opt/homebrew/opt/openjdk@17"' >> ~/.zshrc
   source ~/.zshrc
   ```

3. インストールを確認

   ```bash
   java -version
   ```

**別の方法：Android StudioのJDKを使用する**

Android Studioがインストールされている場合、それに含まれるJDKを使用できます：

1. 環境変数を設定（`~/.zshrc`に追加）

   ```bash
   echo 'export JAVA_HOME="/Applications/Android Studio.app/Contents/jbr/Contents/Home"' >> ~/.zshrc
   echo 'export PATH="$JAVA_HOME/bin:$PATH"' >> ~/.zshrc
   source ~/.zshrc
   ```

2. インストールを確認

   ```bash
   java -version
   ```

インストール後、再度 `npx expo run:android` を実行してください。

## さらに学ぶ

Expoでプロジェクトを開発する方法について詳しくは、以下のリソースを参照してください：

- [Expo ドキュメント](https://docs.expo.dev/)：基礎を学ぶか、[ガイド](https://docs.expo.dev/guides)で高度なトピックに進みましょう。
- [Learn Expo チュートリアル](https://docs.expo.dev/tutorial/introduction/)：Android、iOS、Webで動作するプロジェクトを作成するステップバイステップのチュートリアルに従ってください。

## コミュニティに参加

ユニバーサルアプリを作成する開発者のコミュニティに参加しましょう。

- [GitHub の Expo](https://github.com/expo/expo)：オープンソースプラットフォームを閲覧し、貢献してください。
- [Discord コミュニティ](https://chat.expo.dev)：Expoユーザーとチャットし、質問してください。

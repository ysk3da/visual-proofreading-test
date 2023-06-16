# ビジュアル校正テスト

- [デザインと HTML のズレを検出！Node.js と Puppeteer 活用のビジュアル校正テストで実装時のケアレスミスを防ぐ](https://ics.media/entry/220331/)

## インストール

```sh
npm install
```

## 使い方

プロジェクトルートに`design`ディレクトリを作成し、デザインファイルからアートボードを png などの形式で書き出してください。

localhost:8080 で比較したいページを含む開発環境を起動してください。  
（URL は設定で変更可能です。）

[設定ファイル](libs/test-config.mjs)を開いて、該当のパスと画像をペアリングしてください。

```js
...

// 実装したもののURL
export const CAPTURE_URL = "http://localhost:8080";

// ブラウザのビューポートサイズ
export const VIEW_PORT = { width: 1600, height: 900 };
// export const VIEW_PORT = { width: 375, height: 667 };

// テスト設定。デザイン画像とスクリーンショットを撮るパスを記述する
export const testSettings = [
  {
    design: "top.png",
    capturePath: "/",
  },
  {
    design: "about.png",
    capturePath: "/about/",
  },
  {
    design: "works.png",
    capturePath: "/works/",
  },
];
```

`diff`と`screenshot`ディレクトリは自動的に生成されます。

package.json の scripts に書かれているコマンドを実行してください。

```sh
npm run visual-proofreading-test

# or スライダーなどのアニメーションがある場合はこちら

npm run advanced-visual-proofreading-test
```

`diff`の中の差分画像を確認して、ズレを修正してください。

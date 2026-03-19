# nphello

## パッケージの登録

1. パッケージ作成

```sh
npm init -y
```

2. package.json を変更

```json
// @GitHubユーザー名/リポジトリ名
"name": "@reiminami/nphello",
// メインファイル
"main": "src/index.js",
// リポジトリ内容 (url はクローンする際のURL)
"repository": {
  "type": "git",
  "url": "git@github.com:reiminami/nphello.git"
},
```

3. コンテンツを作成 (例: [src/index.js](/src/index.js))

```js
function hello() {
    console.log("Hello World!");
}

module.exports = hello;
```

4. コミット

作成したコンテンツをコミット

5. アクセストークンの設定 (使用するためメモしておく)

[GitHub Personal Access Tokens のドキュメント](https://dev.classmethod.jp/articles/github-personal-access-tokens/)を参考に、`write:packages`, `read:packages`, `repo` をオンにする。

6. ターミナルでnpm にログイン

```sh
npm login --registry=https://npm.pkg.github.com
# username はGitHubユーザー名
# password はPersonal access tokens (アクセストークン)
```

7. ターミナルでGitHub Packages に登録

```sh
npm publish
```

## パッケージの更新

1. パッケージのコードを修正

2. コミット

3. `npm version` コマンドでバージョン番号を更新＆Gitコミット

  - `patch`: 1.1.1 -> 1.1.2
  - `minor`: 1.1.1 -> 1.2.0
  - `major`: 1.1.1 -> 2.0.0

    ```sh
    npm version patch
    ```

4. `npm publish` で登録

5. 呼び出す側のバージョンを上げる

```sh
# package.json に古いバージョンが残っている場合更新されないため注意
npm install @reiminami/nphello@latest
```

## パッケージの利用

1. `.npmrc` を作成

```sh
echo "@reiminami:registry=https://npm.pkg.github.com" >> .npmrc
```

2. アクセストークン情報を.npmrc に追加 (XXXX はメモしておいたアクセストークン)

```sh
//npm.pkg.github.com/:_authToken=XXXX
```

2. パッケージ(最新) をインストール

```sh
npm install @reiminami/nphello@latest
```

3. 呼び出すファイルを作成し実行

```js
import nphello from "@reiminami/nphello";
nphello();  // Hello World!
```

## commonjs or module

package.json の"type" で、"commonjs"か"module" を選択できる。

- "commonjs": module.exports を使う。
  ```js
  module.exports = hello;
  ```
- "module": export / import を使う。
  ```js
  export default hello;
  ```

## 注意点

- ここまでで.gitignore すべきファイル (呼び出し側)
  - `node_modules/` : 単純に不要
  - `package-lock.json` : ライブラリなので不要
  - `.npmrc` : トークンの記載があるため


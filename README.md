# nphello

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
export function hello() {
    console.log("Hello World!");
}
```

4. コミット

作成したコンテンツをコミット

5. アクセストークンの設定

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






commit

使う側:
echo "@reiminami:registry=https://npm.pkg.github.com" >> .npmrc

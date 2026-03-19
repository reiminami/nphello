# nphello

メモ

- `npm init -y`
- package.jsonを変更
    - name を`@reiminami/nphello`に変更
    - main を`src/index.js`に変更
    - repository url を`git@github.com:reiminami/nphello.git` に変更
- src/index.js 作成
- [x](https://dev.classmethod.jp/articles/github-personal-access-tokens/)
write:packages
read:packages
repo

- ログイン: `npm login --registry=https://npm.pkg.github.com`
Username: Github User name
password: personal access token

npm publish

commit

使う側:
echo "@reiminami:registry=https://npm.pkg.github.com" >> .npmrc

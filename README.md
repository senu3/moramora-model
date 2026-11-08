# マンボウの3Dモデルデモ

マンボウの巡航と鰓の呼吸をブラウザーで観察し、Blenderで形状やリグの作り方を復習するためのリポジトリです。

## デモを見る

Node.js 24 を用意し、リポジトリのルートで実行します。PowerShell では `npm` を `npm.cmd` として実行できます。

```sh
npm ci
npm run dev
```

ターミナルに表示された URL を開きます。ドラッグで視点を回転し、ホイールで拡大・縮小できます。「巡航ループを再生」をオンにすると、鰭と鰓の周期の違いを観察できます。口・鰓のスライダーや「回転制限端の確認」で、変形を一つずつ確かめられます。画面上部のリンクで通常版と圧縮版を切り替えられます。

## Blenderで復習する

[軽量版のBlenderファイル](blender/sunfish_game.blend)を Blender 5.2 で開きます。材質用のテクスチャはファイルに内包しています。

1. 胴体の Shape Keys で `Mouth_Open`、`Gill_Open`、`Gill_Bulge` を動かし、開口と膜の膨らみを見比べます。
2. リグをポーズモードで開き、胸鰭の付け根のローカルX軸と、片側4本の主ボーンおよび後縁の補助ボーンを確認します。
3. アクションエディターで `Swim_Cruise_FourBonePectoral` を確認します。ブラウザーでは、制約を評価してベイクした `Swim_Cruise_Loop` を再生します。

工程ごとの指示と結果は[制作ログ](docs/SUNFISH_MODEL_CREATION_LOG.md)にまとめています。

## GitHub Pages に公開する

1. このリポジトリの `main` を GitHub 上の公開先へ push します。
2. GitHub の **Settings → Pages → Build and deployment → Source** で **GitHub Actions** を選択します。
3. **Actions → Deploy demo to GitHub Pages → Run workflow** から `main` を選び、実行します。以降は `main` への push で更新されます。
4. デプロイが成功したら、**Settings → Pages** に表示される URL を開きます。

公開ビルドは `npm run build` で生成し、`npm run preview` で確認できます。[公開ワークフロー](.github/workflows/pages.yml)は `dist/` を配信します。

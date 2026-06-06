# tsubame-terrace (リダイレクト専用)

旧 GitHub Pages URL `https://tsubame-terrace-owner.github.io/tsubame-terrace/...` に
アクセスされた際、新URL `https://tsubame-terrace-owner.github.io/reservation/...` に
転送するためだけのリポジトリ。

実体のソースコードは [tsubame-terrace-owner/reservation](https://github.com/tsubame-terrace-owner/reservation) にある。

## 仕組み

`docs/404.html` と `docs/index.html` に JavaScript の redirect が入っており、
旧パスのプレフィックス `/tsubame-terrace` を `/reservation` に置換した上で
クエリ文字列 (cancelToken 等) と hash も維持して新URLに `window.location.replace` する。

## いつ削除してよいか

**2026-07-07 以降に削除可能。**

理由:

- 予約システムの `BOOKING_WINDOW_DAYS` は 30 日。
  本日 (2026-06-06) 受け付けた予約の最遅来店日が 2026-07-06。
- 旧URLが含まれる確認メールは、2026-06-06 にGAS側 `FRONTEND_BASE_URL` を
  新URLに更新するまでに送信された分のみ。
- 2026-07-06 までの全ての既存予約が来店日を過ぎれば、
  旧URLのリンクをタップする必要のあるお客様はいなくなる。
- 1日のバッファを取って 2026-07-07 以降に削除すれば安全。

削除手順:
1. GitHub Web で本リポジトリ Settings → Danger Zone → Delete this repository
2. リポジトリ名を入力して削除確定

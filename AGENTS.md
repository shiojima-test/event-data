# チャット（Claude）向けの決まり：出展先リスト

## 置き場所
- データは events.json。各イベントの `todo` が朝のまとめの元になる。書くのは Claude だけ
- 朝のまとめは shiojima-test/festa-carrot の gas/exhibit.js（キャロットの定時処理が8〜11時台に1日1回実行）。投稿先はキャロットのチャンネル（#project-展示 は2026-09-30で廃止）
- 出展先リストのシートは events.json を写すだけ。シートは直さない

## todo の書き方
- `due`：YYYY-MM-DD。申込締切・提出日など「その日までに手を打つ日」だけを入れる。面談日・発送日・結果連絡日は入れない
- `what`：その日にやること（1行）
- `state`：open（未着手）／waiting（返信待ち・`since` に連絡した日）／replied（返事あり・`since` に返事の日）／done（完了）／hold（保留）
- done と hold はまとめに出ない。waiting は連絡から7日たったら出る
- `deadline` と `waiting` の旧フィールドは使わない（旧通知が拾って二重に投稿するため）

## Slackのまとめを貼られたときの進め方（どのチャットでも同じ）
1. events.json を読み、まとめに出ている id の status・memo・todo を確かめる
2. Gmail（連絡先のアドレスで検索）と過去チャットで、手を打ち終えていないかを先に確かめる。確かめて分かることは質問しない
3. 残ったものだけ、タップで答えるカード（ask_user_input）で1問ずつ聞く。まとめて聞かない
4. 答えに合わせて todo を直す。status と memo の先頭に日付つきで経緯を1行足す
5. コミットのメッセージにその id を [ ] で入れる。updated / updated_at を今の時刻にする
6. 期限のあるものは Googleカレンダーへの登録まで検討する

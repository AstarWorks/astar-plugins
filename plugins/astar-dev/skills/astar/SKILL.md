---
name: astar
description: Astar（事務所の書類・テーブル・案件・予定・メール・録音の記録）を読み書きするときに使う。Astar のフォルダ、書類、案件一覧、予定、メールを探す・読む・まとめる・更新する依頼で使う。
---

# Astar の使い方

Astar の MCP サーバー `astar` のツールで操作する。最初の接続ではブラウザで Astar の同意画面が開くので、利用者が組織・担当させる AI メンバー・許可する範囲（読み取りのみ / 書き込みも許可）を選ぶ。

## 始め方

1. まず `context_read` を呼び、見えるテナント・ワークスペース・フォルダと、ASTAR.md の規則を確かめる。ASTAR.md の規則には従う。
2. 場所が分からないときは `search`（横断検索）か `node_search` で探す。path を推測して指定しない。

## よく使うツール

| したいこと | ツール |
|---|---|
| フォルダ・書類を一覧・ツリーで見る | `node_list`, `node_tree`, `workspace_list` |
| 書類を読む | `file_read`, `file_section_read`, `node_read` |
| 書類を作る・直す | `node_create`, `file_update`, `node_rename`, `node_move` |
| 表（案件一覧など）を見る・集計する | `table_list`, `table_record_list`, `table_record_search`, `table_record_aggregate` |
| 表の行を足す・直す | `table_record_create`, `table_record_update` |
| 予定・空き時間 | `calendar_event_search`, `calendar_availability_search` |
| メール | `mail_message_search`, `mail_conversation_read`, `mail_draft_create` |
| 過去の版に戻す | `*_history_list`, `*_history_restore` |

## 守ること

- 書き込みは、利用者が頼んだものだけ行う。消す・送る操作の前には対象を示して確かめる。
- 権限は「担当させた AI メンバーのロール」「接続した人（操作者）の権限」「許可した範囲」のいちばん狭いものになる。403 や権限エラーは、どれが足りないかを利用者に伝える。勝手に別の手段で回り込まない。
- 返した内容には、Astar 上の場所（path）を添える。

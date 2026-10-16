# Astar Plugins

Claude Code と Codex に Astar をつなぐ Plugin です。接続設定（MCP）と、Astar の使い方（スキル）が入っています。

| Plugin | つなぐ先 |
|---|---|
| `astar` | Production（`https://api.astarworks.com/mcp`） |
| `astar-staging` | Staging（社内の確認用） |
| `astar-dev` | dev（開発用、`https://api-dev.astarworks.com/mcp`） |

## 入れ方

Claude Code:

```
/plugin marketplace add AstarWorks/astar-plugins
/plugin install astar@astar
```

Codex:

```
codex plugin marketplace add AstarWorks/astar-plugins
codex plugin add astar@astar
codex mcp login astar
```

初めて使うときにブラウザで Astar の同意画面が開きます。組織・担当させる AI メンバー・許可する範囲を選んで **許可** を押してください。詳しくは Astar のマニュアル「外部のAIからつなぐ」を参照してください。

## 新しい版を出す

`plugins/<name>/.claude-plugin/plugin.json`・`.codex-plugin/plugin.json`・`.claude-plugin/marketplace.json` の `version` を上げて main に push します。利用者は Claude Code なら `/plugin marketplace update astar`、Codex なら `codex plugin marketplace upgrade` で更新します。

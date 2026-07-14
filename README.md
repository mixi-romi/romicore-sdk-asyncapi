# romicore-sdk-asyncapi

MIXI が開発した会話 AI ロボット [Romi](https://romi.ai/) を制御する MQTT API の
[AsyncAPI](https://www.asyncapi.com/) 仕様と、そのドキュメントサイトのソースです。

この仕様に準拠すれば、公式 SDK ([romicore-sdk-py](https://github.com/mixi-romi/romicore-sdk-py))
の利用有無にかかわらず Romi と通信・制御できます。

## ドキュメント

公開ドキュメントサイト: <https://mixi-romi.github.io/romicore-sdk-asyncapi/>

## 構成

| パス | 内容 |
|---|---|
| `asyncapi.yml` | AsyncAPI 3.1.0 仕様（チャネル/オペレーション定義。`schemas/` を `$ref`） |
| `schemas/` | ペイロードスキーマ（`romicore-sdk-py` の `tools/generate_json_schema.py` が生成） |
| `docs/` | ドキュメントサイト（zensical）のソース |
| `zensical.toml` | ドキュメントサイトのビルド設定 |

`schemas/` は SDK 側で生成される成果物で、SDK の payload 定義が更新されると CI により
自動で反映されます（`.github/workflows/build-and-deploy.yml`）。

## ローカルでのビルド

```bash
# ドキュメントサイト（zensical）
uv sync
uv run zensical build          # -> site/

# AsyncAPI HTML
npx @asyncapi/generator@2 asyncapi.yml @asyncapi/html-template -o ./asyncapi
```

## License

[MIT](LICENSE)

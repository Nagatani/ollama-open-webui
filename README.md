# ollama-open-webui

OllamaとOpen WebUIを組み合わせたDockerコンテナです。

## 環境設定

起動する前に、環境変数を設定する必要があります。以下のコマンドを実行して、`.env-sample` を `.env` にコピーしてください。

```bash
cp .env-sample .env
```

その後、`.env` ファイルを開き、`OPEN_WEBUI_SECRET_KEY` の値を安全なランダムな文字列に変更してください。

## 起動方法

以下のコマンドを実行して、サービスを起動します。

```bash
docker compose up -d
```

ブラウザで [http://localhost:3000](http://localhost:3000) にアクセスして、Open WebUI を利用できます。

## Gemma 3 (4B) の使用方法

Gemma 3 (4B) モデルをダウンロード

```bash
docker compose exec ollama ollama pull gemma3:4b
```

## 参考: OllamaでGPUを使用する場合

```yaml
services:
  ollama:
    # 省略

    # 以下のセクションを追加
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              capabilities: [gpu]
              count: all
```

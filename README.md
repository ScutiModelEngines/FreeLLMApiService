# FreeLLMApiService

FreeLLMAPI is an MIT-licensed, self-hosted router that puts free LLM provider tiers behind one OpenAI-compatible `/v1` endpoint. The dashboard and API share LAN port `29652`. [Upstream FreeLLMAPI](https://github.com/tashfeenahmed/freellmapi)

## Deploy

From Windows, run `run.bat` and choose **1 Deploy**, or run `run.bat deploy`. This copies the folder to `lex@scutiserver1.local:/media/ZimaOS-HD/Apps/ModelEngines/` for manual startup on the server.

## First run on the server

1. Open `/media/ZimaOS-HD/Apps/ModelEngines/FreeLLMApiService` on the server. Copy `.env.example` to `.env`, restrict permissions with `chmod 600 .env`, and replace `ENCRYPTION_KEY` with the 64-character hex output of `openssl rand -hex 32`.
2. Run `docker compose up -d`.
3. Open [http://scutiserver1.local:29652](http://scutiserver1.local:29652) on your trusted LAN. Use `docker compose logs freellmapi` to find the one-time setup code when prompted, then create the first dashboard account and add your provider keys under **Keys**. [Upstream install guide](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/install/01-install.md#docker-compose)

Back up `data/`, which holds SQLite and the encrypted provider keys. Keep a secure backup of `ENCRYPTION_KEY` separately so those keys can be decrypted after a restore.

Upstream recommends FreeLLMAPI for personal experimentation only. Pooling free accounts may violate some providers' terms of service. [Upstream disclaimer](https://github.com/tashfeenahmed/freellmapi#disclaimer)

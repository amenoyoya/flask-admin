# flask-admin

## Environment

- Docker: `19.03.2`
- DockerCompose: `1.24.0`
- CLI:
    - Node.js: `10.15.3`
    - yarn: `1.15.2`

### Structure
```bash
./
 |_ app/  # Webアプリケーション本体
 |   |_ seerver/
 |   |   |_ static/ # 静的ファイル配置
 |   |   |   |_ js/
 |   |   |       |_ bundle.js # webpackバンドル後のJSファイル
 |   |   |
 |   |   |_ __init__.py   # ライブラリ本体
 |   |   |_ auth_api.py   # ユーザー認証API
 |   |   |_ config.yml    # 設定ファイル
 |   |   |_ server.py     # Flaskサーバー
 |   |
 |   |_ src/
 |   |   |_ index.js      # Vueソースコード（エントリーポイント）
 |   |
 |   |_ vassals/
 |   |   |_ server.ini    # FlaskサーバーのuWSGI設定
 |   |
 |   |_ package.json      # Node.js依存モジュール定義
 |   |_ webpack.config.js # webpackバンドル設定
 |
 |_ flask/ # flaskコンテナ
 |   |_ Dockerfile        # ビルド設定
 |   |_ requirements.txt  # Python依存モジュール定義
 |
 |_ web/   # webコンテナ
 |   |_ Dockerfile        # ビルド設定
 |   |_ nginx.conf        # nginx設定ファイル
 |
 |_ docker-compose.yml    # DockerComposeビルド設定
                          # - web:   Nginx 1.17 | http://fe-exam.localhost
                          # - flask: Python 3.7 + Flask + uWSGI
```

### Setup
```bash
# Dockerコンテナをビルド＆起動
$ docker-compose build
$ docker-compose up -d

# appディレクトリに移動
$ cd app

# node.js 開発開始
$ yarn install # 依存パッケージインストール
$ yarn watch   # js, vue ファイル変更検知＆バンドル
```

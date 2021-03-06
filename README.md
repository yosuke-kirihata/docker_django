# docker_django

## Django サーバの起動手順

コンテナ起動

```
PS C:\Users\Yosuke Kirihata\Desktop\docker> docker-compose up
```

docker_web のコンテナ ID を確認

```
PS C:\Users\Yosuke Kirihata\Desktop> docker ps
CONTAINER ID   IMAGE           COMMAND                  CREATED             STATUS          PORTS                    NAMES
XXXXXXXXXXXX   docker_web      "python3"                About an hour ago   Up 47 minutes   0.0.0.0:8000->8000/tcp   django
YYYYYYYYYYYY   postgres:12.4   "docker-entrypoint.s…"   About an hour ago   Up 47 minutes   0.0.0.0:5432->5432/tcp   postgres-django
```

確認した コンテナ ID で docker_web の Shell にログイン

```
PS C:\Users\Yosuke Kirihata\Desktop> docker exec -i -t XXXXXXXXXXXX /bin/bash
```

Django サーバ実行(Django アプリ作成、DB マイグレーション済であること)

```
root@fa3a14869cf9:/code[appname]/# python manage.py runserver 0:8000`
```

Web ブラウザによる簡易動作確認
localhost:8000/[作成 Django アプリのルーティング]をブラウザで閲覧

# docker-test

## 手順

### コンテナを作成＆起動します
```
git clone https://github.com/HoriTaichi/docker-test.git

cd docker-test

docker-compose up -d
```

### phpのコンテナにlaravelプロジェクトを作成します
```
docker exec -i -t (PHPコンテナのID) composer create-project --prefer-dist laravel/laravel laravel
```

### 下記のURLで確認ー
```
http://localhost
```
ララベルの画面が見れるはず！

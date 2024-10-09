# sonarqube-sample

## 手順: dotnet

1. dotnet sdkをインストール
2. コンテナ起動
```bash
docker compose up -d
```
3. http://localhost:9000 にアクセスして、初期設定を行う
   1. Create local project
      - Project display name: 任意
      - Project key: 任意
      - Main branch: 任意
   2. setup
      - [x] Use the global setting
   3. Analysis Method
      - [x] Locally
   4. Provide a token
      - Token name: デフォルト
      - Expires in: No expiration
   5. Generate -> Continue
   6. Run analysis on your project
      - [x] .NET
4. 表示されたコマンドを実行

```bash
dotnet tool install --global dotnet-sonarscanner
# slnファイルがあるディレクトリに移動
cd {slnファイルがあるディレクトリ}
dotnet sonarscanner begin /k:"{key}" /d:sonar.host.url="http://localhost:9000"  /d:sonar.token="{Token}"
dotnet build
dotnet sonarscanner end /d:sonar.token="{Token}"
```
4. http://localhost:9000 にアクセスして、結果を確認



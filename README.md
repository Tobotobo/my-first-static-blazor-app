# Blazor Starter Application

このテンプレートには、.NET 8 [Blazor WebAssembly](https://docs.microsoft.com/aspnet/core/blazor/?view=aspnetcore-6.0#blazor-webassembly) クライアントアプリケーション、.NET 8 C# [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)、および共有コードを含む C# クラスライブラリの例が含まれています。

## はじめに

1. [GitHub template](https://docs.github.com/en/enterprise/2.22/user/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template) からリポジトリを作成し、あなたのマシンのローカルにクローンします。

1. **Api** フォルダで `local.settings.example.json` を `local.settings.json` にコピーします。

1. Visual Studio または Visual Studio Code のいずれかを使用して続行します。

### Visual Studio 2022

プロジェクトをクローンしたら、Azure ワークロードがインストールされた最新リリースの [Visual Studio 2022](https://visualstudio.microsoft.com/vs/) でソリューションを開き、以下の手順に従います。

1. ソリューションを右クリックし **Configure Startup Projects...** を選択します。

1. **Multiple startup projects** を選択し、各プロジェクトに以下のアクションを選択します。
    - *Api* - **Start**
    - *Client* - **Start**
    - *Shared* - None

1. **F5** キーを押して、クライアントアプリと Functions API アプリの両方を起動します。

### Visual Studio Code と Azure Static Web Apps CLI による優れた開発体験（オプション）

1. [Azure Static Web Apps CLI](https://www.npmjs.com/package/@azure/static-web-apps-cli) と [Azure Functions Core Tools CLI](https://www.npmjs.com/package/azure-functions-core-tools) をインストール（または更新）します。

1. Visual Studio Code でフォルダを開きます。

1. `Client/wwwroot/appsettings.Development.json` を削除します。

1. Visual Studio Code のターミナルで以下のコマンドを実行し、Static Web Apps CLI を Blazor WebAssembly クライアントアプリケーションと Functions API アプリと共に起動します。

    Client フォルダで以下を実行
    ```bash
    dotnet run
    ```

    Api フォルダで以下を実行
    ```bash
    func start
    ```

    上記とは別のターミナルで以下を実行
    ```bash
    swa start http://localhost:5000 --api-location http://localhost:7071
    ```

    Static Web Apps CLI (`swa`) はポート 4280 でプロキシを起動し、静的サイトのリクエストをポート 5000 の Blazor サーバーに、`/api` エンドポイントへのリクエストを Functions サーバーに転送します。

1. ブラウザを開き、Static Web Apps CLI のアドレス（`http://localhost:4280`）に移動します。このアドレスから、クライアント・アプリケーションと Functions API アプリの両方にアクセスできます。Fetch Data ページに移動すると、Functions API アプリから返されたデータが表示されます。

1. Static Web Apps CLI を停止するには Ctrl-C を入力します。

## テンプレートの構成

- **Client**: Blazor WebAssembly サンプルアプリケーション
- **Api**: Blazor アプリケーションが呼び出す C# Azure Functions API
- **Shared**: Blazor と Functions アプリケーション間でデータモデルを共有する C# クラスライブラリ

## Azure Static Web Apps へのデプロイ

このアプリケーションは [Azure Static Web Apps](https://docs.microsoft.com/azure/static-web-apps) にデプロイすることができます。その方法については、[クイックスタートガイド](https://aka.ms/blazor-swa/quickstart)をご覧ください。
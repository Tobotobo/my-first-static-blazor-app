# MEMO

* Client フォルダで `dotnet run` した時にエラーになったら `dotnet restore` してみる。

## ツールのインストール

注意
Node.js の 18 が必用。  
現在、20 以上はサポートされていない。

20 のサポートについてイシューに上がっているが 2024/03/20 現在未対応。  
[Node 20 support #756](https://github.com/Azure/static-web-apps-cli/issues/756)

###  [Azure Static Web Apps CLI](https://www.npmjs.com/package/@azure/static-web-apps-cli)
```
npm install -g @azure/static-web-apps-cli
```

### [Azure Functions Core Tools CLI](https://www.npmjs.com/package/azure-functions-core-tools)
```
npm i -g azure-functions-core-tools@4 --unsafe-perm true
```




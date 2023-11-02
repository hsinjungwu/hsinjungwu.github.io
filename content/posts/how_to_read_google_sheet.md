---
title: "如何讀取 Google Sheet"
date: 2023-11-01T20:25:00+08:00
draft: false
dropCap: false
tags:
  - "HowTo"
---

## 設定 Google Sheet API

1. 到 https://console.cloud.google.com/ 建立新專案。
2. 在新專案下
    + 建立憑證，目前是採用 **服務帳戶** 的設定並下載金鑰 `client_secret.json`
    > 將服務帳戶加到 sheet 共享名單中
    + 啟用 `Google Sheet API`，如果沒啟用會跳出以下錯誤 
    > Google Sheets API has not been used in project XXXX before or it is disabled. Enable it by visiting
3. 使用以下程式碼 `GoogleSheetsHelper`

```csharp
public class GoogleSheetsHelper
{
    public SheetsService Service { get; set; }
    private const string APPLICATION_NAME = "name";
    private static readonly string[] Scopes = { SheetsService.Scope.Spreadsheets, SheetsService.Scope.SpreadsheetsReadonly };

    public GoogleSheetsHelper()
    {
        InitializeService();
    }

    private void InitializeService()
    {
        var credential = GetCredentialsFromFile();
        Service = new SheetsService(new BaseClientService.Initializer()
        {
            HttpClientInitializer = credential,
            ApplicationName = APPLICATION_NAME
        });
    }

    private GoogleCredential GetCredentialsFromFile()
    {
        GoogleCredential credential;

        using (var stream = new FileStream("client_secret.json", FileMode.Open, FileAccess.Read))
        {
            credential = GoogleCredential.FromStream(stream).CreateScoped(Scopes);
        }
        return credential;
    }
}
```

4. 外部實作

```csharp
private void DoSomething()
{
    GoogleSheetsHelper gsh = new GoogleSheetsHelper();
    var _gsValues = gsh.Service.Spreadsheets.Values;
    var range = $"{sheetName}!A:B";
    var request = _gsValues.Get(sheetId, range);
    var response = request.Execute();
    IList<IList<object>> values = response.Values;
    //values is what you want
}
```

### reference

+ https://ithelp.ithome.com.tw/articles/10283037
+ https://stackoverflow.com/questions/68721853/how-to-fix-google-sheets-api-has-not-been-used-in-project
+ https://xenby.com/b/245-%E6%95%99%E5%AD%B8-google-oauth-2-0-%E7%94%B3%E8%AB%8B%E8%88%87%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97
+ https://dotblogs.com.tw/rainmaker/2016/08/08/230646
+ https://blog.csdn.net/fire555/article/details/106276831
+ https://developers.google.com/api-client-library/dotnet/apis/sheets/v4
+ https://ithelp.ithome.com.tw/questions/10207707
+ http://white5168.blogspot.com/2016/09/google-sheets-api-google-spreadsheet.html#.Y5w_RHZByUk
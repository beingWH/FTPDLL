# FTPDLL
FTPDLL底层由socket方法实现，是一个FTPclient的基本方法类库。
## 使用方法
1. 在引用中添加FTPTools.dll 
1. 命名空间中,using FTPTools.dll
1. 调用方法
```C#
例如，上传文件
  IFTPClient client = FTPFactory.CreateClient("192.9.220.241", "vincent", "198959");
  client.Connect();
  client.OpenDownload("README.md", @"E:\README.md");
  while (client.DoDownload() > 0)
  {
      int perc = (int)(((client.BytesTotal) * 100) / client.FileSize);
      Console.WriteLine(perc.ToString() + "%<br/>");
  }
  client.Disconnect();
```

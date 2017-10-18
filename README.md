# FTPDLL
FTPDLL底层由socket方法实现，是一个FTPclient的基本方法类库。
## 使用方法
1. 在引用中添加FTPTools.dll 
1. 命名空间中,using FTPTools
1. 调用方法
## 常用方法示例
* 创建目录
```C#
  IFTPClient client = FTPFactory.CreateClient("192.9.220.241", "vincent", "198959");
  client.Connect();
  client.MakeDir(string dir)
  client.Disconnect();
```
* 转移到工作目录
```C#
  IFTPClient client = FTPFactory.CreateClient("192.9.220.241", "vincent", "198959");
  client.Connect();
  client.ChangeDir(string dir)
  client.Disconnect();
```
* 移除目录
```C#
  IFTPClient client = FTPFactory.CreateClient("192.9.220.241", "vincent", "198959");
  client.Connect();
  client.RemoveDir(string dir)
  client.Disconnect();
```
* 上传文件
```C#
  IFTPClient client = FTPFactory.CreateClient("192.9.220.241", "vincent", "198959");
  client.Connect();
  client.OpenUpload(@"D:\README.md", Path.GetFileName(@"D:\README.md"));
  while (client.DoUpload() > 0)
  {
      int perc = (int)(((client.BytesTotal) * 100) / client.FileSize);
      Console.WriteLine(perc.ToString() + "%<br/>");
  }
  client.Disconnect();
```
* 下载文件
```C#
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
* 文件夹列表
```C#
  IFTPClient client = FTPFactory.CreateClient("192.9.220.241", "vincent", "198959");
  client.Connect();
  ArrayList list = client.ListFiles();
  for (int i = 0; i < list.Count; i++)
  {
      Console.WriteLine(list[i].ToString() + "<br/>");
  }
  Console.ReadLine();
  client.Disconnect();
```
* 删除文件
```C#
  IFTPClient client = FTPFactory.CreateClient("192.9.220.241", "vincent", "198959");
  client.Connect();
  client.RemoveFile("README.md");
  client.Disconnect();
```
* 文件重命名
```C#
  IFTPClient client = FTPFactory.CreateClient("192.9.220.241", "vincent", "198959");
  client.Connect();
  client.RenameFile("mzwucom.jpg", "test.jpg");
  client.Disconnect();
```
* 显示错误信息
```C#
  IFTPClient client = FTPFactory.CreateClient("192.9.220.241", "vincent", "198959");
  client.Connect();
  Console.WriteLine(client.errormessage);
  Console.ReadLine();
  client.Disconnect();
```

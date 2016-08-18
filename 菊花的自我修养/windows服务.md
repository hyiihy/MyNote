# <center> Windows服务</center>
## 概念
- Windows是一种需要长期运行的应用程序，特别适合服务器环境
- 可以自己创建
- 可开机自启，可暂停和重启而不显示任何用户界面

## 安装Windows服务
Windows服务不同于普通Windows应用程序。不可能简简单单地通过运行一个EXE就启动Windows服务了。安装一个Windows服务应该通过使用.NET Framework提供的InstallUtil.exe来完成，或者通过诸如一个Microsoft Installer (MSI)这样的文件部署项目完成。

## 使用VS创建一个Windows服务
1. 新建一个项目
- 从一个可用的项目模板列表当中选择Windows服务
- 设计器会以设计模式打开
- 从工具箱的组件表当中拖动一个Timer对象到这个设计表面上 (注意: 要确保是从组件列表而不是从Windows窗体列表当中使用Timer)
- 设置Timer属性，Enabled属性为False，Interval属性30000毫秒
- 切换到代码视图页(按F7或在视图菜单当中选择代码)，然后为这个服务填加功能，即扩充System.ServiceProcess.Service类，重载以下方法：
      Dispose – 清除任何受控和不受控资源(managed and unmanaged resources)
      OnStart – 控制服务启动
      OnStop – 控制服务停止
示例代码：
```csharp
using System;
using System.Collections;
using System.ComponentModel;
using System.Data;
using System.Diagnostics;
using System.ServiceProcess;
using System.Configuration.Install;
using SysData.Db;

namespace serverTest
{
 public class Service1 : System.ServiceProcess.ServiceBase
 {
  private System.Timers.Timer timer1;
  /// <summary>
  /// 必需的设计器变量。
  /// </summary>
  private System.ComponentModel.Container components = null;

  public Service1()
  {
   // 该调用是 Windows.Forms 组件设计器所必需的。
   InitializeComponent();

   // TODO: 在 InitComponent 调用后添加任何初始化
  }

  // 进程的主入口点
  static void Main()
  {
   System.ServiceProcess.ServiceBase[] ServicesToRun;

   // 同一进程中可以运行多个用户服务。若要将
   //另一个服务添加到此进程，请更改下行
   // 以创建另一个服务对象。例如，
   //
   //   ServicesToRun = New System.ServiceProcess.ServiceBase[] {new Service1(), new MySecondUserService()};
   //
   ServicesToRun = new System.ServiceProcess.ServiceBase[] { new Service1() };

   System.ServiceProcess.ServiceBase.Run(ServicesToRun);
  }

  /// <summary>
  /// 设计器支持所需的方法 - 不要使用代码编辑器
  /// 修改此方法的内容。
  /// </summary>
  private void InitializeComponent()
  {
   this.timer1 = new System.Timers.Timer();
   ((System.ComponentModel.ISupportInitialize)(this.timer1)).BeginInit();
   //
   // timer1
   //
   this.timer1.Enabled = true;
   this.timer1.Interval = 30000;
   this.timer1.Elapsed += new System.Timers.ElapsedEventHandler(this.timer1_Elapsed);
   //
   // Service1
   //
   this.ServiceName = "Service1";
   ((System.ComponentModel.ISupportInitialize)(this.timer1)).EndInit();

  }

  /// <summary>
  /// 清理所有正在使用的资源。
  /// </summary>
  protected override void Dispose( bool disposing )
  {
   if( disposing )
   {
    if (components != null)
    {
     components.Dispose();
    }
   }
   base.Dispose( disposing );
  }

  /// <summary>
  /// 设置具体的操作，以便服务可以执行它的工作。
  /// </summary>
  protected override void OnStart(string[] args)
  {
   // TODO: 在此处添加代码以启动服务。
   this.timer1.Enabled = true;
   this.LogMessage("Service Started");
  }

  /// <summary>
  /// 停止此服务。
  /// </summary>
  protected override void OnStop()
  {
   // TODO: 在此处添加代码以执行停止服务所需的关闭操作。
   this.timer1.Enabled = false;
   this.LogMessage("Service Stopped");
  }

  private void LogMessage(string xMsg)
  {
   try
   {
      //这里向数据库中插入一条信息为 xMsg的记录，下边是我调用事先写好的Db类添加记录的方法，您也可以使用其他办法来写入数据库。
    //Db.QuerySQL("Insert into SysMsg (SysMsg) values ('"+xMsg+"')");
   }
   catch
   {
    //不做任何操作
   }
  }

  private void timer1_Elapsed(object sender, System.Timers.ElapsedEventArgs e)
  {
   LogMessage("检查服务运行！");
  }
 }
}
```






```JavaScript
//生成的预览和html不能高亮？
var s = "JavaScript syntax highlighting";
alert(s);
```

# Functional-Logger
实现多级日志管理/实现将日志保存到本地文件中，便于问题的快速定位和排查（Implementing multilevel log management/To save the log to the local file, it is convenient to locate and sort out the problem quickly）

#Instructions(使用说明)
使用说明：
-----------------------------------------------------------
-----------------------------------------------------------
-----------------------------------------------------------
1.将Logger.java导入项目
---------------------------------------
---------------------------------------
2.自定义XXApplication类继承于Application类

  在XXApplication类的onCreate方法中初始化Logger:
     @Override
    public void onCreate() {
        super.onCreate();

        //appCtx代表XXApplication的Context(上下文)
        //isWriter代表是否允许将日志文件保存到本地，值为：true/false
        //level代表允许打印的Log的最低级别，值为：VERBOSE、DEBUG、INFO、WARN、ERROR、ASSERT、CLOSE（代表不打印日志）
        Logger.initialize(Context appCtx, boolean isWriter, Level level);
        ...
    }
---------------------------------------
---------------------------------------
3.根据需要自行使用以下类别的日志：
    Logger.v(String tag, String msg);
    Logger.d(String tag, String msg);
    Logger.i(String tag, String msg);
    Logger.w(String tag, String msg);
    Logger.e(String tag, String msg);

    Logger.v(String tag, String msg, Throwable throwable);
    Logger.d(String tag, String msg, Throwable throwable);
    Logger.i(String tag, String msg, Throwable throwable);
    Logger.w(String tag, String msg, Throwable throwable);
    Logger.e(String tag, String msg, Throwable throwable);

    Logger.v(Object target, String msg);
    Logger.d(Object target, String msg);
    Logger.i(Object target, String msg);
    Logger.w(Object target, String msg);
    Logger.e(Object target, String msg);

    Logger.v(Object target, String msg, Throwable throwable);
    Logger.d(Object target, String msg, Throwable throwable);
    Logger.i(Object target, String msg, Throwable throwable);
    Logger.w(Object target, String msg, Throwable throwable);
    Logger.e(Object target, String msg, Throwable throwable);
---------------------------------------
---------------------------------------
4.提示---日志文件保存目录是：/sdcard/Android/data/包名/log/日志文件
     
      ---日志文件保存格式：年_月_日_时_分_秒.log
      
      ---日志打印格式：timeStamp+" "+"ThreadID:"+Process.myTid()+"/"+pkgName+"/"+level+"/"+tag+": "+msg+"\n"+throwable

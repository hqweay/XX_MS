一个终端的管理系统。（就是入门课程里的那种大作业）

有趣之处在于对项目结构瞎折腾，提供了 Config 类在启动时注入，可以实现应用的功能切换：

1. 基于内存
2. 基于内存并使用 txt 文件持久化
3. 基于数据库
4. C/S 分离

如下启动类：

```Java
public static void main(String[] args) {
  // new Config(); 内存读写
  // new Config().setLocalPersistence(true); 内存读写并持久化
  // new Config().setUseDB(true); 使用数据库
  // new Config().setCS(true); C/S 分离，需要启动 sys/ServerApplication
  // 优先级：setCS > setUseDB > setLocalPersistence > 啥都不干

  Config config = new Config().setCS(true);
  new HRApplication(config).run();
}
```


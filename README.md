一个终端的管理系统。（就是入门课程里的那种大作业）

有趣之处在于对项目结构瞎折腾，提供了 Config 类在启动时注入，可以实现应用的功能切换：

1. 基于内存
2. 基于内存并使用 txt 文件持久化
3. 基于数据库

如下启动类：

```Java
// HRApplication.java
public class HRApplication extends AbstractHRApplication {

  public static void main(String[] args) {
    // 当 localPersistence 为 false、useDB 为 false，使用内存保存数据且不持久化
    // 当 localPersistence 为 true、useDB 为 false，使用内存保存数据并使用 txt 文件持久化
    // 只要 useDB 为 true，使用数据库读写数据，不考虑持久化
    new HRApplication(new Config(false, true)).run();
  }
}

// Config.java
public Config(boolean localPersistence, boolean useDB) {
  this.localPersistence = localPersistence;
  this.useDB = useDB;
}
```

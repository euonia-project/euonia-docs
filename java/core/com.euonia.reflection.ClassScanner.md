# ClassScanner

> 扫描 classpath 中给定包下的类。支持基于目录的 classpath（典型于 IDE/开发环境）和基于 JAR 的 classpath（典型于打包部署环境）。仅使用标准 Java API —— 无第三方依赖。

- **Type**: class
- **Package**: `com.euonia.reflection`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### scan

> 扫描指定的包，并返回其中找到的所有非匿名、非合成的类。

- **Parameters**:
  - `packageName` (`String`): 完全限定包名（例如 `com.euonia.bus`）
- **Returns**: `List<Class<?>>` - 包中找到的 Class 对象列表

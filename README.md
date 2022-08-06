# 转载自[Gitee](https://gitee.com/ja-netfilter/ja-netfilter)

源项目地址 https://gitee.com/ja-netfilter/ja-netfilter

作者 [ja-netfilter](https://gitee.com/ja-netfilter)

本仓库 [Releases](https://github.com/JackFranklinTos/ja-netfilter/releases/tag/ja-netfilter) 为 JetBrains Toolbox App 、 ja-netfilter 、 jetbra三款整合包

------

# 个人版使用说明

## 使用 Toolbox App 下载

1. 下载安装 Toolbox App

2. 解压在 Relseases 中的下载的 ja-netfilter 、 jetbra

3. **`ja-netfilter` 文件夹要选择好位置存放，不能删除！！！**

4. 将 `jetbra` 子文件夹 `config-jetbrains` 中的三个CONF文件替换掉 `ja-netfilter`  子文件夹`config` 中的三个相同的CONF文件

5. 在 Toolbox App 中下好产品后，点击右侧菜单的设置，用任一编辑器进行 `编辑JVM选项...`

6. 在空白行复制如下三串代码

   ```
   --add-opens=java.base/jdk.internal.org.objectweb.asm=ALL-UNNAMED
   --add-opens=java.base/jdk.internal.org.objectweb.asm.tree=ALL-UNNAMED
   -javaagent:/absolute/path/to/ja-netfilter.jar
   ```

7. `-javaagent:` 路径设置如下

   ```
   ja-netfilter.jar 文件在 ja-netfilter 中
   例如我的 ja-netfilter.jar 路径为 D:\Programs\Toolbox\ja-netfilter\ja-netfilter.jar
   就将 -javaagent: 后面的内容改成 D:\Programs\Toolbox\ja-netfilter\ja-netfilter.jar
   改完后的三串代码如下所示：
   --add-opens=java.base/jdk.internal.org.objectweb.asm=ALL-UNNAMED
   --add-opens=java.base/jdk.internal.org.objectweb.asm.tree=ALL-UNNAMED
   -javaagent:D:\Programs\Toolbox\ja-netfilter\ja-netfilter.jar
   ```

8. 进入网站 https://3.jetbra.in/ 选择在线的 hostname 进入

9. 选择需要激活的产品鼠标悬停点击复制激活码，在 JetBrains 产品选择 `Activation code` 粘贴复制的激活码即可激活

------

# 官方版使用说明

# ja-netfilter 2022.2.0

### A Java Instrumentation Framework

## Usage

* download from the [releases page](https://gitee.com/ja-netfilter/ja-netfilter/releases)
* add `-javaagent:/absolute/path/to/ja-netfilter.jar` argument (**Change to your actual path**)
    * add as an argument of the `java` command. eg: `java -javaagent:/absolute/path/to/ja-netfilter.jar -jar executable_jar_file.jar`
    * some apps support the `JVM Options file`, you can add as a line of the `JVM Options file`.
    * **WARNING: DO NOT put some unnecessary whitespace characters!**
* or execute `java -jar /path/to/ja-netfilter.jar` to use `attach mode`.
* for **Java 17** you have to add at least these `JVM Options`:

  ```
  --add-opens=java.base/jdk.internal.org.objectweb.asm=ALL-UNNAMED
  --add-opens=java.base/jdk.internal.org.objectweb.asm.tree=ALL-UNNAMED
  ```

* edit your plugin config files: `${lower plugin name}.conf` file in the `config` dir where `ja-netfilter.jar` is located.
* the `config`, `logs` and `plugins` directories can be specified through **the javaagent args**.
  * eg: `-javaagent:/path/to/ja-netfilter.jar=appName`, your config, logs and plugins directories will be `config-appname`, `logs-appname` and `plugins-appname`.
  * if no javaagent args, they default to `config`, `logs` and `plugins`.
  * this mechanism will avoid extraneous and bloated `config`, `logs` and `plugins`.

* run your java application and enjoy~

## Config file format

```
[ABC]
# for the specified section name

# for example
[URL]
EQUAL,https://someurl

[DNS]
EQUAL,somedomain

# EQUAL       Use `equals` to compare
# EQUAL_IC    Use `equals` to compare, ignore case
# KEYWORD     Use `contains` to compare
# KEYWORD_IC  Use `contains` to compare, ignore case
# PREFIX      Use `startsWith` to compare
# PREFIX_IC   Use `startsWith` to compare, ignore case
# SUFFIX      Use `endsWith` to compare
# SUFFIX_IC   Use `endsWith` to compare, ignore case
# REGEXP      Use regular expressions to match
```


## Debug info

* the `ja-netfilter` will **NOT** output debugging information by default
* add environment variable `JANF_DEBUG=1` (log level) and start to enable it
* or add system property `-Djanf.debug=1` (log level) to enable it
* log level: `NONE=0`, `DEBUG=1`, `INFO=2`, `WARN=3`, `ERROR=4`

## Debug output

* the `ja-netfilter` will output debugging information to the `console` by default
* add environment variable `JANF_OUTPUT=value` and start to change output medium
* or add system property `-Djanf.output=value` to change output medium
* output medium value: [`NONE=0`, `CONSOLE=1`, `FILE=2`, `CONSOLE+FILE=3`, `WITH_PID=4`]
* eg: `console` + `file` + `pid file name` = 1 + 2 + 4 = 7, so the `-Djanf.output=7`

## Plugin system

* for developer:
    * view the [scaffold project](https://gitee.com/ja-netfilter/ja-netfilter-sample-plugin) written for the plugin system
    * compile your plugin and publish it
    * just use your imagination~

* for user:
    * download the jar file of the plugin
    * put it in the subdirectory called `plugins` where the ja-netfilter.jar file is located
    * enjoy the new capabilities brought by the plugin
    * if the file suffix is `.disabled.jar`, the plugin will be disabled


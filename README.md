# 转载自 Gitee

项目源 https://gitee.com/ja-netfilter/ja-netfilter

[releases page](https://github.com/JackFranklinTos/ja-netfilter/releases/tag/ja-netfilter) 为原作者插件、JetBrains Toolbox App、jetbra.zip整合包，后续更新

### package 0.1.0 使用说明
- 下载 `jetbrains-toolbox-1.25.12627.exe` 、 `ja-netfilter-2022.2.0.zip` 、 `jetbra.zip`
- 安装 `toolbox` , 可自行设置后下载所需的JetBrains产品
- 解压 `ja-netfilter-2022.2.0.zip` ，记住解压路径，不能删除压缩包内的 `ja-netfilter`文件夹！！！
- 解压 `jetbra.zip` ，复制 `jetbra`文件夹中的 `jetbra`文件夹中的 `config-jetbrains`文件夹中的 `dns.conf` 、 `power.conf` 、 `url.conf` 替换掉 `ja-netfilter`文件夹中的 `config`文件夹中的这三个文件
- 回到Toolbox主界面，点击已安装产品右边的选项，依次选择 `设置` 、 `配置` 、 `编辑JVM选项...` 、 以 `记事本` 方式打开（自行选择，建议取消勾选始终使用此应用打开.vmoptions文件）
- 在记事本中粘贴 `-javaagent:/absolute/path/to/ja-netfilter.jar` 、 `--add-opens=java.base/jdk.internal.org.objectweb.asm=ALL-UNNAMED` 、 `--add-opens=java.base/jdk.internal.org.objectweb.asm.tree=ALL-UNNAMED`
### 修改 javaagent:
- 以我为例，我的 `ja-netfilter.jar`文件路劲为 `D:\Programs\Toolbox\ja-netfilter\ja-netfilter.jar`
- 就将 `javaagent:/absolute/path/to/ja-netfilter.jar` 修改成 `javaagent:D:\Programs\Toolbox\ja-netfilter\ja-netfilter.jar`
- 特别注意的一点是，复制的 `/ja-netfilter.jar` 中的 `/` 要修改成 `\`
### 激活码激活
- 进入网站 https://3.jetbra.in/
- 选择在线的hostname进入
- 选择自己需要激活的产品复制激活码激活

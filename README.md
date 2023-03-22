## Tomcat源码构建步骤
网络参考地址:https://www.cnblogs.com/zzk0/p/14127315.html

### 安装ant
1. 下载地址:https://ant.apache.org/bindownload.cgi
2. 配置环境变量
```shell
#ant
export ANT_HOME=/Users/liboren/Applications/apache-ant-1.10.13
export PATH=${PATH}:${ANT_HOME}/bin
```
3. 输入 ant -version 成功即可

### 使用idea构建
1. 创建配置文件build.properties
```properties
base.path=/Users/liboren/OpenSource/tomcat/lib
```
2. 执行命令

```shell
ant ide-intellij
```




### 启动调试
org.apache.catalina.startup.BootStrap main方法

## Tomcat处理逻辑
### 结构划分
#### Connector连接器(未详细研究)
1. 监听端口,进行报文收发
2. 对报文进行编组装配,将其转换为Servlet规范可以识别的请求响应对象
#### Container容器结构 Engine->Host[`多个`]->Host[`多个`]->Wrapper[`多个`]
1. Engine - 相当于服务器
2. Host - 虚拟主机
3. Host - 应用
4. Wrapper - Servlet接口
#### 容器启动
1. Tomcat启动时候会依次循环加载以上结构
2. 然后在start过程中会依次遍历每个Wrapper并调用其init()方法



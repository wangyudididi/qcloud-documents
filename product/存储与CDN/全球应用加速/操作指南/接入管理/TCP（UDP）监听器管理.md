## 新增TCP/UDP 监听器
1. 登录 [全球应用加速控制台](https://console.cloud.tencent.com/gaap)，进入“接入管理”页面，单击指定通道的【ID/通道名】。
2. 进入到下一级页面，选择【TCP 监听器管理】/【UDP 监听器管理】>【新建】，可进入向导，具体配置如下：
 1. 配置监听器信息，用于设置加速的协议和端口映射关系。
![](https://main.qcloudimg.com/raw/05515f5f1b43c553b725258e95e4df4c.png)
**源站类型**：可以是 IP 地址或域名，但同一个监听器只支持一种类型。
**源端口**：指加速通道 VIP 的访问端口。端口规范：有效范围1 - 65535（21端口暂不开放），支持单个端口或连续端口范围，但端口不能重复，一次最多添加的连续端口20个，如8000 - 8019。
 2. 配置源站处理策略，即同一个监听器绑定多个源站的情况下，选择源站之间的调度策略。
![](https://main.qcloudimg.com/raw/950dd83a557906be1f162cb3622e5afa.png)
**轮询**：Round Robin 调度策略。
**轮询加权**：weighted RR（可以在绑定监听器时设置各源站的权重）。
**最小连接数**：在所有源站中选择连接数最小的源站优先进行调度。
>!源站类型为域名的监听器，仅支持“轮询”一种调度策略，如果域名解析出多个 IP，则每个解析的 IP 都按照轮询策略进行调度。
 3. 如果是 TCP 协议，需要配置健康检查机制。
![](https://main.qcloudimg.com/raw/0bfbd554eacf61cdc256b6f9c53cea7d.png)
**响应时长**：响应的超时时间（仅在“启用健康检查”情况下有效）。
**监控间隔**：前后两次健康检查的时间间隔（仅在“启用健康检查”情况下有效）。
当健康检查判断源站异常时，该源站将不再转发数据包，直至该源站健康检查状态恢复正常。

## 设置TCP/UDP 监听器
单击【TCP/UDP 监听器管理】标签页，在操作栏单击【设置】可以修改监听器名字、调度策略和健康检查参数等。

## 源站绑定
单击【TCP/UDP 监听器管理】标签页，在操作栏单击【源站绑定】，可选择多个源站进行绑定或解绑，如果未找到源站信息，则可能是源站类型不匹配或源站未添加在“源站管理”中。

如果监听器策略为“加权轮询”，则可以在绑定的同时设置源站的权重，范围1 - 100，按权重值占总权重的比例进行调度，如源站1的权重为60，源站2的权重为80，则源站1的调度比例为 60 / (60 + 80) = 42.8%，源站2的调度比例为57.2%。
![](https://main.qcloudimg.com/raw/3508a3b4d1535dcc9ee33e922a7f332f.png)
如果开启了健康检查，绑定源站后，健康检查即开始启动，可以通过监听器的状态来判断源站是否正常，加速通道只会向正常状态的源站进行数据包转发，异常的源站将不再转发数据包，直至该异常源站健康检查状态恢复正常后才重新转发。

未开启健康检查或 UDP 协议监听器，不论源站的状态如何，始终做数据包转发。
![](https://main.qcloudimg.com/raw/7142b3a642030d3019464e849f197ab1.png)

## 删除TCP/UDP 监听器
单击【TCP/UDP 监听器管理】标签页，在操作栏单击【删除】，可以删除指定的监听器，若监听器已绑定源站，则需要选中“允许强制删除绑定有源站的监听器”后，才能删除。删除后，该监听器的端口将停止加速。
![](https://main.qcloudimg.com/raw/03079357d59a83cb552e127d11aa0e8a.png)

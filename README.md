# Network
Some summmaries after relearning network.
### 整体逻辑
1.将SIGPIPE信号处理掉，因为该信号会导致进程结束
2.初始化epoll
3.创建socket
4.为创建完成的socket设置工作模式（阻塞、非阻塞）
5.为epoll设置事件
6.将新创建的socket添加至epoll
7.开始循环执行处理阶段
（1）.添加一个epoll_wait函数，等待事件的产生
（2）.处理接收到的信息
[1].循环处理事件，如果发现事件的描述符为监听描述符，转入链接处理
[2].否则，如果事件为正确信息，将其加入线程池

### Handling HTTP Request
要注意几个问题，检查格式是否正确，查看是GET还是POST，检查HTTP版本

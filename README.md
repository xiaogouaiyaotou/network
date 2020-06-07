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

### RAII机制
### 优雅关闭连接
### STL优先队列
优先队列的特点为，会将每次新加入的元素进行排序，根据开始的构造将最大/最小的元素置于队首，其利用了堆排序的方法 </br>
构造小根堆优先队列 priority_queue<int,vector<int>, greater<int> > q; </br>
 大根堆优先队列   priority_queue< int> q; </br>
### http长连接，短连接
 HTTP长短连接本质上还是TCP的长短连接。长短连接其实就是是否要长期保持服务器和客户端的联系。众所周知，客户端每次和服务器连接都需要三次握手，短连接即是每次交流都需要进行一次三次握手和四次握手。长连接即只进行一次三次握手，而后在整个网页打开阶段都不断开连接，一直到主动关闭连接。HTTP、1.1默认就使用长连接。此功能在HTTP/1.0后期版本中是可以选择开启的。

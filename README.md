# OS Assignment
## 何为作业调度和进程调度？
- 作业调度是**外存与内存**之间的调度，发生频率很低，使进程从**创建态到就绪态**的过程;   
而进程调度是从**内存到CPU**的调度，发生频率很高，使进程从**就绪态到运行态**的过程。  

### 作业调度算法
1. 先来先服务算法  
2. 短作业优先算法  
3. 高响应比优先算法
      
### 进程调度算法  
1. 时间片轮转算法  
2. 优先级调度算法   
3. 多级反馈队列算法  

### 具体调度算法：
1. 先来先服务(FCFS): 按照到达顺序，非抢占式，不会饥饿
2. 短作业/进程优先(SJF): 抢占/非抢占，会饥饿
3. 高响应比优先(HRRN): 综合考虑等待时间和要求服务事件计算一个优先权，非抢占，不会饥饿
4. 时间片轮转(RR): 轮流为每个进程服务，抢占式，不会饥饿
5. 优先级: 根据优先级，抢占/非抢占，会饥饿
6. 多级反馈队列: 
设置多个就绪队列，每个队列的进程按照先来先服务排队，然后按照时间片轮转分配时间片
若时间片用完还没有完成，则进入下一级队尾，只有当前队列为空时，才会为下一级队列分配时间片。
抢占式，可能会饥饿
   
## 简单描述一下流程
1. 先进行作业调度，从waitQueue中查询到达的作业，若作业到达则判断系统的资源是否满足该作业需求（磁带机、内存），
   若满足则分配资源，转换为就绪态进程放入readyQueue中供processExecute调用  
2. 在每一个进程调度执行之前，先查询等待队列得到下一个进程到达的时间作为nextCriticalTime，同当前进程的burstTime进行比较，
   取较小的值作为下一次时钟中断的值（就是交给进程调度的时间），时间到回到作业调度中，若进程调度执行完则返回作业号在作业调度中释放其资源。

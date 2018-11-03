2018年11月03日

## 线程

>**进程、线程、协程之概念理解**
> >**进程**：进程（Process）是计算机中的程序关于某数据集合上的一次运行活动，**是系统进行资源分配和调度的基本单位**，是操作系统结构的基础。在早期面向进程设计的计算机结构中，进程是程序的基本执行实体；在当代面向线程设计的计算机结构中，**进程是线程的容器**。程序是指令、数据及其组织形式的描述，**进程是程序的实体**。
>> 进程是一个具有独立功能的程序关于某个数据集合的一次运行活动。它可以申请和拥有系统资源，是一个动态的概念，是一个活动的实体。它不只是程序的代码，还包括当前的活动，通过程序计数器的值和处理寄存器的内容来表示。
>> 进程的概念主要有两点：   
>> **第一**，进程是一个实体。每一个进程都有它自己的地址空间，一般情况下，包括**文本区域（text region）、数据区域（data region）和堆栈（stack region）**。文本区域存储处理器执行的代码；数据区域存储变量和进程执行期间使用的动态分配的内存；堆栈区域存储着活动过程调用的指令和本地变量。     
>> **第二**，进程是一个“执行中的程序”。程序是一个没有生命的实体，只有处理器赋予程序生命时（操作系统执行之），它才能成为一个活动的实体，我们称其为进程。      
> 
>>**线程**：线程，有时被称为**轻量级进程(Lightweight Process，LWP），是程序执行流的最小单元**。一个标准的线程由线程ID，当前指令指针(PC），寄存器集合和堆栈组成。另外，线程是进程中的一个实体，是被系统独立调度和分派的基本单位，线程自己不拥有系统资源，只拥有一点儿在运行中必不可少的资源，但它可与同属一个进程的其它线程**共享进程所拥有的全部资源**。一个线程可以创建和撤消另一个线程，同一进程中的多个线程之间可以并发执行。由于线程之间的相互制约，致使线程在运行中呈现出间断性。线程也有**就绪、阻塞和运行三种基本状态**。就绪状态是指线程具备运行的所有条件，逻辑上可以运行，在等待处理机；运行状态是指线程占有处理机正在运行；阻塞状态是指线程在等待一个事件（如某个信号量），逻辑上不可执行。每一个程序都至少有一个线程，若程序只有一个线程，那就是程序本身。
>> 线程是程序中一个单一的顺序控制流程。进程内一个相对独立的、可调度的执行单元，是系统独立调度和分派CPU的基本单位指运行中的程序的调度单位。在单个程序中同时运行多个线程完成不同的工作，称为**多线程**。
> 
>>**协程**：一个程序可以包含多个协程，可以对比与一个进程包含多个线程，因而下面我们来比较协程和线程。我们知道多个线程相对独立，有自己的上下文，切换受系统控制；**而协程也相对独立，有自己的上下文，但是其切换由自己控制，由当前协程切换到其他协程由当前协程来控制。**
> 
>> **守护进程**:Daemon()程序是一直运行的服务端程序，又称为**守护进程**。通常在系统后台运行，没有控制终端，不与前台交互，Daemon程序一般作为系统服务使 用。Daemon是长时间运行的进程，通常在系统启动后就运行，在系统关闭时才结束。一般说Daemon程序在后台运行，是因为它没有控制终端，无法和前 台的用户交互。Daemon程序一般都作为服务程序使用，等待客户端程序与它通信。我们也把运行的Daemon程序称作守护进程。
所谓守护 线程，是指在程序运行的时候在后台提供一种通用服务的线程，比如垃圾回收线程就是一个很称职的守护者，并且这种线程并不属于程序中不可或缺的部分。因此， 当所有的非守护线程结束时，程序也就终止了，**同时会杀死进程中的所有守护线程**。反过来说，只要任何非守护线程还在运行，程序就不会终止。
>> 用户线程和守护线程两者几乎没有区别，唯一的不同之处就在于虚拟机的离开：如果用户线程已经全部退出运行了，只剩下守护线程存在了，虚拟机也就退出了。 因为没有了被守护者，守护线程也就没有工作可做了，也就没有继续运行程序的必要了。
> 
> >**进程间通信**(IPC，Inter-Process Communication)，指至少两个进程或线程间传送数据或信号的一些技术或方法。进程是计算机系统分配资源的最小单位。**每个进程都有自己的一部分 独立的系统资源，彼此是隔离的**。为了能使不同的进程互相访问资源并进行协调工作，才有了进程间通信。这些进程可以运行在同一计算机上或网络连接的不同计算 机上。
进程间通信技术包括消息传递、同步、共享内存和远程过程调用。IPC是一种标准的Unix通信机制。
使用IPC 的理由：1. 信息共享 2. 加速; 3. 模块化方便; 4. 私有权分离.    
主要的 IPC 方法:
　　1. 方法 提供方(操作系统或其他环境)
　　2. 文件 多数操作系统
　　3. 信号 多数操作系统
　　4. Socket 多数操作系统
　　5. 消息队列(en:Message queue) 多数操作系统
　　6. 管道(en:Pipe) 所有的 POSIX systems, Windows.
　　7. 命名管道(en:Named Pipe) 所有的 POSIX 系统, Windows.
　　8. 信号量(en:Semaphore) 所有的 POSIX 系统, Windows.
　　9. 共享内存 所有的 POSIX 系统, Windows.
　　10Message passing(en:Message passing) 用于 MPI规范，Java RMI, CORBA, MSMQ, MailSlot 以及其他.
  

### 线程的使用
一般有两种使用方法，一种是直接继承 Thread ，然后重写 run() 方法，另一种是实现 Runnable 接口，同样实现 run() 方法。两个都差不多，并没有明确的优劣之分，可以根据个人的喜好来使用不同的方法。


### 从线程返回信息
线程的运行时不确定的，它是直接交给操作系统去调度的，所以我们很难保证线程能及时准确的返回信息。    
解决方法：   
1.轮询方法，定期去轮询返回的信息，知道轮询成功才停止。这种会占用 cpu 的时间等，比较耗费资源
2.回调方法，这个相对比较轻松一些，可以在线程运行有结果后操作回调接口，那么就可以吧结果回调到需要结果的地方。
3.使用 Future 和 Callable 或者Executor 

> 大概操作流程是：创建一个 ExecutorService 的服务，向 executorService 提交 Callable 任务，获取结果的 Future 。需要注意的是，如果程序运行完有结果了，那么 future 可以解析对应的结果，如果程序没有运行完，就会阻塞的等待结果，知道成功运算出结果。这样好处是，你可以创建很多的线程，每个线程都会按照结果顺序返回结果值。


demo
``` java
import java.io.*;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class Main {

    public static void main(String[] args) {
        int[] data = {1,2,3,4,5,6,7,8,9,122,10};
        try {
            System.out.println(findMaxNumber(data));
        } catch (ExecutionException e) {
            e.printStackTrace();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }

    public static int  findMaxNumber(int[] data) throws ExecutionException, InterruptedException {
        if(data.length==0){
            throw  new IllegalArgumentException("数据为空");
        }
        if(data.length ==1){
            return data[0];
        }
        FindMaxTask task1 = new FindMaxTask(data,0,data.length/2);
        FindMaxTask task2 = new FindMaxTask(data,data.length/2,data.length);
        ExecutorService service  = Executors.newFixedThreadPool(2);
        Future<Integer> future1 = service.submit(task1);
        Future<Integer> future2 = service.submit(task2);
        return Math.max(future1.get(),future2.get());

    }
}


import java.util.concurrent.Callable;

public class FindMaxTask implements Callable<Integer> {
    private int[] data;
    private int start;
    private int end;

    public FindMaxTask(int[] data, int start, int end) {
        this.data = data;
        this.start = start;
        this.end = end;
    }
    @Override
    public Integer call() throws Exception {
        int max = Integer.MIN_VALUE;
        for(int i = start;i<end;i++){
            max =Math.max(max,data[i]);
        }
        return max;
    }
}
```


### 同步和互斥
基本概念
> **同步**：合作的并发进程需要按先后次序执行。
> **互斥**：当一个进程正在临界区中访问临界资源时，其他进程不能进入临界区。

同步的操作
使用 **synchronized** 关键字或者 使用 **Lock** 控制，轻量级的 同步机制 **volatile**
同步的替代方法
+ 使用局部变量。局部变量不存在同步问题，因为虚拟机每一次使用局部变量的时候，都会在新的一个栈帧中创建、使用、销毁局部变量，每个线程都有自己单独的一组局部变量。这种效果 **threadlocal** 可以实现，threadlocal 是线程内部数据存储类，每个线程有且仅有一份变量。
+ 使用线程安全的类，因为线程安全的类一般是不可以修改的（final），所以一经创建他们就不会改变。这样的类比如有 String ,Integer , Short , Byte, Long, Float,Double,Character,Boolean ,Void等等的包装类
+ 非线程安全的类用作为线程安全的类的一个私有字段。 **java.util.concurrent.atomic** 包中特意设计的为保证线程安全单可变的类。比如说，AtomicInteger 替代 Integer ,AtomicIntegerArray 替代 int[] 等。还有就是 **java.util.Collections**中  Collections.synchronizedSet(xxx) ,Collections.synchronizedList(xxx) ,Collections.synchronizedMap(xxx) ,

### 死锁

> 死锁是指两个或两个以上的进程在执行过程中，由于竞争资源或者由于彼此通信而造成的一种阻塞的现象，若无外力作用，它们都将无法推进下去。此时称系统处于死锁状态或系统产生了死锁，这些永远在互相等待的进程称为死锁进程。

造成死锁的条件是
1.互斥
2.占有且等待
3.不可剥脱
4.循环等待

### 线程优先级
每个线程默认的优先级都是 5，一般不用自己手动去设置优先级，除非很清楚知道某一个线程非常重要，不然很容易造成其他线程的“饥饿现象”。

``` java
   /**
     * The minimum priority that a thread can have.
     */
    public final static int MIN_PRIORITY = 1;

   /**
     * The default priority that is assigned to a thread.
     */
    public final static int NORM_PRIORITY = 5;

    /**
     * The maximum priority that a thread can have.
     */
    public final static int MAX_PRIORITY = 10;
```

如果确实需要修改优先级的，可以使用 setPriority(newPriority);方法

``` java
  * @param newPriority priority to set this thread to
     * @exception  IllegalArgumentException  If the priority is not in the
     *               range <code>MIN_PRIORITY</code> to
     *               <code>MAX_PRIORITY</code>.
     * @exception  SecurityException  if the current thread cannot modify
     *               this thread.
     * @see        #getPriority
     * @see        #checkAccess()
     * @see        #getThreadGroup()
     * @see        #MAX_PRIORITY
     * @see        #MIN_PRIORITY
     * @see        ThreadGroup#getMaxPriority()
     */
    public final void setPriority(int newPriority) {
        ThreadGroup g;
        checkAccess();
        if (newPriority > MAX_PRIORITY || newPriority < MIN_PRIORITY) {
            throw new IllegalArgumentException();
        }
        if((g = getThreadGroup()) != null) {
            if (newPriority > g.getMaxPriority()) {
                newPriority = g.getMaxPriority();
            }
            setPriority0(priority = newPriority);
        }
    }
	
	
	  /* Some private helper methods */
    private native void setPriority0(int newPriority);
```

### 放弃
要让线程放弃控制权，可以通过 yield() 显示的放弃。

``` java
 /**
     * A hint to the scheduler that the current thread is willing to yield
     * its current use of a processor. The scheduler is free to ignore this
     * hint.
     *
     * <p> Yield is a heuristic attempt to improve relative progression
     * between threads that would otherwise over-utilise a CPU. Its use
     * should be combined with detailed profiling and benchmarking to
     * ensure that it actually has the desired effect.
     *
     * <p> It is rarely appropriate to use this method. It may be useful
     * for debugging or testing purposes, where it may help to reproduce
     * bugs due to race conditions. It may also be useful when designing
     * concurrency control constructs such as the ones in the
     * {@link java.util.concurrent.locks} package.
     */
    public static native void yield();
```

### 休眠

对比 | wait() | sleep()
:------:|:--------:|:---------:
属于 | Object 类方法 | Thread的静态方法
锁 | 休眠的时候所拥有的锁会别释放 | 拥有的锁不糊被释放
唤醒 | 时间到了需要通过 notify () / notifyAll() 进行唤醒，并需要重新去竞争锁  | 时间到了就可以直接回复运行，锁没有被释放


**Object 类的 wait**
``` java

public final native void wait(long timeout) throws InterruptedException;、

public final void wait(long timeout, int nanos) throws InterruptedException {
        if (timeout < 0) {
            throw new IllegalArgumentException("timeout value is negative");
        }

        if (nanos < 0 || nanos > 999999) {
            throw new IllegalArgumentException(
                                "nanosecond timeout value out of range");
        }

        if (nanos > 0) {
            timeout++;
        }

        wait(timeout);
    }
	
	
	 public final void wait() throws InterruptedException {
        wait(0);
    }

```

**Thread.sleep()**

``` java
 public static native void sleep(long millis) throws InterruptedException;
 public static void sleep(long millis, int nanos)  throws InterruptedException {
        if (millis < 0) {
            throw new IllegalArgumentException("timeout value is negative");
        }

        if (nanos < 0 || nanos > 999999) {
            throw new IllegalArgumentException(
                                "nanosecond timeout value out of range");
        }

        if (nanos >= 500000 || (nanos != 0 && millis == 0)) {
            millis++;
        }

        sleep(millis);
    }
```

### 中断停止 interrupt
一般来说，线程自己运行完就会 自动释放掉，但是如果想中断线程的执行过程可以使用 interrupt() 进行操作。

``` java
 public void interrupt() {
        if (this != Thread.currentThread())
            checkAccess();

        synchronized (blockerLock) {
            Interruptible b = blocker;
            if (b != null) {
                interrupt0();           // Just to set the interrupt flag
                b.interrupt(this);
                return;
            }
        }
        interrupt0();
    }
	
	
private native void interrupt0();
```

### 连接线程
一个线程如果需要其他线程的结果，这个时候就需要等待其他线程一起完成后在统一处理该线程。使用 join() 函数的时候前面执行的线程都会执行完，如果有的线程执行的快，就需要等待执行比较慢的线程，等所有的线程都运行完之后在执行 join() 后面的线程。

``` java
public final synchronized void join(long millis) throws InterruptedException {
        long base = System.currentTimeMillis();
        long now = 0;

        if (millis < 0) {
            throw new IllegalArgumentException("timeout value is negative");
        }

        if (millis == 0) {
            while (isAlive()) {
                wait(0);
            }
        } else {
            while (isAlive()) {
                long delay = millis - now;
                if (delay <= 0) {
                    break;
                }
                wait(delay);
                now = System.currentTimeMillis() - base;
            }
        }
    }
	
	
public final synchronized void join(long millis, int nanos) throws InterruptedException {

        if (millis < 0) {
            throw new IllegalArgumentException("timeout value is negative");
        }

        if (nanos < 0 || nanos > 999999) {
            throw new IllegalArgumentException(
                                "nanosecond timeout value out of range");
        }

        if (nanos >= 500000 || (nanos != 0 && millis == 0)) {
            millis++;
        }

        join(millis);
    }
	
public final void join() throws InterruptedException {
        join(0);
    }

```

### 唤醒
当线程在等待资源的时候使用了 wait()等函数，其他线程使用完资源之后就会通知 有可用的资源了，这个时候 notify（）和 notifyAll（）就登场了.notify() 基本上回随机的从等待的这个对象的线程列表中选择一个线程，并将他唤醒。nitifyAll() 犯法会唤醒等待对象的每一个线程，全部线程一起去竞争资源，最后只有一个线程得到资源，其他的又进入等待的情况


Object 类的方法
``` java
    public final native void notify();
	 public final native void notifyAll();
```

### 线程池
为了程序中频繁的创建线程，可以采用线程池。
线程池的好处
1.避免线程的频繁创建和销毁带来的开销，提高了线程的复用性。
2.可以对线程进行控制，可以指定周期性的执行线程
3.可以控制线程的并发量，提高响应的速度

submit() 将 Runnable 或者 Callable 提交给线程池操作，通过 shutdown（）操作可以停止插入任务，正在运行的任务不受中断的影响，正在运行的任务会自己运行完。shutdownNow() 会终止当前正在运行的任务。






参考资料
1. [《进程、线程、协程之概念理解》](https://www.cnblogs.com/work115/p/5620272.html)
2. [《死锁》](https://baike.baidu.com/item/%E6%AD%BB%E9%94%81/2196938?fr=aladdin)
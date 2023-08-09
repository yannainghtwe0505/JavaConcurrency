# JavaConcurrency

Before Reading this section **you must know what is functional interface and how they work.**
<br>
# most used functional interface in concurrency

Runnable->Functional interface that return void<br>
Callable->Functional interface that return value and throw checked exceptions

# Service API
ExecutorService<br>
ScheduleExecutorService

# Create Service API instance
ExecutorService service = Executors.newSingleThreadExecutor();<br>
ScheduledExecutorService service = Executors.newSingleThreadScheduledExecutor();<br>
ExecutorService service = Executors.newCachedThreadPool();<br>
ExecutorService service = Executors.newFixedThreadPool();<br>
ScheduledExecutorService service = Executors.newScheduledThreadPool();<br>
![image](https://github.com/yannainghtwe0505/JavaConcurrency/assets/95702171/f0f9d8a7-62d4-4e50-9067-ea65ddf3f24d)

# ExecutorService  methods
execute(Runnable arg)<br>
submit(Runnable arg)<br>
submit(Callable arg)<br>
invokeAll(?)<br>
invokeAny(?)

# ScheduleExecutorService methods
schedule()<br>
schedule()<br>
scheduleAtFixedRate() with time fixed<br>
scheduleWithFixedDelay() if finish

# volatile and Atomic
The **volatile** keyword indicates that the variable's value may be modified by multiple threads concurrently.<br>

**Atomic** is the property of an operation to be carried out as a single unit of execution without any interference from another thread.<br>
eg.eg.AtomicInteger sheepCount 3 new AtomicInteger(0);

# synchronize
 private void incrementAndReport() {
        synchronized (this) {
            System.out.print((++sheepCount) + " ");
        }
    }
# CyclicBarrier
 try {
            removeLions();
            c1.await();
            cleanPen();
            c2.await();
            addLions();
            c2.await();
            addLions2();
        }

  try {
            var manager = new LionPen_with_CyclicBarrier();
            var c1 = new CyclicBarrier(4);
            var c2 = new CyclicBarrier(4, () -> System.out.println("*** Pen Cleaned!"));
            for (int i = 0; i < 4; i++)
                service.submit(() -> manager.performTask(c1, c2));
        } finally {
            service.shutdown();
        }      

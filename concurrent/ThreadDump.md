ThreadDump HelloWorld

```

import com.alibaba.fastjson.JSON;
import java.lang.management.ManagementFactory;
import java.lang.management.ThreadMXBean;
import java.util.concurrent.ArrayBlockingQueue;
import java.util.concurrent.BlockingQueue;
import java.util.concurrent.ConcurrentHashMap;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.ThreadPoolExecutor;
import java.util.concurrent.TimeUnit;

public class SqlUtil {

	private static ConcurrentHashMap<String, Long> threadMap = new ConcurrentHashMap<>();
	static BlockingQueue<Runnable> queue = new ArrayBlockingQueue<>(10);
	static ExecutorService executorService = new ThreadPoolExecutor(2, 5, 6, TimeUnit.SECONDS, queue);

	public static void main(String[] args) {
		submit("task1");
		submit("task2");

		ThreadMXBean threadMXBean = ManagementFactory.getThreadMXBean();
		StackTraceElement[] stack1 = threadMXBean.getThreadInfo(threadMap.get("task1"), 100).getStackTrace();
		StackTraceElement[] stack2 = threadMXBean.getThreadInfo(threadMap.get("task2"), 100).getStackTrace();

		System.out.println(JSON.toJSONString(stack1));
		System.out.println(JSON.toJSONString(stack2));
	}

	public static void submit(final String name) {
		executorService.submit(new Runnable() {
			@Override
			public void run() {
				Thread thread = Thread.currentThread();
				threadMap.put(name, thread.getId());
				thread.setName(name);
				System.out.println(thread.getName());
				if (name.equals("task1")) {
					try {
						Thread.sleep(5*1000);
					} catch (InterruptedException e) {
						e.printStackTrace();
					}
				} else {
					try {
						Thread.sleep(5*1000);
					} catch (InterruptedException e) {
						e.printStackTrace();
					}
				}

			}
		});
	}

}

```

# Q2 reverse array
```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

int n;
int *results;
void *runn(void *param); // the thread function

int main(int argc, char **argv)
{
    n = atoi(argv[1]);
    results = (int *)malloc(n * sizeof(int)); // dynamic array
    pthread_t tid[n]; // the thread identifier
    // initializing array
    for (int i = 0; i < n; ++i)
    {
        results[i] = rand() % 5;
        printf(" %d ", results[i]);
    }
    //creating threads
    for (int i = 0; i < n / 2; ++i)
    {
        pthread_create(&tid[i], NULL, runn, (void *)(i)); // create the thread
    }
    for (int i = 0; i < n; ++i)
    {
        pthread_join(tid[i], NULL); // wait for the thread to exit
    }
    // printing reversed array
    for (int i = 0; i < n; ++i)
    {
        printf(" %d ", results[i]);
    }
}
void *runn(void *param)
{ // the thread will begin control in this function
    int i = (int)param;
    int temp = results[i];
    
    results[i]= results[(n-1) - i];
    results[(n-1) - i] = temp;

    pthread_exit(0); // thread exit
}
```
- in java
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
 
public class Driver {
  private static class CThread implements Runnable {
    private List<Integer> list;
    private int index;
 
    public CThread(List<Integer> list, int index) {
      this.list = list;
      this.index = index;
    }
 
    public void run() {
      System.out.printf("%s swap indices %d and %d\n",
                        Thread.currentThread().getName(), index,
                        list.size() - (this.index + 1));
      Collections.swap(list, this.index, list.size() - (this.index + 1));
    }
  }
 
  public static void main(String[] args) {
    final int size = Integer.parseInt(args[0]);
    List<Integer> list = new ArrayList<Integer>();
    for (int index = 0; index < size; ++index) {
      list.add(index);
    }
    Collections.shuffle(list);
 
    System.out.println(list);
 
    List<Thread> threads = new ArrayList<Thread>();
    for (int index = 0; index < size / 2; ++index) {
      Thread thread = new Thread(new CThread(list, index));
      threads.add(thread);
      thread.start();
    }
    
    try {
      for (Thread thread : threads) {
        thread.join();
      }
    } catch (InterruptedException e) {
      e.printStackTrace();
    }
    
    System.out.println(list);
  }
}
```
# Q3 A. Text Matching
```java
public class Service implements Runnable {
	
	Socket nextClient;
	
	public Service(Socket nextClient) {
		this.nextClient = nextClient;
	}

	@Override
	public void run() {
		// initializing input and output streams
		PrintWriter output = new PrintWriter(nextClient.getOutputStream(),true);
		
		BufferedReader reader = new BufferedReader(new InputStreamReader(nextClient.getInputStream()));
		
		String text1 = reader.readLine();
		String text2 = reader.readLine();

		if (text1.equalsIgnoreCase(text2))
			output.println("Matching Texts");
		else 
			output.println("Non-matching Texts");
			
		nextClient.close();
}
```
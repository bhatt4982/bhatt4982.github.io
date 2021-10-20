# Concurrency (in C++)

## Threads

```c++
#include<thread>
std::thread thread_object(callable)
```

A callable can be either of the three

- A function pointer

  ```c++
  void printNums(int N) {
  
  	for (int i = 1; i <= N; i++) {
  		cout << i << endl;
  	}
  }
  
  int main() {
  	thread t(printNums, 10);
  	t.join();
  	return 0;
  }
  
  ```

  

- A function object

  ```c++
  class PrintNums {
  public:
  	void operator()(int N)
  	{
  		for (int i = 1; i <= N; i++) {
  			cout << i << endl;
  		}
  	}
  };
  
  int main() {
  	thread t(PrintNums(), 10);
  	t.join();
  	return 0;
  }
  ```

  

- A lambda expression

  ```c++
  auto f = [](int N) {
      for (int i = 1; i <= N; i++) {
          cout << i << endl;
      }
  };
  
  thread t(f, 10);
  t.join();
  ```

  ```c++
  thread t([](int N) {
      for (int i = 1; i <= N; i++) {
          cout << i << endl;
      }
  }, 10);
  t.join();
  ```

  

#### Max supported threads

##### Computation Intensive

```c++
unsigned int numThreads = std::thread::hardware_concurrency();
// returns the total number of supported concurrency.
```

A single CPU core can have up-to 2 threads per core. If we have 2 CPUs (8 cores) each of which can support 16 threads, hardware_concurrency() will be equal to 32.

In case, we restrict CPU usage (Lets say to 1, using command like numactl), hardware_concurrency() will still return unrestricted value.

##### IO Intensive

For I/O-bound threads, the question is what precise kind of I/O is involved here. 

If the contested resource is a hard disk drive, then more than one concurrent access will slow things down.

If the contested resource is a network interface, then any number of threads can access it without any problems as long as the total bandwidth of the interface is not exceeded.

For I/O bound threads the number of CPU cores is completely irrelevant. In fact you don't need multiple threads to do parallel I/O: asynchronous I/O and event-based systems are entirely sufficient here.

**RAID** - Redundant Array of Inexpensive Disks can help in such scenarios as it supports parallel IO

## Thread Pool

Creating and destroying a thread takes some time and has some overhead in terms of CPU resources, so ideally you will have a thread pool that has the **worker threads** started and sleeping, while another **dispatcher thread** will be responsible for batching and sending the work to the worker threads.

## Async

```c++
#include <future>
using namespace std;
void printNums(int N)
{
	for (int i = 1; i <= N; i++) {
		cout << i << endl;
	}
}

int main() {
	auto future = async(launch::async, [] { printNums(10); });
	future.wait();
	return 0;
}
```



## Thread Synchronization

### Mutex

**MUT**ual **EX**clusive access to shared data

```c++
#include <mutex> // Header
std::mutex mutex_name; // Declaration
mutex_name.lock(); // Acquire the mutex
mutex_name.unlock(); // Release the mutex
```

#### Problems

* If `unlock()` is not called, behavior is undefined.
* If exception is thrown before `unlock()`, `unlock()` will never called - which leads to undefined behavior.

#### Solution - lock_guard

`lock_guard()` - always guarantees to unlock the mutex using the RAII (Resource Acquisition Is Initialization) paradigm | the raw mutex is encapsulated inside a `lock_guard()` that invokes `lock()` at its construction and `unlock()` at its destruction, when it exits its scope.



````c++
std::lock_guard<std::mutex> lg(mutex_obj);
````

### Examples

1. Print odd and even numbers using threads.

   ```c++
   mutex gMutex;
   
   int num = 1;
   int N = 10;
   
   void printEvenfunc() {
   	while (true) {
   		gMutex.lock();
   		if(num <= N && num % 2 == 0 )
   			cout << num++ << endl;
   		gMutex.unlock();
   		if (num > N)
   			break;
   	}
   }
   
   void printOddfunc() {
   	while (true) {
   		gMutex.lock();
   		if (num <= N && num % 2 != 0)
   			cout << num++ << endl;
   		gMutex.unlock();
   		if (num > N)
   			break;
   	}
   }
   
   
   int main() {
   	thread print_odd(printOddfunc);
   	thread print_even(printEvenfunc);
   
   	print_odd.join();
   	print_even.join();
   
   	return 0;
   }
   ```
   
   
   
   ```c++
   // using shared_mutex
   // as mutex will give error - Unlock of unowned mutex
   shared_mutex evenMutex, oddMutex;
   
   int num = 1;
   int N = 10;
   
   void printEvenfunc() {
	while (true) {
   		evenMutex.lock();
   		if (num > N) {
   			evenMutex.unlock();
   			oddMutex.unlock();
   			return;
   		}
   		cout << num++ << endl;
   		oddMutex.unlock();
   	}
   }
   
   void printOddfunc() {
   	while (true) {
   		oddMutex.lock();
   		if (num > N) {
   			evenMutex.unlock();
   			oddMutex.unlock();
   			return;
   		}
   		cout << num++ << endl;
   		evenMutex.unlock();
   	}
   }
   
   int main() {
   
   	evenMutex.lock();
   	oddMutex.lock();
   
   	thread print_odd(printOddfunc);
   	thread print_even(printEvenfunc);
   
   	oddMutex.unlock();
   
   	print_odd.join();
   	print_even.join();
   
   	return 0;
   }
   
   ```
   
   
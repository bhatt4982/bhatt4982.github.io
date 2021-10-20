# Memory Management



## Memory Layout

### Address space

* global
* static
* local
* runtime

### Memory Sections

| Section      | Purpose                      |
| ------------ | ---------------------------- |
| Stack        | Local Variables              |
| Heap         | Dynamically allocated memory |
| Data Segment | Global and static variables  |
| Code Segment | Program executable code      |

**Note:** Modern system uses technique called **Address Space Layout Randomization (ASLR)** - that is used to increase the difficulty of performing a **buffer overflow attack** that requires the attacker to know the location of an executable in memory. 

## Byte Ordering

Order in which bytes are stored in the memory

Example: 

int: 4 byte

(Dec) 2143055809 (Hex) 7FBC6FC1

Most Significant Byte(MSB) - 7F 

Least Significant Byte(LSB) - C1

1. Big Indian - most significant byte is stored first - 7F BC 6F C1
   * used by IBM
2. Little Indian - least significant byte is stored first - C1 6F BC 7F
   * used by Intel

## Dynamic Memory Allocation

* Allocated in Heap at runtime
* Can be accessed through out the program
* Available during program runtime, unless explicitly released
* Has to be released explicitly by programmer

### C-style memory allocation

#### sizeof

* Queries size of the object or type.

```c++
size_t unsigned int sizeof(data_type);
```

```c++
cout << sizeof(char) << endl;
cout << sizeof(int) << endl;
cout << sizeof(unsigned int) << endl;
cout << sizeof(long) << endl;
cout << sizeof(long long) << endl;
----
Output:
1
4
4
4
8
```



#### free

* Deallocate memory block

```c++
void free (void* ptr);
```



#### malloc

Allocate memory block

```c++
void* malloc (size_t size);
```

```c++
int *ptr = (int*)malloc(sizeof(int));
*ptr = 4982;
cout << *ptr << endl;
free(ptr);
----
Output:
4982
```



#### calloc

Allocate and zero-initialize array

```c++
void* calloc (size_t num, size_t size);
```

```c++
int *ptr = (int*)calloc(1, sizeof(int));
*ptr = 4982;
cout << *ptr << endl;
free(ptr);
----
Output:
4982
```



#### realloc

Reallocate memory block

```c++
void* realloc (void* ptr, size_t size);
```

```c++
// allocate memory for 1 int
int *ptr = (int*)calloc(1, sizeof(int));
*ptr = 4982;
// re-allocate memory to same pointer for 2 int
ptr = (int*)realloc(ptr, 2*sizeof(int));
*(ptr+1) = 4983;
cout << *ptr << endl;
cout << *(ptr+1) << endl;
free(ptr);
----
Output:
4982
4983
```

#### limitations

* Cannot initialize (expect calloc that initializes to 0)
* malloc, calloc, realloc - does not call constructor
* free - does not call destructor
* Cannot be customized
* Return NULL on failure (Always check for NULL after memory allocation)

### C++ style memory allocation

* new - to allocate - on success constructor is invoked
* delete - to free - on destructor constructor is invoked
* new[] or delete[] - to allocate and free array

```c++
// allocate memory, but do not initialize
int *ptr = new int;
cout << *ptr << endl;
delete ptr;
----
Output
<garbage>
######
// allocate memory and initialize to 0
int *ptr = new int(); //new int{};
cout << *ptr << endl;
delete ptr;
----
Output
0
######
// allocate memory and initialize to val
int *ptr = new int(4982); //new int{4982};   
```



```c++
// allocate and initialize array
int *ptr = new int[7]{1, 2, 3, 4};
for(int i = 0; i < 7 ; i++)
    cout << *(ptr+i) << " ";
cout << endl;
delete[] ptr;
```

* If memory cannot be allocated, new throws **bad_allocation exception**

  ```c++
  try {
      int *ptr = new int[INT_MAX / 5];
      delete ptr;
  }
  catch (exception &ex) {
      cout << "exception - " << ex.what() << endl;
  }
  ----
  Output
  exception - bad allocation
  ```

  

* use nothrow version of new to avoid exception

  ```c++
  int *ptr = new(std::nothrow) int[INT_MAX/5];
  ```

* Also, new handler function can be set to handle exception - it calls new handler function repeatedly till memory is available.

  ```c++
  void newHandler() {
  	cout << "Catches exception" << endl;
  }
  
  int main() {
  	std::set_new_handler(newHandler);
  	int *ptr = new int[INT_MAX/5];
  	delete ptr;
  	
  	return 0;
  }
  ```

  

#### Placement New

* allocates memory at  the address specified by the user
* used in memory pool
* useful in embedded systems
* destructor should be called explicitly for such objects

```c++
Type *ptr = new(<memmory_address>)Type{};
```

```c++
class CustomType {
public:
	CustomType() {
		cout << "CustomType Construtor..." << endl;
	}
	~CustomType() {
		cout << "CustomType Destrutor..." << endl;
	}
};

int main() {
	char buff[10];
	CustomType *ptr = new(buff) CustomType{};
	//delete ptr;
	ptr->~CustomType();
    
	return 0;
}
----
Output
CustomType Construtor...
CustomType Destrutor...

```

```c++
class CustomType {
public:
	int num;
	CustomType(int n) {
		num = n;
		cout << "CustomType Construtor..." << endl;
	}
	~CustomType() {
		cout << "CustomType Destrutor..." << endl;
	}
};

int main() {
	const int N = 3;
	// allocates memory for objects - does not call construtor
	CustomType *ptr = static_cast<CustomType*>(operator new(N * sizeof(CustomType)));
	
	for (int i = 0; i < N; i++) {
		// placement new
		// constructor called
		new(ptr + i) CustomType{ i };
	}
	for (int i = 0; i < N; i++) {
		cout << (ptr + i)->num << endl;
	}

	for (int i = 0; i < N; i++) {
		(ptr + i)->~CustomType();
	}
	operator delete(ptr);
	return 0;
}
----
Output:
CustomType Construtor...
CustomType Construtor...
CustomType Construtor...
0
1
2
CustomType Destrutor...
CustomType Destrutor...
CustomType Destrutor...
```
# Input & Output

## Speed

### Fast cin/cout

```c++
ios_base::sync_with_stdio(false);
cin.tie(NULL);
```

* `ios_base::sync_with_stdio(false)` It toggles **on** or **off** the **synchronization of all the C++ standard streams** with their corresponding standard C streams if it is called before the program performs its first input or output operation.
* `cin.tie(NULL)` - a method which simply guarantees the flushing of `cout` before `cin` accepts an input.

* Use `cout("\n")` instead of `endl`

### printf/scanf



## Precision

### cout

```c++
#include <iomanip>
cout << setprecision(5);
```

### printf



## File IO

### cin

```c++
freopen("input.txt", "r", stdin); 
```


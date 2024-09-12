# FunctionObjectPointer
C++ program to demonstrate how to pass functions as parameters using std::function. Here's an explanation and breakdown of the code:

## Key Concepts:
1. **Function Pointers**: In C++, functions can be passed as parameters to other functions using pointers. However, `std::function` is a more flexible way to handle callable objects (functions, lambdas, etc.).

2. `std::function`: This is a wrapper around callable objects (like functions, lambdas, or functors) and provides more versatility. You can use it to pass different kinds of callable entities as parameters to other functions.

## Code breakdown
```
#include <functional>
#include <iostream>
using namespace std;

// Define add and multiply to return respective values
int add(int x, int y) { return x + y; }
int multiply(int x, int y) { return x * y; }
```
Here, two functions add and multiply are defined to add and multiply two integers, respectively.
```
// Function that accepts an object of type std::function<> as a parameter
int invoke(int x, int y, function<int(int, int)> func)
{
    return func(x, y);
}
```
  - The `invoke` function takes three parameters: two integers x and y, and a `std::function` object `func` that expects two integers as input and returns an integer.
  - Inside the function, `func` is invoked with x and y as arguments, and the result is returned.
This function allows you to pass any callable object (function, lambda, etc.) that matches the signature `int(int, int)`.

```
int main()
{
    // Pass the required function as a parameter using its name
    cout << "Addition of 20 and 10 is ";
    cout << invoke(20, 10, &add) << '\n';

    cout << "Multiplication of 20 and 10 is ";
    cout << invoke(20, 10, &multiply) << '\n';

    return 0;
}
```
In the main function:
  - The invoke function is called twice. The first call passes `&add`, a pointer to the add function, and the second call passes `&multiply`, a pointer to the multiply function.
  - As `invoke` is called, it executes the function (`add` or `multiply`) with the given arguments (20 and 10), and prints the result.
Output:
```
Addition of 20 and 10 is 30
Multiplication of 20 and 10 is 200
```
## Advantages of Using std::function:
  - **Flexibility**: The `std::function` type is highly versatile and can store pointers to functions, lambdas, or even objects that overload the operator().
  - **Polymorphism** for Callable Objects: You can change the behavior of the invoke function by passing different types of functions or callables, which enhances modularity.
This approach provides a clean way to manage and invoke functions dynamically, making it useful for scenarios where functions need to be passed around as first-class citizens.


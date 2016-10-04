# Homework #3

##### by Xuenan Xu GWID G26980825
&nbsp;

**1**
```javascript
function sub1() {
	function sub2() {
		return x;
	}
	function sub3() {
		var x = 3;
		return sub4(sub2);
	}
	function sub4(subx) {
 		var x = 4;
		return subx();
	}
	var x = 2;
	return sub3();
}
```
The call of `sub1()` will return 2. `sub1()` calls `sub3()`, and then `sub3()` call `sub4(subx)`, and finally `sub4(subx)` calls `sub2()`, so the return value is totally determined by `sub2()`, which didn't define `x` as its local variable, so the `return x;` in `sub2()` will return the global `x` defined in `sub1()`.

**2**
```javascript
function makeAdder(x) {
	return function(y) {return x + y;}
}
function closure() {
	var add10 = makeAdder(10);
	var add5 = makeAdder(5);
	return add10(20) + add5(30);
}
```
The call `closure()` will return 65. In `makeAdder(x)` there is a definition of `return function(y) {return x + y;}`, this definition means that we can attach a parameter to variables that is calculate with `makeAddr(x)` and the attached parameter will be the `y` in the inner definition. I did some test to prove that, by added some log to `makeAddr(x)`:
```javascript
function makeAdder(x) {
	console.log("makeAdder" + x)
	return function(y) {
		console.log("function" + y)
		return x + y;
	}
}
```
This time the call `closure()` will return some logs shown below:
```
makeAdder10
makeAdder5
function20
function30
=> 65
```
We can see from the test that by calling `var add10 = makeAdder(10)`, this `add10` is something like a function, not a integer or float or other regular type of variables, so the `return` statement in `closure()` called 2 functions on 2 integers, and the return value is `(20 + 10) + (30 + 5) = 65`.

**3**
```c
#include "stdio.h"

int func1(int x, int y) {
	return (x*x + y*y);
};

int main(void) {
	int (*ptrFunc1)(int, int) = func1;
	printf("%d", ptrFunc1(5, 10));
    return 0;
}
```
I wrote the program in a typical C program, like shown above. The result shall be `5 * 5 + 10 * 10 = 125`. The definition of `int (*ptrFunc1)(int, int) = func1;` defined a pointer named `ptrFunc1` for `func1`, the pointer is like a alias and works exactly the same as its source.

&nbsp;
> Written with [Atom](https://atom.io/).


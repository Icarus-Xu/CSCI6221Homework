# Homework #2

##### by Xuenan Xu GWID G26980825
&nbsp;

**1**
```java
// a)
int intArray[] = {1, 2, 3};
int index = 3;
if(index < 4 && intArray[index++] > 0) {
	System.out.format("%d", index);
} else {
	System.out.format("%d", index);
}

// b)
int intArray[] = {1, 2, 3};
int index = 5;
if(index < 4 && intArray[index++] > 0) {
	System.out.format("%d", index);
} else {
	System.out.format("%d", index);
}
```

_**a**_ will produce a `ArrayIndexOutOfBoundsException` because when judging `if` statement, `index < 4` returns true, then the program proceed to check  `intArray[index++] > 0` and that will cause access to a out of bound value, which produce the exception above.

_**b**_ will not produce such out of bound exception, but print `5` instead. That is because when judging the `if` statement, `index < 4` returns false, then the whole statement must be false no matter what  `intArray[index++] > 0` returns. The program then automatically skipped the judgement of the latter statement, and proceed to the contents in the `if` statement.

**2**
```perl
#!/usr/local/bin/perl

$name = "Mark Zuckerberg";
$age = 32;
$status = ($age > 60) ? "A senior citizen"
 					 : "Not a senior citizen";
print "$name is $status\n";
```

The output shall be `"Mark Zuckerberg is Not a senior citizen"`

**3**
```python
for n in range(15, 20):
	for x in range(2, n):
		if n % x == 0:
			print '%d = %d * %d' % (n, x, n / x)
			break
	else:
		print n, ' is a prime number'
```

The program is to find prime numbers in [15, 20), the domain is specified in the first `for` statement. In the second `for` statement, the program divided n by numbers in [2, n) in order to find factors of n. If the code in the second `for` statement never runs, which means `n` is a prime number, the program comes to the `else` statement.
The output shall be:
```
15 = 3 * 5
16 = 2 * 8
17  is a prime number
18 = 2 * 9
19  is a prime number
```

**4**
```c
int input = 1;
switch(input) {
	case 1:
		printf("case #1\n");
	case 2:
		printf("case #2\n");
	default:
		printf("default case\n");
}
```
The `case` statement is kind of like `goto`, they are symbols, not determination statements. That means in `switch-case` structure, codes in `case` statements run in order. We can write pseudocode for `switch-case` structures:
```
{
    if(b==1)goto case 1;
    else if(b==2)goto case 2;
    else if(b==3)goto case 3;
    else goto default;
    goto end_of_switch;
    {
    	case 1: ...
    	case 2: ...
    	case 3: ...
    	default: ...
    	end_of_switch:
    }
}
```
We use `break` statement at the end of `case` in order to skip the codes in other `case` statements, . There is no break in this switch-case structure, so the output shall be:
```
case #1
case #2
default case
```
> Written with [Atom](https://atom.io/).

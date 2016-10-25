# Homework #6

##### by Xuenan Xu GWID G26980825
&nbsp;

**1**

The program can be divided into 2 parts.

The first part is fact definition, that `0! = 1` and `1! = 1`.
```
factorial(0,1).
factorial(1,1).
```
The second part is the definition of recursion.
```
factorial(N,M) :-
  N1 is N-1, factorial(N1,M1), M is N*M1.
```
We can do query like shown below:
```
1 ?- factorial(4,X).
X = 24 .
2 ?- factorial(10,X).
X = 3628800 .
```

**2**

The program can be divided into 2 parts as well.

The first part is fact definition, that is `The reversal of [] and a reversed list A is A itself`.
```
reverse_revised([],_,_).
```
The second part is the definition of rescursion.
```
reverse_revised([Head|Tail],_,X) :-  reverse_revised(Tail,[Head|_],X).
```
When trying to trace a reverse process, I got the following result:
```
[trace] 21 ?- reverse_revised([1,2,3],[],X).   Call: (7) reverse_revised([1, 2, 3], [], _G3857) ? creep
   Call: (8) reverse_revised([2, 3], [1|_G3936], _G3857) ? creep
   Call: (9) reverse_revised([3], [2|_G3939], _G3857) ? creep
   Call: (10) reverse_revised([], [3|_G3942], _G3857) ? creep
   Exit: (10) reverse_revised([], [3|_G3942], _G3857) ? creep
   Exit: (9) reverse_revised([3], [2|_G3939], _G3857) ? creep
   Exit: (8) reverse_revised([2, 3], [1|_G3936], _G3857) ? creep
   Exit: (7) reverse_revised([1, 2, 3], [], _G3857) ? creep
true.
```

&nbsp;
> Written with [Atom](https://atom.io/).

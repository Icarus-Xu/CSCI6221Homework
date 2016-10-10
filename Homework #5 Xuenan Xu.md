# Homework #5

##### by Xuenan Xu GWID G26980825
&nbsp;

In this homework we got 2 problems, the first one is to reverse a `simple list`, lists without non-atom members; another one is to reverse a `general list`, which is lists with both atom and non-atom members. After carefully reviewed these 2 problems, I believe they are actually the same problem, as `simple list` is a special condition of `general list`, in other words, `general list` is the normal form of lists, so we shall focus on this generalized type of list, not the specialized ones. Actually, if an algorithm works good on generalized objects, it shall works as well on specialized ones. An algorithm that designed for specified usage may be more effective on certain condition, but lack of generality means lack of portability. I programmed the code for `general list`, and when I run it on `simple list`, it works unsurprisingly well.

The work flow can be described like this (argument list named `l`):
1. if `l` is null, return a empty list
2. if `l` is not null, proceed to 3
3. if the first element of `l` is an atom, proceed to 4, else proceed to 5
4. make a list with the first element of `l`, proceed to 6
5. make a list with the __reversal__ of the first element of l(a list by assumption), proceed 6
6. append the process result of the first element of `l` to the __reverse__ of the rest of `l`

We then can write code based on upper workflow like this:
```scheme
(define (reverse-list l)
	(if (null? l)
		`()
		(append
		    (reverse-list (cdr l))
		    (if (list? (car l))
		        (list (reverse-list (car l)))
				(list (car l))
		    )
		)
	)
)
```
The algorithm accurately implemented the workflow we defined, and it works for both `simple list` and `general list`.
```
(reverse-list `(A B C))
=> (C B A)
(reverse-list `(A (B C (D E)) F))
=> (F ((E D) C B) A)
```

&nbsp;
> Written with [Atom](https://atom.io/).

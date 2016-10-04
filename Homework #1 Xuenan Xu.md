# Homework #1

##### by Xuenan Xu GWID G26980825
&nbsp;

**1**
```javascript
function big() {
    function sub1() {
        var x = 7;
        return sub2();
    }
    function sub2() {
        return x + 10;
    }
    var x = 3;
    return sub1();
}
```

The result of calling _big()_ shall be **13**. In `big()` we defined `x = 3`, and that is visible in `sub2()`. In `sub1()` we defined `x = 7` but as `sub1()` and `sub2()` are on the same level of code, this `x = 7` is invisible in `sub2()`, that is when we call `big()` we calculate `sub2()` with the `x` in `big()` without modify the `x` in `sub1()`.

**2**
```python
pList = [x ** 2 for x in range(16) if x % 4 == 0]
```

The content of `pList` shall be `{0, 16, 64, 144}`, as `range(16)	` contains `[0, 16)`, so `x ∈ {0, 4, 8, 12}`.

**3**
```scheme
(CDR '(A (BC))
(LIST 'A 'B '(C D) 'E '(F))
(CONS '(A B) '(C D))
```

* `(CDR '(A (BC)) = (BC)`
* `(LIST 'A 'B '(C D) 'E '(F)) = (A B (C D) E (F))`
* `(CONS '(A B) '(C D)) = ((A B) C D)`

**4**
```c
int cArray[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
int* pInt = cArray;
```

* `cArray[6] = 6`
* `pInt[3] = 3`
* `*(pInt + 8) = 8`

&nbsp;
> Written with [Atom](https://atom.io/).

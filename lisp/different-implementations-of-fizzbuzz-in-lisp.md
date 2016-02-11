
### Different Implementations of Fizzbuzz in Lisp

Using simple if conditions:
```lisp
(defun is-mult-p (n multiple)
  (= (rem n multiple) 0))

(defun fizzbuzz (&optional n)
  (let ((n (or n 1)))
    (if (> n 100)
        nil
        (progn
          (let ((mult-3 (is-mult-p n 3))
                (mult-5 (is-mult-p n 5)))
            (if mult-3
                (princ "Fizz"))
            (if mult-5
                (princ "Buzz"))
            (if (not (or mult-3 mult-5))
                (princ n))
            (princ #\linefeed)
            (fizzbuzz (+ n 1)))))))
  ```

 Using cond :
 ```lisp
 (defun fizzbuzz (n end) (if (> n end) nil (cons
	(cond
		((= 0 (mod n 15)) "fizzbuzz")
		((= 0 (mod n 3))  "fizz")
		((= 0 (mod n 5)) "buzz")
		(t n))
	(fizzbuzz (+ n 1) end))))

(format t "~{~A ~}" (fizzbuzz 1 100))
```

Using a set of functions :
 ```lisp
(defun is_dividable (dividee divider)
  (eq (mod dividee divider) 0))

(defun is_fizz (num)
  (is_dividable num 3))

(defun is_buzz (num)
  (is_dividable num 5))

(defun fizzbuzz_in (num)
  (cond ((and (is_fizz num) (is_buzz num))
         (format t "FizzBuzz~&"))
        ((is_fizz num)
         (format t "Fizz~&"))
        ((is_buzz num)
         (format t "Buzz~&"))
        (t
         (format t "~A~&" num))))

(defun fizzbuzz (min max)
  (if (<= min max)
      (progn
        (fizzbuzz_in min)
        (fizzbuzz (1+ min) max))))

(fizzbuzz 1 100)
```

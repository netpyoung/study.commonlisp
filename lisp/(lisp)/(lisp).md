( Lisp )
=========================================================================
![!lisp-logo.png]

# Lisp
* Lisp�� �� �ǹ��ϴ� �ž�?
* AI���?
* ǥ����� �̻��ϰ�, ��ȣ�� ���� ���?
* Ư¡?

## Lisp�� �� �ǹ��ϴ� �ž�?
* �̸��� ��� : LISt Processing
* �̸����� ��Ÿ������ Linked List(���� ���� ����Ʈ)�� �ֵ� �ڷᱸ��.


## AI ���?
 ![Lisp Machine in MIT��s Museum][!lisp-machine.jpg]

* Lisp�� �ƹ��� "�� ��ī��(John McCarthy)��
 - (1927�� 9�� 4�� ~ 2011�� 10�� 24��)
 - 1956�� ��Ʈ�ӽ� ��ȸ���� ó������ �ΰ�����(Artificial Intelligence)�̶�� �� â��
 - 1958�� Lisp ���߽���
 - 1960�� �� "Recursive Functions of Symbolic Expressions and Their Computation by Machine, Part I"
 - 1971�� Ʃ���� ����. �ΰ����ɿ� ���� �������� ����


## ǥ����� �̻��ϰ�, ��ȣ�� ���� ���?
 ![lisper keyboard][!lisp-keyboard.png]
* ���� ǥ��� : `+` 1 2
* ���� ǥ��� : 1 `+` 2
* ���� ǥ��� : 1 2 `+`

`(1 + 2) * 3 => * + 1 2 3 => (* (+ 1 2) 3)`

### ��ȣ
* ó������ �źΰ��� ���.
* html, xml���� ���� ����!
* �ڵ�� �����͸� �����ִ� �ϸ��

### Ư¡?
From Wikipedia
�з����� : �Լ���, ������, reflective, meta
Ÿ��     : Dynamic, strong

ǥ���� : (��Դ�) S-expression
��ũ��
�������ݷ���
�������������� �����Ϸ�


### �Լ��� ���α׷��� ���?
First-class
 �Լ� ��ü�� �������� ������ �� ������, ���ڷ� �ѱ�ų� ��ȯ�� �� �ִ�

���̵� ����Ʈ(side effect)�� ����
But!, pure functional�� �ƴ�.


# Atom & Expression
## REPL
* `R`ead `E`val `P`rint `L`oop
 - Interactive shell�̶� �Ҹ��⵵ ��.

```lisp
(defun game-repl ()
  (let ((cmd (game-read)))
    (unless (eq (car cmd) 'quit)
      (game-print (game-eval cmd))
      (game-repl))))
```


## ATOM
 ![atom][!atom-animation.jpg]
* �ɺ�
* ����
* ��, ���� �׸��� NIL

### �ɺ�
```
CL-USER>  a
The variable A is unbound.

CL-USER> (defvar a 1)
A

CL-USER>  a
1

CL-USER> (list a)
(1)

CL-USER> :a
:A
```

### ��
* �ڿ��� : `1234`
* �Ҽ�  : `123.4`
* �м� : `123/4 = (/ 123 4)`
* ���Ҽ� : `#C(1 2) = (complex 1 2) = 1 + 2i`

### ����

```
CL-USER> (+ 5/9 3/4)
47/36

CL-USER> (* 2 (+ #c(10 5) 4)) ;; 2 * ( (10 + 5i) + 4)
#C(28 10)

CL-USER> (expt (expt (expt (expt 10 10) 10) 10) 10)
100000000000000000000000000000000000��
```

### ��, ���� �׸��� NIL
* ��   : T
* ���� : NIL

* ��, Common Lisp����, NIL�� ()�� ������ ������ �����Ѵ�.
* ��ġ C ���� if( x )���� x�� 0�̸� �����̶�� �Ǵ��ϴ� �Ͱ� ����.
* �㳪, ������ ����(Clojure, Scheme)������ ��, ���� ������ �ٸ� �� ������ ����.

### NIL

```
CL-USER> nil
NIL

CL-USER> ()
NIL

CL-USER> (list)
NIL

CL-USER> (list nil)
(NIL)
```

# Expression
 ![cons-canvas][!cons-canvas.jpg]

* S-expression ?
* Cons cell?
* car, cdr ?
* Cons cell & car, cdr

## S-expression 
(Symbolic-expression, sexpr)

* Atom : ���� | �ɺ�.
 - ���⼭ �ɺ��� �����̸��̳� �����ͷ� ���Ǵ� ��������.
* Expression
 - (x . y)�� ���� ����(form)�� �� ǥ����. (���⼭ x, y�� s-exression)

## Cons cell ?
 ![cons-cell][!cons-cell.gif]

 constructs memory objects which hold two values or pointers to values.
 
(setf x '(a (r t) b))

## car, cdr?
car, cdr�� �̸��� ���� ���
"IBM 704"�󿡼� lisp�� �����ϴµ�, ��� "IBM 704"���� ����ϴ� ���������� �̸��� car, cdr�̿���.

�Ŀ�,����̸� first�� rest���� �������� caar, cadr, cdadr�� ��øŰ���带 ��ü�ϱ⿡�� ������ �־���.

* `[15 Address][15 Decrement][3 Prefix][3 Tag]`
 - car (Contents of the `Address` part of Register number)
 - cdr (Contents of the `Decrement` part of Register number)
 - cpr (Contents of the `Prefix` part of Register number)
 - ctr (Contents of the `Tag` part of Register number)

## Cons cell & car, cdr
```
CL-USER> (cons 1 2)
(1 . 2)

CL-USER> (car '(1 . 2))
1

CL-USER> (cdr '(1 . 2))
2
```

```
CL-USER> (cons 1 nil) 
(1)

CL-USER> (cons 1 (cons 2 (cons 3 nil))) 
(1 2 3)

CL-USER> (list 1 2 3)
(1 2 3)
```

# Lambda
## Lambda
 ![lambda-symbol][!lambda-symbol.png]

* lambda
* funcall & eval
* defun

`���� ���(�� -, lambda -)�� �Լ� ����, �Լ� ����, �ͳ��� �Լ��� �������� ǥ���ϱ� ���� ���� ü���̴�`

## lambda

```
CL-USER> (lambda (x) (+ x 10))
#<FUNCTION (LAMBDA (X)) {2496A42D}>

CL-USER> ( (lambda (x y) 
		 (+ (* x x) (* y y)))
		 5 2 )
29
```

## funcall & eval
```
CL-USER> (setq a (lambda (x) (+ x 10)))
#<FUNCTION (LAMBDA (X)) {2496A42D}>

CL-USER> (funcall a 123)
133

CL-USER> (eval '(funcall a 123))
133
```

## defun
```
CL-USER> (defun sum-of-1-to-n (n)
           (/ (* n (1+ n)) 2))
SUM-OF-1-TO-N

CL-USER> (sum-of-1-to-n 100)
5050
```

## ???

```
�� (funcall a 10) ??
�׳� (a 10)�ϸ� �ɰ� ������

Common Lisp��
Variable�� Funtion�� �̸������� ������.

Scheme��
Variable�� Function�� �̸������� ����.
```

# Condition
 ![condition-drink][!condition-drink.gif]
* if
 - when
 - unless
* cond

## if
```lisp
(defun number? (n)
  (if (zerop n)
      :zero
      (if (minusp n)
	  :minus
	  (if (plusp n)
	      :plus
	      :idk))))
```

### when, unless
```lisp
(defun number?-when (n)
  (when (zerop  n)
    (return-from number?-when :zero))
  (when (minusp n)
    (return-from number?-when :minus))
  (when (plusp  n)
    (return-from number?-when :plus))
  :idk)
```

```lisp
(defun float?-unless (n)
  (unless (floatp n)
    (return-from float?-unless :not-float))
  :float)
```

### cond
```lisp
(defun number-what3 (n)
  (cond ((minusp n) :minus)
	  ((zerop  n) :zero)
	  ((plusp  n) :plus)
	  (t          :idk)))
```

# Binding
* let, let*
* flet, lbales
* lexical & dynamic

![!binding-rope][!binding-rope.jpg]

## let, let*
```lisp
CL-USER> (let ((x 10)
	         (y 20))
	     (+ x y))
30 

CL-USER> (let* ((x 10)
		    (y (+ x 20)))
	     y)
30
```

## flet, lables
```lisp
CL-USER> (flet ((hello (x) (1- x)))
	     (hello 10))	      
9

CL-USER> (labels ((hello (x)
			  (if (> x 3)
			    (hello (1- x))
			    x)))
             (hello 10))
3
```

## lexical & dynamic
```lisp
(defparameter *global* 10)

(defun hello ()
  (print *global*))

(let ((x *global*))
  (defun hello2 ()
     (print x)))
```

# LISt Processing
* quote, unquote
* macro
* defmacro

## quote, unquote
```
CL-USER> a
1
CL-USER> (quote a)
A
CL-USER>��a
A

CL-USER> (list a)
(1)
CL-USER> ��(a)
(A)
CL-USER> `(,a)
(1)
```

` ` ` �� �ַ�, Scheme���� �̸� `Quasiquote`, Common Lisp���� `backquote`�� �θ�.


```
CL-USER> `(1 2 ,@(list 3 4))
(1 2 3 4)
```

## macro
Lisp form�̳� object�� �޾� ������ �ǰų� ����Ǵ� �ڵ带 ����
���� �߻�ȭ ��� ����

Domain-specific language�� ���� ����.

��Ÿ�� �� ��ũ�� Ȯ�� Ÿ���� ����

����ȭ�� ������ �ֱ⵵ ��

����ϰ�, ������ �ڵ带 �̲�����

### cond macro
```lisp
(defmacro cond (&rest clauses)
  (when clauses
    (let* ((this   (first clauses))
	      (others (rest  clauses))
	      (test  (first this))
	      (forms (rest  this)))
      `(if ,test
	    (progn ,@forms)
	    (cond  ,@others)))))

```

### cond expand
```lisp
(cond ((minusp n) :minus)
	 ((zerop  n) :zero)
	 ((plusp  n) :plus)
	 (t          :idk))
```


```lisp
(IF (MINUSP N)
    (PROGN :MINUS)
    (COND ((ZEROP N) :ZERO) 
          ((PLUSP N) :PLUS)
          (T         :IDK)))
```

# DSL
* dsl
* loop
* format
![dsl-3][!dsl-3.png]

## dsl
* DSL�̶�?
 - Domain-Specific Language
 - �ǵ��� �巯���� �ڵ�(Intention-revealing code)
 - Ư�� ������ Ÿ������ �� ��ǻ�� ���

* External DSLs
 - ���� ����ϰ� �ִ� ����� �ܺο� �����ϴ� DSL. ex) SQL, ����ǥ����
* Graphical DSLs
 - �ǵ��� ǥ���ϱ� ���� ���ں��� ������ �̿��� DSL. ex) UML
 - ����ȭ���� ������ ������, ���� ������ �ذ��ϱ� ���ؼ��� �״���..
* Fluent interfaces
 - Api�� �� ��ġ�Ͽ� �б� ���ϰԸ���.
 - �������� ���� ���� �ַ� ����.
* Internal or embeded DSLs
 - ���� ����ϰ� �ִ� �� �״�� ����ϴ� DSL.

## loop
```lisp
CL-USER> (loop for i from 1 to 10
               collect i)
(1 2 3 4 5 6 7 8 9 10)
```

## format
```
CL-USER> (format nil "~{~a~^, ~}��
                     '(1 2 3 4 5))
"1, 2, 3, 4, 5"
```

# CLOS
* Common Lisp Object System
* ��ü������ �����ϱ� ����, ������ �����Ѱ��� �ƴ�, ��ũ�θ� �̿��Ͽ� ä��.

```lisp
(defclass <POS> ()
  ((x :initarg :x :accessor x)
   (y :initarg :y :accessor y)))

(defun new-pos (x y)
  (make-instance '<POS> :x x :y y))

(defparameter p1 (new-pos 10 20))

(defmethod print-object ((pos <POS>) stream)
  (with-slots (x y) pos
    (format stream "#<Pos ~a, ~a>" x y)))

(defmethod rotate ((pos <POS>))
  (with-slots (x y) pos
    (new-pos (- y) x)))
```

```lisp
(defclass <Rectangle> ()
  ((w :accessor w :initarg :w)
   (h :accessor h :initarg :h)))

(defclass <Circle> ()
  ((r :accessor r :initarg :r)))

(defmethod area! ((rectangle <Rectangle>))
  (with-slots (w h) rectangle
    (* w h)))

(defmethod area! ((circle <Circle>))
  (with-slots (r) circle
    (* pi (expt r 2))))

(defparameter aa (make-instance '<Rectangle> :w 10 :h 20))
(defparameter bb (make-instance '<Circle> :r 10))

(area! aa)
(area! bb)
```

# Debug
* step
* trace
* disassamble
* declare

## step
```
CL-USER> (step (labels ((hello (x)
			  (if (> x 3)
			    (hello (1- x))
			    x)))
             (hello 10)))
```

## trace
```
CL-USER> (defun hello (x)
	   (if (> x 3)
	       (hello (1- x))
	       x))
HELLO
CL-USER> (trace hello)
(HELLO)

CL-USER> (hello 5)
  0: (HELLO 5)
    1: (HELLO 4)
      2: (HELLO 3)
      2: HELLO returned 3
    1: HELLO returned 3
  0: HELLO returned 3
3

CL-USER> (untrace hello)
T
```

## disassamble
```lisp
(defun add1 (n)
  (1+ n))

(disassemble 'add1)

; disassembly for ADD1
; 247C2D38:       840500000021     TEST AL, [#x21000000]
;       3E:       8B55FC           MOV EDX, [EBP-4]
;       41:       BF04000000       MOV EDI, 4
;       46:       E84DD483FD       CALL #x22000198
;       4B:       7302             JNB L0
;       4D:       8BE3             MOV ESP, EBX
;       4F: L0:   8BE5             MOV ESP, EBP
;       51:       F8               CLC
;       52:       5D               POP EBP
;       53:       C3               RET
;       54:       CC0A             BREAK 10
;       56:       02               BYTE #X02
;       57:       18               BYTE #X18
;       58:       4F               BYTE #X4F                  ; ECX
```
## declare

```
(defun int-add1 (n)
    (declare (fixnum n)
             (optimize (speed 3) (safety 0) (debug 0)))
    (the fixnum (1+ n)))

(disassemble 'int-add1)

; disassembly for INT-ADD1
; 2489E3E0:       840500000021     TEST AL, [#x21000000]      ; no-arg-parsing entry point
;        6:       83C204           ADD EDX, 4
;        9:       8BE5             MOV ESP, EBP
;        B:       F8               CLC
;        C:       5D               POP EBP
;        D:       C3               RET
```

# Foreign Function Interface

## Cffi-with-gcc

```c
#include <stdio.h>
int hello (int a, int b) {
    return a + b;
}
```

`gcc -shared -o test.so test`

```lisp
(defcfun "hello" :int
  (a :int)
  (b :int))
  
 (hello 1 2)
```

```lisp
(ql:quickload :cffi)

(in-package :cl-user)
(defpackage :cffi-exam
  (:use :cl :cffi))
(in-package :cffi-exam)

(define-foreign-library test.so
  (t (:default "~/tmp/test")))

(use-foreign-library test.so)
```


## cffi-with-win32
```lisp
(ql:quickload :cffi)
```

```lisp
(in-package :cl-user)
(defpackage winapi
  (:use :cl :cffi))
(in-package :winapi)

(define-foreign-library user32.dll
  (t (:default "user32")))

(define-foreign-library kernel32.dll
  (:windows "kernel32"))

(cffi:define-foreign-library gdi32.dll
  (:windows "gdi32.dll"))

(use-foreign-library user32.dll)
(use-foreign-library kernel32.dll)
(use-foreign-library gdi32.dll)

(defctype LPCSTR :string)
(defctype HANDLE :pointer)
(defctype HWND HANDLE)

(DEFCFUN ("MessageBoxA" MessageBox) :INT
  (HWND HWND)
  (LPTEXT LPCSTR)
  (LPCAPTION LPCSTR)
  (UTYPE :UINT))
  
(MessageBox (null-pointer) "hello" "world" 0)
```

# more and more

## elisp
![ex-elisp][!ex-elisp.jpg]

## abcl
![ex-abcl-1][!ex-abcl-1.png]
![ex-abcl-2][!ex-abcl-2.png]

## clojure
![ex-clojure][!ex-clojure.jpg]

# �����ڷ�
## Common Lisp: A Gentle Introduction to Symbolic Computation
![common-lisp-book][!common-lisp-book.jpg]

## Land of Lisp
![landoflisp][!landoflisp.jpg]

##OnLisp
 - The Less than Rapid prototype
 - "Because Lisp and rapid prototyping evolved together, Lisp include a lot of features specifically inteded for prototype: inefficient but convenient features like property lists, keyword parameters, and, for that matter, lists."
 - "It's important to realize, though, that Lisp is a language for writing production software as well as a language for writing prototypes.
 - OnLisp - ���� : Paul Graham ( Y Combinator â���� )
![onlisp][!onlisp.jpg]


# Links
* [Peter Seibel's Practical Common Lisp]
* [Paul Graham's On Lisp]
* [David Lamkin's Successful Lisp]
* [Shriram Krishnamurthi's Programming Languages: Application and Interpretation]
* [Guy Steele's Common Lisp the Language, 2nd ed]
* [LispWorks HyperSpec]


 [!atom-animation.jpg]: ./imgs/atom-animation.jpg
 [!binding-rope.jpg]: ./imgs/binding-rope.jpg
 [!clojure-logo.png]: ./imgs/clojure-logo.png
 [!common-lisp-book.jpg]: ./imgs/common-lisp-book.jpg
 [!condition-drink.gif]: ./imgs/condition-drink.gif
 [!cons-canvas.jpg]: ./imgs/cons-canvas.jpg
 [!cons-cell.gif]: ./imgs/cons-cell.gif
 [!dsl-3.png]: ./imgs/dsl-3.png
 [!ex-abcl-1.png]: ./imgs/ex-abcl-1.png
 [!ex-abcl-2.png]: ./imgs/ex-abcl-2.png
 [!ex-clojure.jpg]: ./imgs/ex-clojure.jpg
 [!ex-elisp.jpg]: ./imgs/ex-elisp.jpg
 [!lambda-symbol.png]: ./imgs/lambda-symbol.png
 [!landoflisp.jpg]: ./imgs/landoflisp.jpg
 [!lisp-keyboard.png]: ./imgs/lisp-keyboard.png
 [!lisp-logo.png]: ./imgs/lisp-logo.png
 [!lisp-machine.jpg]: ./imgs/lisp-machine.jpg
 [!onlisp.jpg]: ./imgs/onlisp.jpg
 
 [Peter Seibel's Practical Common Lisp]: http://gigamonkeys.com/book/
 [Paul Graham's On Lisp]: http://www.paulgraham.com/onlisp.html
 [David Lamkin's Successful Lisp]: http://psg.com/~dlamkins/sl/cover.html
 [Shriram Krishnamurthi's Programming Languages: Application and Interpretation]: http://cs.brown.edu/~sk/Publications/Books/ProgLangs/
 [Guy Steele's Common Lisp the Language, 2nd ed]: http://www-prod-gif.supelec.fr/docs/cltl/clm/node1.html
 [LispWorks HyperSpec]: http://www.lispworks.com/documentation/HyperSpec/Front/index.htm
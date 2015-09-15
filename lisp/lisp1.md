在lisp中输入以下东西学习或者回顾知识

\>表示输入的代码

\#表示注释，不需要输入

```
> 1

> (+ 2 3)

> (+ 2 3 4)

> (/ (- 7 1) (- 4 2))

> 2 (+ 2 3) (+ 2 3 4) (/ (- 7 1) (- 4 2))

> (quote (+ 3 5))

> '(+ 3 5)

> 'Liuchen	#结果发现变成了大写了。

> '(my 3 "Sons")	#发现引号保护了sons而没有变成大写

> '(the list (a b c) has 3 elements)

> (list 'my (+ 2 1) "Sons")

> (list '(+ 2 1) (+ 2 1))

> ()

> nil	#这个和上个都是表示空列表，可以在需要的时候使用

> (cons 'a '(b c d))	#注意后一个参数是'()才可以组合，否则生成其他，可以自己尝试

> (car '(a b c))

> (cdr '(a b c))

> (listp '(a b c))

> (listp 'a)

> (if (listp '(a b c))
      (+ 1 2)
      (+ 5 6))

> (if (listp 27)
      (+ 1 2)
      (+ 5 6))

> (defun our-third (x)
   (car (cdr (cdr x))))
   
\#2015年9月7号添加

> (defun our-member (obj lst)
   (if (null lst)
       nil
   (if (eql (car lst) obj)
       lst
       (our-member obj (cdr lst)))))	#哇，能用看懂这样一个lisp语言的递归，已经很棒了。
	   
> (our-member 'b '(a b c))	#测试our-member函数

> (our-member 'z '(a b c))	#测试our-member函数

> (format t "~A plus ~A equals ~A. ~%" 2 3 (+ 2 3))

> (let ((x 1) (y 2))
     (+ x y))	#let只是临时给x和y赋初始值。相当于初始化，注意括号的个数。
	 
> (defparameter *glob* 99)	#定义全局变量。全局变量人为习惯给它们特殊命名形式。比如说这里就是 *名字* 形式

> (boundp '*glob*)	查看变量是否为全局变量

> (let ((n 10))	#注意n 10的括号数量，结合上个let例子理解为啥要这样操作
   (setf n 2)	#setf是赋值。
   n)

\2015年7月14号添加
> (setf lst '(c a r a t))

> (remove 'a lst)

> lst

(setf x (remove 'a x))

> lst

>	(defun show-squares (start end)
	  (do ((i start (+ i 1)))
		  ((> i end) 'done)
		(format t "~A ~A~%" i (* i i))))
	
> (show-squares 2 5)

/2015年7月15号添加
> (apply #'+ '(1 2 3))

> (+ 1 2 3)

> (apply #'+ 1 2 '(3 4 5))

> (apply #'+ 1 2 )	#发现这个有误，利用这个只需要满足最后一个参数是'(),即列表形式

> (funcall #'+ 1 2 3)

> ((lambda (x) (+ x 100)) 1)	#lambda是临时函数，这个分成两段来看就看懂了，(lambda (x) (+ x 100))和1。显然1->x,然后输出x+100

> (typep 27 'integer)

```

阅读到http://acl.readthedocs.org/en/latest/zhCN/ch2-cn.html#form的习题部分，下回做一下习题2的解答
原本已经觉得学完了，但是居然发现其实山外有山，这个只是一本书里面的一章，具体目录网址为：http://acl.readthedocs.org/en/latest/zhCN/index.html

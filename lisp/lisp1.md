��lisp���������¶���ѧϰ���߻ع�֪ʶ

\>��ʾ����Ĵ���

\#��ʾע�ͣ�����Ҫ����

```
> 1

> (+ 2 3)

> (+ 2 3 4)

> (/ (- 7 1) (- 4 2))

> 2 (+ 2 3) (+ 2 3 4) (/ (- 7 1) (- 4 2))

> (quote (+ 3 5))

> '(+ 3 5)

> 'Liuchen	#������ֱ���˴�д�ˡ�

> '(my 3 "Sons")	#�������ű�����sons��û�б�ɴ�д

> '(the list (a b c) has 3 elements)

> (list 'my (+ 2 1) "Sons")

> (list '(+ 2 1) (+ 2 1))

> ()

> nil	#������ϸ����Ǳ�ʾ���б�����������Ҫ��ʱ��ʹ��

> (cons 'a '(b c d))	#ע���һ��������'()�ſ�����ϣ��������������������Լ�����

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
   
```

�Ķ���http://acl.readthedocs.org/en/latest/zhCN/ch2-cn.html#form��2.7�ݹ��½�
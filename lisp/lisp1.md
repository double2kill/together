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

> nil	#������ϸ����Ǳ�ʾ���б���������Ҫ��ʱ��ʹ��

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
   
\#2015��9��7�����

> (defun our-member (obj lst)
   (if (null lst)
       nil
   (if (eql (car lst) obj)
       lst
       (our-member obj (cdr lst)))))	#�ۣ����ÿ�������һ��lisp���Եĵݹ飬�Ѿ��ܰ��ˡ�
	   
> (our-member 'b '(a b c))	#����our-member����

> (our-member 'z '(a b c))	#����our-member����

> (format t "~A plus ~A equals ~A. ~%" 2 3 (+ 2 3))

> (let ((x 1) (y 2))
     (+ x y))	#letֻ����ʱ��x��y����ʼֵ���൱�ڳ�ʼ����ע�����ŵĸ�����
	 
> (defparameter *glob* 99)	#����ȫ�ֱ�����ȫ�ֱ�����Ϊϰ�߸���������������ʽ������˵������� *����* ��ʽ

> (boundp '*glob*)	�鿴�����Ƿ�Ϊȫ�ֱ���

> (let ((n 10))	#ע��n 10����������������ϸ�let�������ΪɶҪ��������
   (setf n 2)	#setf�Ǹ�ֵ��
   n)

\2015��9��14�����
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

/2015��9��15�����
> (apply #'+ '(1 2 3))

> (+ 1 2 3)

> (apply #'+ 1 2 '(3 4 5))

> (apply #'+ 1 2 )	#������������������ֻ��Ҫ�������һ��������'(),���б���ʽ

> (funcall #'+ 1 2 3)

> ((lambda (x) (+ x 100)) 1)	#lambda����ʱ����������ֳ����������Ϳ����ˣ�(lambda (x) (+ x 100))��1����Ȼ1->x,Ȼ�����x+100

> (typep 27 'integer)

/2015��9��19�����

> (setf z (list 'a (list 'b 'c) 'd))

> (car (cdr z))

> (eql (cons 'a nil) (cons 'a nil))	#��Ȼ���nil

> (setf x (cons 'a nil))

> (eql x x)

> (equal x (cons 'a nil))	#ע�������equal���Բ���ȡ�

(defun compress (x)	#ѹ�����롣
  (if (consp x)
      (compr (car x) 1 (cdr x))
      x))

(defun compr (elt n lst)
  (if (null lst)
      (list (n-elts elt n))
      (let ((next (car lst)))
        (if (eql next elt)
            (compr elt (+ n 1) (cdr lst))
            (cons (n-elts elt n)
                  (compr next 1 (cdr lst)))))))

(defun n-elts (elt n)
  (if (> n 1)
      (list n elt)
      elt))
	 
Ч����
> (compress '(1 1 1 0 1 0 0 0 0 1))	#�ܶ�������Ĵ���Ͳ���Ѿ�����lisp�ˡ�
((3 1) 0 1 (4 0) 1)

> (uncompress '((3 1) 0 1 (4 0) 1))	#����ѹ����һ������дһ����ѹ�ķ���
(1 1 1 0 1 0 0 0 0 1)

(defun uncompress (lst)
  (if (null lst)
      nil
      (let ((elt (car lst))
            (rest (uncompress (cdr lst))))
        (if (consp elt)
            (append (apply #'list-of elt)
                    rest)
            (cons elt rest)))))

(defun list-of (n elt)
  (if (zerop n)
      nil
      (cons elt (list-of (- n 1) elt))))
	  
/2015��9��22�����
> (nth 0 '(a b c))

> (nthcdr 2 '(a b c))

> (mapcar #'(lambda (x) (+ x 10))
          '(1 2 3))
		  
> (mapcar #'list
          '(a b c)
          '(1 2 3 4))

> (member 'b '(a b c))

> (member '(a) '((a) (z)) :test #'equal)

> (member 'a '((a b) (c d)) :key #'car)

> (member 2 '((1) (2)) :key #'car :test #'equal)

> (member 2 '((1) (2)) :test #'equal :key #'car)	���߶�ѯ���Ƿ���һ��Ԫ�ص� car ����( equal ) 2��

> (adjoin 'b '(a b c))

> (adjoin 'z '(a b c))	  

```

�Ķ���http://acl.readthedocs.org/en/latest/zhCN/ch3-cn.html
��3.13��״�б��»ػ��ǿ�����һ��ϰ��2�Ľ��

ԭ���Ѿ�����ѧ���ˣ����Ǿ�Ȼ������ʵɽ����ɽ�����ֻ��һ���������һ�£�����Ŀ¼��ַΪ��http://acl.readthedocs.org/en/latest/zhCN/index.html

## 1.1 The Elements of Programming

### Key concepts:
- primitive expressions
- means of combination
- means of abstraction

### Notes 
基本表达式（Expression）包含两类：没有括号的值（Value）、和被括号括起来的过程（Procedure）（包含一般形式和特殊形式）。  

### Exercises
Ex1.1  
大家需要注意的是，一方面，SICP书中把表达式分为「基本表达式」（primitive expressions）和复合表达式，或说「组合式」（combinations）。  
但另一方面，我们应该注意「值」与「式」的区分。Scheme程序的执行就是一系列求值的过程。所以一类表达式，是生来就为了求值的被放在括号中的「过程」；而它们的最后归宿，就是不用再进一步求值的另一类表达式，称为「值」。  
「值」也可以进一步分类：一般来说，简单数据如数字、字符等都是不用进一步求值的；已经定义的运算规则（不论是来自解释器的定义，还是用户自己的定义）也是不用进一步求值的。其实在以后我们会看到，随着抽象的增加，数值和运算规则之间的界线会愈发地模糊。  
但是我们需要注意，特殊形式的运算规则并不是「值」，比如「+」是值，而「DEFINE」就**不是**值：  
```scheme
1 ]=> +

;Value 2: #[arity-dispatched-procedure 2]

1 ]=> define

;Syntactic keyword may not be used as an expression: #[keyword-value-item 3]
;To continue, call RESTART with an option number:
; (RESTART 1) => Return to read-eval-print level 1.

2 error> (restart 1)

;Abort!
```

表达式包含不用进一步求值的「值」（Value）和需要进一步求值的「式」（Formula）或「过程」（Procedure）。  
式子的一般求值步骤是：  
1. 先求每一个子表达式的值；  
2. 然后把最左边的值作为运算符，把其他值作为运算对象，进行求值。  

但特殊形式的式子其求值方式有所不同吧？  


体会了上面的内容之后，让我们来看下面的表达式：  
```
10
```  
这显然是一个不用进一步求值的「值」，故结果是10。  
```scheme
(+ 5 3 4) 
```
这是一个需要进一步求值的「式子」，结果为12。  

说到 + - * / 四则运算，有一个思考题留给大家：  
```
(+ 4 2 1)  
(+ 4 2)  
(+ 4)  
(+)  
  
(- 4 2 1)  
(- 4 2)  
(- 4)  
(-)  
  
(* 4 2 1)  
(* 4 2)  
(* 4)  
(*)  
  
(/ 4 2 1)  
(/ 4 2)  
(/ 4)  
(/)  
```
  
先在脑中给出答案，再用Scheme解释器计算一下，思考是为什么。



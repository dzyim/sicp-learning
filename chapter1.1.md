## 1.1 The Elements of Programming

（以下部分内容可能需要修改，因为根据定义，组合式（combinations）不包括特殊形式（special forms）。）

### Key concepts:
- primitive expressions
- means of combination
- means of abstraction

### Notes 
在程序设计中，我们与两类要素打交道：数据（Data）与过程（Procedure）。  
一个表达式（Expression）其实也可以分为两种：没有括号的值（Value）、和被括号括起来的组合式（Combination）。  

### Exercises
Ex1.1  
本题需要我们对题干中的表达式进行求值。如果我们手边有Scheme解释器的话，这些表达式的求值只是小菜一碟，所以我们聊聊别的。  

我们应该注意「值」与「式」的区分。  
SICP书中把表达式分为「基本表达式」（primitive expressions）和复合表达式（compound expressions），或说「组合式」（combinations）。那么什么是「基本表达式」呢？  
很多初学者可能会在这里犯错，误解基本表达式的意思。  
我在第一次阅读SICP的时候，以为下面这种形式的表达式是基本表达式：
```
(+ 1 1)
```
而只有产生了嵌套的结构，如下面这种形式的
```
(* (+ 1 1) 2)
```
才是复合表达式。  
其实这是一种常见的错误认识。  
  
「基本表达式」就是「值」。  
Scheme程序的执行是一系列求值的过程。所以一类表达式，是生来就为了求值的被放在括号中的「过程」，也就是「组合式」；而它们的最后归宿，就是不用再进一步求值的另一类表达式，称为「值」，也就是「基本表达式」。  
「值」（或说「基本表达式」）可以进一步分类：一般来说，简单数据如数字、字符等都是不用进一步求值的；已经定义的运算规则（不论是来自解释器的定义，还是用户自己的定义）也是不用进一步求值的。所以简单数据和简单运算规则都是基本表达式（primitive expression）。其实在以后我们会看到，随着抽象的增加，数值和运算规则之间的界线会愈发地模糊。  
但是我们需要注意，特殊形式的运算规则只是语法关键词，并不是「值」，比如「+」是值，而「DEFINE」就**不是**值。  
如果我们在Scheme解释器的交互页面分别输入「+」和「define」，会得到下面的结果：   
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

我们知道了表达式包含本身就是值的「基本表达式」和需要进一步求值的「复合表达式」。  
组合式（combinations）是具有一般性的求值步骤的：  
1. 先求每一个子表达式的值；  
2. 然后把最左边的值作为运算符，把其他值作为运算对象，进行求值。  

而每种特殊形式的式子则各有其不同的求值方式。  


体会了上面的内容之后，让我们来看下面的表达式：  
```scheme
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



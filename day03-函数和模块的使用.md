## 函数的定义  
  在python中可以使用def关键字来定义函数，和变量一样每个函数也有一个名字，而且命名规则跟变量的命名规则是一致的。在函数后面的圆括号中可以放置传递给函数的参数。而函数执行完以后可以通过return关键字来返回一个值。
  
      def factorial(num):  
          result = 1  
          for n in range(1,num + 1):  
              result *= n  
          return result  

      m = int(input('m = '))  
      n = int(input('n = '))  
      print(factorial(m) // factorial(n) // factorial(m - n))    

## 函数的参数
  在python中，函数的参数可以有默认值，也支持使用可变参数，所以python并不需要像其他语言一样支持重载，因为我们在定义一个函数的时候可以让它有多种不同的使用方式。
    
    from random import randint
    def roll_dice(n = 2):
        total = 0
        for _ in range(n):
            total += randint(1,6)
        return total

    def add(a = 0,b = 0,c = 0):
        return a + b + c

    print(roll_dice())
    print(roll_dice(3))
    print(add())
    print(add(1))
    print(add(1,2))
    print(add(1,2,3))
    print(add(a=50,c=100,b=200))
    
  在上面的代码中，我们可以给两个函数传入参数，如果没有参数，这时函数将用默认值运行。  
  在很多时候我们对函数的参数个数是不确定的时候，我们可以使用可变参数，可以传入0个或多个参数。
  
    # 在参数前使用*表示args是可变参数
    def add(*args):
        total = 0
        for var in args:
            total += var
        return total

    print(add(2))
    print(add(100))
    print(add(6))
    print(add(1,2,3))
    print(add(3))

## 用模块管理函数
  有些时候在同一个.py文件中定义了两个同名函数，由于python没有函数重载的概念，那么后面的定义会覆盖之前的定义，也就意味着两个同名函数实际上只有一个是存在的。
  为了解决这种问题，python中每个文件就代表了一个模块（module），我们在不同的模块中可以有同名的函数，在使用函数的时候我们通过import关键字导入指定的模块就可以区分到底使用的是哪个模块中的函数。   
  module1.py
  
    def foo():
        print('hello,world!')
  
  module2.py
    
    def foo():
        print('goodbye,world!')

  test.py
  
    from module1 import foo
    foo()  # 输出hello，world！
    from module2 import foo
    foo()  # 输出goodbye，world！
  
  也可以按照如下所示的方式来区分到底要使用哪一个foo函数。
  test.py
  
    import module1 as m1
    import module2 as m2
    
    m1.foo()
    m2.foo()
  
  但是如果将代码写成下面的样子，那么程序中调用的是最后导入的那个foo，因为导入的foo覆盖了之前导入的foo  
  test.py
  
    from module1 import foo
    from module2 import foo
    foo()  #输出goodbye，world！
  
  如果我们导入的模块除了定义函数之外还有可以执行代码，那么python解释器在导入这个模块时就会执行这些代码，事实上我们可能并不希望如此，因此如果我们在模块中编写了执行代码，最好是将这些执行代码放入如下所示的条件中，这样的话除非直接运行该模块，if条件下的这些代码是不会执行的，因为只有直接执行的模块的名字才是"_main_"。  
  module3.py
    
    def foo():
        pass
    def bar():
        pass

    if __name__ == '__main__':
        print('call foo()')
        foo()
        print('call bar()')
        bar()
  
  test.py
  
    import module3 
    # 导入module3时，不会执行模块中if条件成立时的代码，因为模块的名字是module3，而不是_main_
  
## 变量的作用域  
    
    def foo():
    b = 'hello'

    def bar(): # python中可以在函数内部再定义函数
        c = True
        print(a)
        print(b)
    print(c) # NameError: name 'c' is not defined

    bar()

    if __name__ == '__main__':
        a = 100
        foo()
  
  在上面的代码中，bar函数的内部并没有定义a和b两个变量。在if分支中定义了一个变量a，这是一个全局变量，属于全局作用域，因为它没有定义在任何一个函数中。在上面的foo函数中我们定义了变量b，这是一个定义在函数中的局部变量，属于局部作用域，除了在foo函数内，其它区域不能访问到b。b对于bar函数来说，属于嵌套作用域，在bar函数中是可以访问到b的。而bar函数中的c则属于局部作用域，在bar函数外是无法访问的。
  python查找一个变量时会按照“局部作用域”、“嵌套作用域”、“全局作用域”和“内置作用域”的顺序进行搜索。
  内置作用域就是python内置的那些隐含标识符min、len等都属于内置作用域。
  
  下面这段代码，我们希望通过调用函数修改全局变量a的值，但实际上是实现不了的。
  
    def foo():
    a = 200
    print(a) # 200

    if __name__ == '__main__':
        a = 100
        foo()
        print(a) # 100
  
  在调用foo函数后，我们发现a的值仍然是200，这是因为我们在函数foo中写a = 200的时候，是重新定义了一个名字为a的局部变量，他和全局作用域的a不是同一个变量，因为局部作用域中有了自己的变量a，因此foo函数不在搜索全局作用域中的a。如果我们希望在foo函数中修改全局作用域中的a，则应该这样写：
  
    def foo():
        global a
        a = 200
        print(a) # 200

    if __name__ == '__main__':
        a = 100
        foo()
        print(a) # 100
  
  我们可以用global关键字来指示foo函数中的变量a来自于全局作用域，如果foo函数在全局作用域中没找到a，那么就会使用global下一行中的a并将置于全局作用域。同理，如果我们希望函数内部的函数能够修改嵌套作用域中的变量，可以使用nolocal关键字来指示变量来自于嵌套作用域。
  在开发中，我们应该尽量减少对全局变量的使用，因为全局变量的作用域和影响范围过于广泛，可能会发生意料之外的修改和使用，除此之外全局变量比局部变量拥有更长的生命周期，可能导致对象占用的内存长时间无法被垃圾回收。

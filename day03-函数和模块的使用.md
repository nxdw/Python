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

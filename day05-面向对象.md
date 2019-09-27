## 面向对象编程基础
  把一组数据和处理他们的方法组成对象（object），把相同行为的对象归纳为类（class）,通过类的封装（encapsulation）隐藏内部细节，通过继承(inheritance)实现类的特化（specialization）和泛化（generalizaiton），通过多态（polymorphism）实现基于对象类型的动态分派。   
  按照面向对象的编程理念，程序中的数据和操作数据的函数是一个逻辑上的整体，我们称之为对象。而我们解决问题的方式就是创建出需要的对象并向对象发出各种各样的消息，多个对象的协同工作最终可以让我们构造出复杂的系统来解决现实中的问题。

## 类和对象  
  简单的说，类是对象的蓝图和模板，而对象是类的实例。类似抽象的概念，而对象是具体的东西。在面向对象编程的世界中，一切皆为对象，对象都有属性和行为，每个对象都是独一无二的，而且对象一定属于某个类。当我们把一大堆拥有共同特征的对象的静态特征（属性）和动态特征（行为）都抽取出来后，就可以定义出一个叫做“类”的东西。
  
## 定义类

    class Student(object):

        # __init__ 是一个特殊方法用于在创建对象时进行初始化操作
        # 通过这个方法我们可以为学生对象绑定name和age两个属性
        def __init__(self,name,age):
            self.name = name
            self.age = age

        def study(self,course_name):
            print('%s正在学习%s.' % (self.name,course_name))

        # PEP 8 要求标识符的名字用全小写多个单词用下划线连接
        def watch_mv(self):
            if self.age < 18:
                print('%s只能观看 abc 。' % self.name)
            else:
                print('%s正在观看电影我的祖国.' % self.name)

  写在类中的函数，我们通常称之为（对象的）方法，这些方法就是对象可以接收的消息。
  
## 创建和使用对象
  当我们定义好一个类之后，可以通过下面的方式来创建对象并给对象发消息

    class Student(object):

        # __init__ 是一个特殊方法用于在创建对象时进行初始化操作
        # 通过这个方法我们可以为学生对象绑定name和age两个属性
        def __init__(self,name,age):
            self.name = name
            self.age = age

        def study(self,course_name):
            print('%s正在学习%s.' % (self.name,course_name))

        # PEP 8 要求标识符的名字用全小写多个单词用下划线连接
        def watch_mv(self):
            if self.age < 18:
                print('%s只能观看 abc 。' % self.name)
            else:
                print('%s正在观看电影我的祖国.' % self.name)

    def main():
        stu1 = Student('daxiong',26)
        stu1.study('doctor')
        stu1.watch_mv()
        stu2 = Student('jerry',14)
        stu2.study('think')
        stu2.watch_mv()

    if __name__ == '__main__':
        main()

## 访问可见性问题
  在很多面向对象编程语言中，我们通常会将对象的属性设置为私有的（private）或受保护的（protected），简单的说就是不允许外界访问，而对象的方法通常都是公开的（public）。在python中，属性和方法的访问权限只有两种，也就是公开的和私有的，如果希望属性是私有的，在给属性命名时可以用两个下划线作为开头。

    class Test:
        def __init__(self,foo):
            self.__foo = foo

        def __bar(self):
            print(self.__foo)
            print('__bar')


    def main():
        test = Test('hello')
        a = test.__bar()
        print(test.__foo)

    if __name__ == '__main__':
        main()

  但是，Python并没有从语法上严格保证私有属性或方法的私密性，它只是给私有的属性和方法换了一个名字来“妨碍”对它们的访问，事实上如果你知道更换名字的规则仍然可以访问到它们。
  
    class Test:
        def __init__(self,foo):
            self.__foo = foo

        def __bar(self):
            print(self.__foo)
            print('__bar')


    def main():
        test = Test('hello')
        test._Test__bar()
        print(test._Test__foo)

    if __name__ == '__main__':
        main()

## 面向对象的支柱
  面向对象有三大支柱：封装、继承和多态。  
  封装是“隐藏一切可以隐藏的实现细节，只像外界暴露（提供）简单的编程接口”。我们在类中定义的方法其实就是把数据和对数据的操作封装起来了，在我们创建了对象之后，只需要给对象发送一个消息（调用方法）就可以执行方法中的代码，也就是说我们只需要知道方法的名字和传入的参数（方法的外部视图），而不需要知道方法内部的实现细节。

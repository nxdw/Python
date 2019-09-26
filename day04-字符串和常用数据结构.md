## python中常用的字符串函数示例

    def main():
        str1 = 'hello,world!'
        # 通过len函数计算字符串的长度
        print(len(str1))  #  13
        # 获得字符串首字母大写的拷贝
        print(str1.capitalize()) # Hello,world!
        # 获得字符串变大写后的拷贝
        print(str1.upper()) # HELLO,WORLD!
        # 从字符串中查找子串所在位置
        print(str1.find('or')) # 8
        print(str1.find('shit')) # -1
        # 与find类似但找不到子串是会引发异常
        # print(str1.index('or')) # 8
        # print(str1.index('shit')) # -1
        # 检查字符串是否以指定的字符串开头
        print(str1.startswith('He')) # False
        print(str1.startswith('hel')) # True
        # 检查字符串是否以指定的字符串结尾
        print(str1.endswith('!'))  # True
        # 将字符串以指定的宽度居中并在两侧填充指定的字符
        print(str1.center(50,'*'))
        # 将字符串以指定的宽度靠右放置左侧填充指定的字符
        print(str1.rjust(50,'*'))
        str2 = 'abc123456'
        # 从字符串中取出指定位置的字符（下标运算）
        print(str2[2]) # c
        # 字符串切片（从指定的开始索引到指定的结束索引）
        print(str2[2:5]) # c12
        print(str2[2:]) # c123456
        print(str2[2:2]) # c246
        print(str2[::2]) # ac246
        print(str2[::-1]) # 654321cba
        print(str2[-3:-1]) # 45
        # 检查字符串是否由数字构成
        print(str1.isdigit()) # False
        # 检查字符串是否以字母构成
        print(str2.isalpha()) # False
        # 检查字符串是否以数字和字母构成
        print(str2.isalnum())  # True
        str3= '    jackf234@a.com  '
        print(str3)
        # 获得字符串修剪左右两侧空格的拷贝
        print(str3.strip())

    if __name__ == '__main__':
        main()

  除了字符串，python还内置了多种类型的数据结构，如果要在程序中保存和操作数据，绝大多数可以利用现有的数据结构来实现，最常用的包括列表、元组、集合和字典。

## 列表
  下面的代码演示了如何定义列表、使用下标访问列表元素以及添加和删除元素的操作。
  
    def main():
        list1 = [1,3,5,7,100]
        print(list1)
        list2 = ['hello'] * 5
        print(list2)
        # 计算列表长度（元素个数）
        print(len(list1))
        # 下标（索引）运算
        print(list1[0])
        print(list1[4])
        # print(list1[5]) # IndexError: list index out of range
        print(list1[-1])
        print(list1[-3])
        list1[2] = 300
        print(list1)
        # 添加元素
        list1.append(200)
        list1.insert(1,400)
        list1 += [1000,2000]
        print(list1)
        print(len(list1))
        # 删除元素
        list1.remove(3)
        if 1234 in list1:
            list1.remove(1234)
        del list1[0]
        print(list1)
        # 清空列表元组
        list1.clear()
        print(list1)

    if __name__ == '__main__':
        main()
  
#### 列表切片

    def main():
        fruits = ['grape','apple','strawberry','waxberry']
        fruits += ['pitaya','pear','mango']
        # 循环遍历列表元素
        for fruit in fruits:
            print(fruit.title(),end=' ')
        print()
        # 列表切片
        fruits2 = fruits[1:4]
        print(fruits2)
        # fruit3 = fruits # 没有复制列表只创建了新的引用
        # 可以通过完整切片操作来复制列表
        fruit3 = fruits[:]
        print(fruit3)
        fruits4 = fruits[-3:-1]
        print(fruits4)
        # 可以通过反向切片操作来获得倒转后的列表的拷贝
        fruits5 = fruits[::-1]
        print(fruits5)


    if __name__ == '__main__':
            main()

#### 列表排序
    
    def main():
        list1 = ['orange','apple','zoo','internationalization','blueberry']
        list2 = sorted(list1)
        # sorted函数返回列表排序后的拷贝不会被修改传入的列表
        # 函数的设计就应该想sorted函数一样尽可能不产生副作用
        list3 = sorted(list1,reverse=True)
        # 通过key关键字参数指定根据字符串长度进行排序而不是默认的字母表顺序
        list4 = sorted(list1,key=len)
        print(list1)
        print(list2)
        print(list3)
        print(list4)
        # 给列表对象发出排序消息直接在列表对象上进行排序
        list1.sort(reverse=True)
        print(list1)

    if __name__ == '__main__':
        main()

#### 生成列表

    import sys
    def main():
        f = [x for x in  range(1,10)]
        print(f)
        f = [x + y for x in 'ABCDE' for y in '1234567']
        print(f)
        # 用列表的生成表达式语法创建列表容器
        # 用这种语法创建列表之后元素已经准备就绪所以需要耗费较多的内存空间
        f = [x ** 2 for x in range(1,100)]
        print(sys.getsizeof(f))  # 查看对象占用内存的字节数
        print(f)
        # 请注意下面的代码创建的不是一个列表而是一个生成器对象
        # 通过生成器可以获取到数据但它不占用额外的空间存储数据
        # 每次需要数据的时候就通过内部的运算得到数据(需要花费额外的时间)
        f = (x ** 2 for x in range(1,100))
        print(sys.getsizeof(f))
        print(f)
        for val in f:
            print(val)

    if __name__ == '__main__':
        main()
        
  除了上面提到的生成器语法，python还有另一种定义生成器的方式，就是通过yield关键字将一个普通函数改造成生成器函数。下面的代码演示了如何实现一个生成菲波那切数列的生成器。
  
    def fib(n):
        a,b = 0,1
        for _ in range(n):
            a,b = b,a + b
            yield a

    def main():
        for val in fib(20):
            print(val)

    if __name__ == '__main__':
        main()

## 元组  
  python的元组与列表类似，不同之处在于元组的元素不能修改。我们把多个元素组合到一起就形成了一个元组，所以它和列表一样可以保存多条数据。下面的代码演示了如何定义和使用元组。

    def main():
        # 定义元组
        t = ('tom',26,True,'tonghai')
        print(t)
        # 获取元组中的元素
        print(t[0])
        print(t[3])
        # 遍历元组中的值
        for member in t:
            print(member)
        # 将元组转换成列表
        person = list(t)
        print(person)
        # 列表是可以修改它的元素
        person[0] = 'daxiong'
        person[1] = 18
        print(person)
        # 将列表转换成元组
        fruits_list = ['apple','banana','orange']
        fruits_tuple = tuple(fruits_list)
        print(fruits_tuple)

    if __name__ == '__main__':
        main()

#### 探讨
  为什么我们已经有列表这种数据结构，还需要元组这样的类型呢？   
  1.元组中的元素是无法修改的，事实上我们在项目中尤其是多线程环境（后面会讲到）中可能更喜欢使用的是那些不变对象（一方面因为对象状态不能修改，所以可以避免由此引起的不必要的程序错误，简单的说就是一个不变的对象要比可变的对象更加容易维护；另一方面因为没有任何一个线程能够修改不变对象的内部状态，一个不变对象自动就是线程安全的，这样就可以省掉处理同步化的开销。一个不变对象可以方便的被共享访问）。所以结论就是：如果不需要对元素进行添加、删除、修改的时候，可以考虑使用元组，当然如果一个方法要返回多个值，使用元组也是不错的选择。   
  2.元组在创建时间和占用的空间上面都优于列表。我们可以使用sys模块的getsizeof函数来检查存储同样的元素的元组和列表各自占用了多少内存空间，这个很容易做到。我们也可以在ipython中使用魔法指令%timeit来分析创建同样内容的元组和列表所花费的时间。

## 集合
  python中的集合跟数学上的集合是一致的，不允许有重复元素，而且可以进行交集、并集、差集等运算。

    def main():
        set1 = {1,2,3,3,3,4}
        print(set1)
        print('Length =',len(set1))
        set2 = set(range(1,10))
        print(set2)
        set1.add(4)
        set1.add(5)
        set2.update([11,12])
        print(set1)
        print(set2)
        set2.discard(5)
        # remove的元素如果不存在会引发KeyError
        if 4 in set2:
            set2.remove(4)
        print(set2)
        # 遍历集合容器
        for elem in set2:
            print(elem ** 2,end=' ')
        print()
        # 将元组转换成集合
        set3 = set((1,2,3,4,2,1))
        print(set3.pop())
        print(set3)
        # 集合的交集、并集、差集、对称差运算
        print(set1,set2)
        print(set1 & set2)
        # print(set1.intersection(set2))
        print(set1 | set2)
        # print(set1.union(set2))
        print(set1 - set2)
        # print(set1.differenct(set2))
        print(set1 ^ set2)
        # print(set1.symmetric_difference(set2))
        # 判断子集合超集
        print(set2 <= set1)
        # print(set2.issuperbset(set1))
        print(set3 <= set1)
        # print(set3.issuperbset(set1))
        print(set1 >= set2)
        # print(set1.issuperbset(set2))
        print(set1 >= set3)
        # print(set1.issuperbset(set3))
    if __name__ == '__main__':
        main()  
  
## 字典
  字典是另一种可变容器模型，类似于我们生活中使用的字典，它可以存储任意类型对象，与列表、集合不同的是，字典的每个元素都是由一个键和一个值组成的“键值对”，键和值通过冒号分开。下面的代码演示了如何定义和使用字典。
  
    def main():
        scores = {'tom':98,'jerry':97,'daxiong':100}
        print(scores['tom'])
        print(scores['daxiong'])
        for elem in scores:
            print('%s\t--->\t%d' % (elem,scores[elem]))
        scores['jerry'] = 77
        scores['daxiong'] = 101
        print(scores)
        if 'kit' in scores:
            print(socres['kit'])
        print(scores.get('kit'))
        print(scores.get('kit',57))
    main()

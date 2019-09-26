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

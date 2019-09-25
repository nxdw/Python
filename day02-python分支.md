## if判断语句的使用 
  由if、elif、else关键字构成，多个判断语句可以嵌套，在python中用缩进的方式来设置代码的层次结构。  
  username = input('请输入用户名：')  
  password = input('请输入口令：')    
  if username == 'admin' and passwd == '123456':    
    print('success')    
  else:    
    print('failer')    

  if condition:   
  	print(....)   
  elif:   
  	print(....)   
  else:   
    print(....)   

## for-in 循环结构  
  如果已知循环次数，这用for-in循环即可
  for x in range(100):  
  	sum += x  
  print(sum)  
  
## range类型  
  range类型可以用来产生一个不变的数值序列，而且这个序列通常都是用在循环中的  
  - range(101) 可以产生一个0到100的整数序列。  
  - range(1,100) 可以产生一个1到99的整数序列。  
  - range(1,100,2) 可以产生一个1到99的奇数序列，其中的2是步长值。  
  
## while循环
  如果对循环次数未知，则使用while循环。while循环通过一个能够产生或转换出bool值得表达式来控制循环，表达式值为True则循环继续，表达式值为False则循环结束。
  
	import random  
	answer = random.randint(1,100)  
	counter = 0  
	while True:  
		counter += 1  
		number = int(input('请输入：'))  
		if number < answer:  
			print('猜大一点')  
		elif number > answer:  
			print('小一点')  
		else:  
			print('seccess')  
			break  
	print('you summer test %d' % counter)  
	if counter > 7:  
		print('you have a little stuppied')    
		
	
	for i in range(1,10):
		for j in range(1,10):
			print('%d*%d=%d' % (i,j,i * j),end='\t')
		print( )
  

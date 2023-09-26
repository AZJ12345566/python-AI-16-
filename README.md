# python-AI-16-
python+AI笔记(16)
# 一阶-八章-文件的读取操作
#打开文件
f=open("D:/测试.txt",'r',encoding="UTF-8")
print(type(f))  #是一个对文本文件进行操作的对象

#读取文件-read()
print(f.read(10)) #读取10个字符(反正输出汉字是10个汉字)
print(f.read())  #在程序中多次read下一个read会在上一个read后接着读取

#读取文件-readlines()  #读取文件的全部行，封装到列表中
lines=f.readlines()
print(type(lines))
print(lines)   #这里输出啥都没有，因为他也是续接上一个read的后面

#readline()和上一个就少了一个s，readline一次去读取一行
line1=f.readline()
line2=f.readline()
line3=f.readline()
print(line1)
print(line2)
print(line3)

#for循环读取文件行
for line in f:
    print(line)  #每一次打印一行的数据

#关闭文件对象close()
f.close()

#with open 语法操作文件
with open("D:/测试.txt",'r',encoding="UTF-8") as f:
    for line in f:
        print(line)
#with open的作用是自动将文件关闭，通过这种方法避免遗忘close

# 一阶-八章-文件读取的课后练习讲解
#通过文件读取操作，读取此文件，统计bala单词出现的次数
#1.read(),count("bala")
#2.一行行的读取文件按照空格切分，统计bala的次数

#打开文件，以读取模式打开
f=open("D:/word.txt","r",encoding="UTF-8")

#用count方法统计
content=f.read()
count=content.count("bala")
print(count)  #在文件中出现了多少次bala就输出多少

#读取内容，一行一行读取
count=0  #使用count变量来累计bala出现的次数
for line in f:
    line=line.strip()  #通过strip去除开头和结尾的空格以及换行符
    words=line.split(" ")
    print(words)
    for word in words:
        if word=="bala"
            count+=1
#判断单词出现次数并累计
print(count)

#关闭文件
f.close()

# 一阶-八章-文件的写入操作
#直接调用write，内容并未真正写入文件，而是放在缓冲区里
#当调用flush的时候，内容才会真正被写入文件
#这样避免频繁操作硬盘，效率更高

#打开文件，文件不存在
f=open("D:/test.txt",'w',encoding="UTF-8")  #文件不存在，在w的模式下，系统会自动帮你创建文件
f.write("Hello World!")  #内容写入内存中
#flush刷新
f.flush()  #这一步才会将内容写入进硬盘中
f.close()  #close是内置了flush函数的功能

#打开一个已经存在的文件
f=open("D:/test.txt",'w',encoding="UTF-8")
#write写入、flush刷新
f.write("bala")  #文件存在，则会直接清空内容，重新开始写入内容
f.close()

# 一阶-八章-文件的追加写入操作
#和上一节差不多，追加就将w模式替换成a模式

#打开一个不存在的文件
f=open("D:/test.txt","a",encoding="UTF-8")
#write写入
f.write("bala)
f.flush()
f.close()

#打开一个已经存在的文件
f=open("D:/test.txt","a",encoding="UTF-8")
f.write("\ncala")  #原有内容不变，新内容追加在后面
f.close()

# 一阶-八章-文件操作的综合案例
#打开文件，并且读取内容
fr=open("D:/bill.txt","r",encoding="UTF-8")
#打开文件获得文件对象，准备写入
fw=open("D:/bill.txt","w",encoding="UTF-8")
#for循环读取文件
for line in fr:
    line=line.strip()
    #判断内容，将满足的内容写出
    if line.split(",")[4]=="测试"：
        continue
    fw.write(line)
    #由于前面对内容进行了strip操作，所以要手动添加换行符
    fw.write("\n")

fr.close()
fw.close()

# Shell编程

### 1.基本概念

- Shell是一个命令解析器，可以接收应用程序或用户命令，然后访问操作系统内核
- Shell是一个功能强大的编程语言，易编写，易调试，灵活性强

### 2.执行Shell程序的方式

- 方式一：./文件名，此方式需要执行权限
- 方式二：/bin/bash 文件名，此方式不需要执行权限

### 3.基本编写

```shell
#!/bin/bash
#打印输出HelloWorld!
echo HelloWorld!
```



### 4.变量的定义

- 语法格式
  	- 定义变量：变量=值
  	- 撤销变量：unset 变量
- 定义规则
  - 变量名称可以由字母，数字和下划线组成，但不能以数字开头，环境变量名建议大写
  - 不能使用bash里的关键字
  - 中间不能有空格，可以有下划线
  - 在bash中，变量默认类型都是字符串类型，无法直接进行数值运算
  - 变量的值如果有空格，需要使用双引号或单引号括起来

### 5.常用的运算符

#### 算术运算符

| 运算符 | 说明                   | 举例                            |
| ------ | ---------------------- | ------------------------------- |
| +      | 加法                   | `expr $a + $b`                  |
| -      | 减法                   | `expr $a - $b`                  |
| *      | 乘法                   | `expr $a \* $b`                 |
| /      | 除法                   | `expr $a / $b`                  |
| %      | 取余                   | `expr $a % $b`                  |
| =      | 赋值                   | lc=$lb 表示将变量lb的值赋值给lc |
| ==     | 相等，相同返回true     | [ $a == $b ]                    |
| !=     | 不相等，不相同返回true | [ $a != $b ]                    |

代码示例：

```shell
#!/bin/bash

#定义两个变量
la=5
lb=9

#打印两个变量的数值
echo "ia=$la"
echo "ib=$lb"

#实现加法运算，要求+两边必须有空格
echo `expr $la + $lb`

#其他方式实现加法运算
#方式二,此处加号两边并不要求有空格
lc=$[$la+$lb]
echo $lc
#方式三,此处加号两边并不要求有空格
ld=$(($la+$lb))
echo $ld
```



#### 关系运算符

| 运算符 | 说明                                 | 英文                    | 举例                   |
| ------ | ------------------------------------ | ----------------------- | ---------------------- |
| -eq    | 检测两个数是否相等，相等返回true     | equal                   | [ $a -eq $b ]返回true  |
| -ne    | 检测两个数是否不相等，不相等返回true | not equal               | [ $a -ne $b ]返回false |
| -gt    | 判断左边的数是否大于右边的           | greater than            | [ $a -gt $b ]返回false |
| -lt    | 判断左边的数是否小于右边的           | less than               | [ $a -lt $b ]返回false |
| -ge    | 判断左边的数是否大于等于右边的       | Greater than or qual to | [ $a -ge $b ]返回false |
| -le    | 判断左边的数是否小于等于右边的       | Less than or equal to   | [ $a -le $b ]返回false |

代码示例：

```
#!/bin/bash

#定义一个简单的系统
number=5000
echo $number

if [ $number -eq 520 ]
then
   echo "真的爱你"
elif [ $number -lt 520 ]
then
   echo "爱你一点也没少"
else
   echo "爱你真的很深"
fi
```



### 6.流程控制语句

#### if判断

```shell
if [ 条件判断式 ] 
  then
    程序 
fi
```

#### case语句

```shell
case $变量名 in 
  "值1"） 
    如果变量的值等于值1，则执行程序1 
    ;; 
  "值2"） 
    如果变量的值等于值2，则执行程序2 
    ;; 
  …省略其他分支… 
  *）
  如果变量的值都不是以上的值，则执行此程序
  ;; 
esac 
```

**示例代码：**

```shell
#!/bin/bash
#提示用户输入1~4之间的整数，并且将该整数记录到变量中
echo "请输入1~4之间的整数"
read number #表示读取一个整数到变量number中

#使用case语句进行打印
case $number in
    1) echo "1:云想衣裳花想容"
    ;;
    2) echo "2:男儿和不带吴钩"
    ;;
    3) echo "3:天生我材必有用"
    ;;
    4) echo "4:千金散尽还复来"
    ;;
    *) echo "没有选择1~4"
    ;;
esac

```

#### for循环

```shell
for (( 初始值;循环控制条件;变量变化 )) 
do
  程序 
done
```

**示例代码：**

```shell
#!/bin/bash

#使用for循环打印1~100的累加和

sum=0;

for(( i=1;i<=100;i++ ))
do
  sum=$[$sum+$i]
done

#打印最终结果
echo $sum

```

#### while循环

```shell
while [ 条件判断式 ] 
do
  程序 
done
```

**示例代码：**

```shell
#!/bin/bash

#使用while循环，实现1~100的累加和

sum=0
i=1

while [ $i -le 100 ]
do
  sum=$[$sum+$i]
  i=$[$i+1]
done

echo $sum
```

#### 函数

```shell
#注：此处[]可加可不加
[ function ] funname[()] 
{ 
  Action; 
  [return int;] 
}
funname
```

**示例代码：**

```shell
#!/bin/bash

#定义一个函数，计算两个输入数据的和
function sum()
{
    s=$[$a+$b]
    echo $s
}

#提示用户从键盘输入两个数据
read -p "请输入第一个数字" a
read -p "请输入第二个数字" b

#调用函数
sum $a $b
echo $sum

```


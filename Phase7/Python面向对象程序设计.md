

# Python面向对象程序设计

### 方法

##### 构造方法

* `__init__`构造方法

  ```python
  class Student:
      name=None
      age = None
      tel = None
  
      del __init__(self,name,age,tel):
      self.name = name
      self.age = age
      self.tel = tel
      print("Student类创建了一个类对象")
  
  stu = Student("周杰伦",31,"18500006666")
  print(stu.name)
  print(stu.age)
  print(stu.tel)
  ```

##### 魔术方法

python内置的类方法，各自有各自特殊的功能

* `__str__`字符串方法

控制类转换为字符串的行为

返回值：字符串

```python
class Student:
    def __init__(self, name, age):
        self.name = name  # 学生姓名
        self.age = age    # 学生年龄

    # __str__ 魔术方法
    def __str__(self):
        return f"学生姓名：{self.name}, 年龄：{self.age}"

stu = Student("周杰伦", 11)
print(stu)          # 会调用 __str__ 方法
print(str(stu))     # 也会调用 __str__ 方法
```

* `__lt__`小于、大于符号比较

  传入参数：other,另一个对象

  返回值：True或False

  ```python
  class Student:
      def __init__(self, name, age):
          self.name = name
          self.age = age
  
      # 定义小于比较：按年龄比较
      def __lt__(self, other):
          return self.age < other.age
  
  stu1 = Student("周杰伦", 11)
  stu2 = Student("林豪杰", 13)
  
  print(stu1 < stu2)  # 结果：True
  print(stu1 > stu2)  # 结果：False
  ```

* `__le__`小于等于、大于等于符号比较

  传入参数：other,另一个对象
  
  返回值：True或False
  
  ```python
  class Student:
      def __init__(self, name, age):
          self.name = name
          self.age = age
  
      # 定义小于等于比较：按年龄比较
      def __le__(self, other):
          return self.age <= other.age
  
  stu1 = Student("周杰伦", 11)
  stu2 = Student("林军杰", 13)
  
  print(stu1 <= stu2)  # 结果：True
  print(stu1 >= stu2)  # 结果：False
  ```

* `__eq__`==符号比较

  传入参数：other,另一个对象
  
  返回值：True或False
  
  ```python
  class Student:
      def __init__(self, name, age):
          self.name = name
          self.age = age
  
      # 定义等于比较：按年龄比较
      def __eq__(self, other):
          return self.age == other.age
  
  stu1 = Student("周杰伦", 11)
  stu2 = Student("林军杰", 11)
  
  print(stu1 == stu2)  # 结果：True
  ```
  
  注：对象之间可以比较，但是是比较内存地址，也即是：不同对象 `==` 比较一定是 `False` 结果。
  
### 面向对象的三大特性

  **封装**  **继承**  **多态**

  ##### 封装

  将现实世界事物封装到类中，从而完成程序对现实世界事物的描述

  ![15](D:\Geek考核\Phase7\Phase7-png\15.png)

* 私有成员
  * 定义：用**双下划线 `__` 开头**来定义私有成员
  * 特点：
    - 外部**不能直接访问 / 修改**私有成员，否则会报错或无效。
    - 私有成员无法被类对象使用，但是可以被其他的成员（类内部的）使用。
  * 意义:在类中提供仅供内部使用的属性和方法，而不对外开放使用（类对象无法使用）

```python
class Phone:
    __current_voltage = None


    def __keep_single_core(self):
        print("让CPU以单核模式运行")

phone = Phone()
# phone.__keep_single_core()
print(phone.__current_voltage)

#会报错
```

```python
#定义一个类，内含私有成员变量和私有成员方法
class Phone:
    __current_voltage = 0.5

    def __keep_single_core(self):
        print("让CPU以单核模式运行")

    def call_by_5g(self):
        if self.__current_voltage >= 1:
            print("5g通话已开启")
        else:
            self.__keep_single_core()
            print("电量不足，无法使用5g通话，并已设置为单核运行进行省电")

phone = Phone()
phone.call_by_5g()

#让CPU以单核模式运行
#电量不足，无法使用5g通话，并已设置为单核运行进行省电
```

##### 继承

```
class  类名(父类名):
	类内容体
```

继承分为单继承（继承单个父类）和多继承（继承多个父类）

继承表示：将从父类那里继承（复制）来成员的变量和成员方法（不含私有）

* 单继承

  ```python
  #单继承
  class Phone:
      IMEI = None          # 序列号（类属性）
      producer = "HM"      # 厂商（类属性）
  
      def call_by_4g(self):
          print("4g通话")
  
  # Phone2022 继承 Phone 类
  class Phone2022(Phone):
      face_id = "10001"    # 新属性：面部识别ID
  
      def call_by_5g(self):
          print("2022年新功能：5g通话")
  
  phone = Phone2022()
  print(phone.producer)
  phone.call_by_4g()
  phone.call_by_5g()
  print(phone.face_id)
  print(phone.IMEI)
  ```

  ```
  D:\Scripts\python.exe "D:\Tools\PyCharm\PyCharmProject\py_project01\第四章 - 面向对象程序设计\7.继承的基础语法.py" 
  HM
  4g通话
  2022年新功能：5g通话
  10001
  None
  
  进程已结束，退出代码为 0
  
  ```

* 多继承

```
class 类名(父类1，父类2,.....,父类N)
	类内容体
```

注：多个父类中，如果有同名的成员，那么默认以继承顺序（从左到右）为优先级

即：先继承的保留，后继承的覆盖

```python
class Phone:
    IMEI = None          # 序列号（类属性）
    producer = "HM"      # 厂商（类属性）

    def call_by_4g(self):
        print("4g通话")
class NFCReader:
    # 类属性：NFC类型、生产商
    nfc_type = "第五代"
    producer = "HM"

    # 方法：NFC读卡
    def read_card(self):
        print(f"{self.producer} {self.nfc_type} NFC 读卡功能已开启")

    # 方法：NFC写卡
    def write_card(self):
        print(f"{self.producer} {self.nfc_type} NFC 写卡功能已开启")
class RemoteControl:
    # 类属性：遥控类型
    rc_type = "红外遥控"

    # 成员方法：开启遥控功能
    def control(self):
        print("红外遥控开启了")

# 子类：同时继承三个父类（多继承）
class MyPhone(Phone, NFCReader, RemoteControl):
    pass

# 测试代码
phone = MyPhone()

# 调用父类 Phone 的方法
phone.call_by_4g()    # 输出：4g通话

# 调用父类 NFCReader 的方法
phone.read_card()     # 输出：NFC读卡
phone.write_card()    # 输出：NFC写卡

# 调用父类 RemoteControl 的方法
phone.control()       # 输出：红外遥控开启了
```

```
D:\Scripts\python.exe "D:\Tools\PyCharm\PyCharmProject\py_project01\第四章 - 面向对象程序设计\7.继承的基础语法.py" 
4g通话
HM 第五代 NFC 读卡功能已开启
HM 第五代 NFC 写卡功能已开启
红外遥控开启了

进程已结束，退出代码为 0
```

> `pass` 是 Python 中的**空语句**，它的字面意思就是 “跳过 / 什么都不做”—— 当 Python 解释器执行到 `pass` 时，不会执行任何操作，直接跳过。

* 复写

  * 定义：当子类继承父类后，如果对父类的属性或方法 “不满意”，可以在子类中重新定义同名的属性或方法，这就是复写。复写后，子类对象在调用该属性或方法时，会优先使用子类自己的版本，而不是父类的。

* 调用被复写的父类成员

  * 1. 方式 1：直接通过父类名调用

    成员变量：`父类名.成员变量`
    成员方法：`父类名.成员方法(self)`（必须显式传入 `self`）
    
  * 2. 方式 2：通过 `super()` 调用
  
    成员变量：`super().成员变量`
    成员方法：`super().成员方法()`（不需要传 `self`）

```python
class Phone:
    IMEI = None          # 序列号
    producer = "ITCAST"  # 厂商

    def call_by_5g(self):
        print("使用5g网络进行通话")

# 定义子类，复写父类成员
class MyPhone(Phone):
    producer = "ITHEIMA"  # 复写父类的成员属性

    def call_by_5g(self):
        # 子类新增的前置逻辑
        print("开启CPU单核模式，确保通话的时候省电")
        #调用被复写的父类成员
        #方式1
        print(f"父类的厂商是:{Phone.producer}")
        #方式2
        print(f"父类的厂商是:{super().producer}")
        # 调用父类的call_by_5g方法，复用原有逻辑
        super().call_by_5g()
        # 子类新增的后置逻辑
        print("关闭CPU单核模式，确保性能")

# 测试
phone = MyPhone()
print(phone.producer)  # 输出：ITHEIMA（复写后的属性）
phone.call_by_5g()
```

```
D:\Scripts\python.exe "D:\Tools\PyCharm\PyCharmProject\py_project01\第四章 - 面向对象程序设计\9.继承_复写和使用父类成员.py" 
ITHEIMA
开启CPU单核模式，确保通话的时候省电
父类的厂商是:ITCAST
父类的厂商是:ITCAST
使用5g网络进行通话
关闭CPU单核模式，确保性能

进程已结束，退出代码为 0
```

##### 多态

* 定义：

  指多种状态，即完成某个行为时，使用不同的对象会得到不同的状态

  本质是：同一个行为，在不同对象上表现出不同的状态。

  在继承关系中，它表现为：

  - 函数 / 方法的形参声明为**父类类型**（如 `Animal`）。

  - 实际传入的是该父类的任意**子类对象**（如 `Dog`、`Cat`）。

  - 调用同一个方法（如 `speak()`）时，会根据传入对象的真实类型，执行对应子类的复写逻辑，从而得到不同的结果。

    ```python
    # 父类 Animal
    class Animal:
        def speak(self):
            pass  # 定义一个抽象方法，子类必须复写
    
    # 子类 Dog，继承 Animal
    class Dog(Animal):
        def speak(self):
            print("汪汪汪！")
    
    # 子类 Cat，继承 Animal
    class Cat(Animal):
        def speak(self):
            print("喵喵喵！")
    
    #父类的作用：确定子类必须具备哪些方法（定义 “规范”）。
    #子类的作用：自行决定这些方法的具体实现（填充 “细节”）。
    
    # 多态函数：接收父类 Animal 类型的参数
    def make_noise(animal: Animal):
        animal.speak()  # 调用方法，具体行为由传入的子类对象决定
    
    # 测试
    dog = Dog()
    cat = Cat()
    
    make_noise(dog)  # 输出：汪汪汪！
    make_noise(cat)  # 输出：喵喵喵！
    ```

  * 抽象类（接口）

    抽象类：含有抽象方法的类(如Animal)。

    抽象方法：方法体为空实现（`pass`），不提供具体逻辑，仅用于定义规范

    抽象类就好比定义一个标准，包含了一些抽象的方法，要求子类必须实现

    抽象类配合多态，完成

    * 抽象的父类设计（设计标准）
    * 具体的子类实现（实现标准）

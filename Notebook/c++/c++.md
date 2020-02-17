#c++

## 基础语法篇
### 第一部分

1. 关键字const ，程序在运行期间不能改变。
2. 将一个int类型的变量，赋值给char类型。只将int的（二进制表示）的低8位转化为char
3. continue 结束本次循环，break，结束switch或者循环
4. 输入输出流控制字符

    | 控制符                           | 作用                           |
    | -------------------------------- | ------------------------------ |
    | dec                              | 设置数值的基数位10             |
    | hex                              | 设置数值的基数位16             |
    | oct                              | 设置数值的基数位8              |
    | setfill（c）                     | 设置填充字符位c                |
    | setw（n）                        | 设置字符宽度为n                |
    | setprecision（n）                | 设置显示精度位n                |
    | setiosflags（iOS：：fixed）      | 设置浮点数以固定的小数位数显示 |
    | setiosflags（iOS：：scientific） | 设置科学计数法显示             |
    | setiosflags（iOS：：left）       | 输出数据左对齐                 |
    | setiosflags（iOS：：right）      | 输出数据右对齐                 |
    | setiosflags（iOS：：skipws）     | 忽略前导的空格                 |
    | setiosflags（iOS：：uppercase）  | 数据以16进制输出端时字母大写   |
    | setiosflags（iOS：：showpos）    | 输出整数时给出“+”号            |
   ==在程序开头需要添加iomanip头文件==
   
   ````c++
   double a=123.456789;
   cout<<setiosflags(ios::scientific)<<setprecision(4)<<a;
   int b;
   cout<<setfill('*')<<setw(10)<<b;
   ````
5. 函数模板 tamplate<typeanme T>
6. 静态局部变量 static 函数在调用完之后并不释放静态局部变量的内存，下一次函数调用时保持原值。对于静态局部变量的赋值只有在第一次赋值时进行赋值，之后调用函数，函数里面的赋值函数不在生效。
7. 静态变量和动态变量是从函数存储周期方面来说的，在函数运行期间会不会动态的开辟动态的释放，还是从头到尾一直有效。
8. extern 从a文件中引用b文件中的变量num，应该在a文件中声明 extren int num
9. **内部函数：如果一个函数只能被本文件中的其他函数调用，则成为内部函数。内部函数的一般格式为：**==内部函数又成为静态函数==
     ````c++
        static int fun(){}
    ````
10. 如果函数之前被extern声明则是一个外部函数。
11. string为c++的一个字符串类。并不是c++的基本元素之一。需要引用头文件<string>.
12. 指针变量即地址变量。用来存放一个地址的变量。
    1.  定义方法：在一个变量之前加上*，代表是一个指针变量。
        ````C++ 
          float *pointer_1;
           int * pointer_2;
        ````
        ==*pointer_1应该指向一个变量而不是一个数值。==
        例如：int * pointer_3 =*pointer_2;
        *pointer_2是一个值，而*pointer_3需要指向一个变量，因此赋值语句不正确。
    2. 赋值:只需要将被指向的变量地址赋值给指针变量即可。‘
        ````c++
        point_1 =&i;
        pointer_2=&j;
        ````
13. 数组元素的名称就是数组元素的指针（指针）。 
        ````    
        int *pointer_1 ;int a[];
        pointer_1=a;
        ````
14. ==可以使用一个指针指向字符串的首地址，来代表一个字符串。就类似数组。==例：char * pointer1 ="I love China";
15. ==函数与指针==
    1.  int （*p） (int a,int b)  p为指向函数的指针，函数没有名字。
        ````C++ 
        int max(int a,int b);
        int *p(int a,int b);
        p=max;//指针赋值语句 函数名字也是一个地址
        cout<<p(a,b)<<endl;
        ````
    2. 用指向函数的指针作为参数
        ````
        double integral(double a,double b, double (*fun)(double))
        ````
    3. 返回指针的函数
        ````C++ 
        int* a(int ,int )
        ````

    4. 指针数组
       ```` c++
       int *p [4];
       ````
    5.  指向指针的指针
        ```` c++
            char * (*p);
            char **p;


            char **p;
            char *name[]={"BASIC","FORTRAN","c++"};
            p== name +2;
            cout<<*p<<endl;//c++
            cout<<**p<<endl;//c
          ````
    6. const 指针 指针变量是一个常量或者指向的对象是一个常量
       1. const 类型名 * 指针变量名
        ==不允许通过指针两变量改变他指向对象的值。但是指针的指向是可以改变的==
         ```` c++
         int a=15，b=16;
        const int * p=&a;
        *p=15/ --非法--
         p=&b;//合法
         ````
    7. 常指针 ==指针的指向不能改变==
       1. char * const p1="China";
    8. void 指针 ：指向空类型或者不指向“确定的类型”的数据
16. ==引用==
    1.  变量的引用
       ```` c++
       int a ;
       int &b=a;  //这个时候为变量的引用

       int *c=&a;//这个时候为取地址符号
       ````
       ==1. 变量的引用必须在引用的时候对其进行初始化 2. 不能进行引用的引用 3. 不能引用数组==
    2. 引用作为函数的参数
        ==引用的主要作用是作为函数的参数使用引用==
17. 结构体
    1.  struct 名字 {}；
18.使用new和delete动态的开辟空间
    1. new  范围开辟空间的首地址或者地址
        new int ==不需要添加括号作为函数调用==
        new int（100） 初始化为100,返回空间的地址
        new char[10]; 返回字符字符数组的首地址
        float flo =new float(3.1415);
    2. delete 撤销一段空间
       1. delete 指针变量
       2. --delete[] 指针变量 --
             ```` c++
             char * p =new char[10];
             delete [] p;
             ````
        3. new返回值是一个地址.可以使用new返回一个结构体的首地址
              ```` c++
               student *p =new Student ;==不需要添加括号==
             ````
19. ==枚举==
    1.  enum 枚举类型名称 {枚举常量表}
            ```` c++
            enum {sun,mon,yue,wed,thu,fri,sat} workday;
            waokday=sun;//此时workday为1,输出workday的值也为1;

             ````
    2. 枚举类型不能才用数据进行赋值
       1. workday=1 ; //错误
       2. 但是可以使用强制类型转换; workday =(workday)2;
    3. 枚举类型和数组的使用方法差不多,但是他的值只能为枚举类型中的那几个


##第二部分 
### 类和对象
1. ==面向对象的4个特点:抽象.封装.继承.多态==
2. 对象的两个要素:属性和行为
3. 类并不占用内存空间.每一个对象在初始化时分配空间.
4. 类的初始化:
   1. 构造函数:构造函数不带有返回值类型,默认返回为类的类型
   2. 构造函数在类外定义时也不需要带有返回值类型.但是需要添加类的限定符
      1. ```` c++
             class Time{
                 public :
                 int minute,houre,day;
                 static int mounse;
                    Time();
                    Time(int a,int b,int c);
             }
            Time::Time(){}
          ````
    3. 带参构造函数
       1. Time::Time(int a,int b,int c):minute(a),houre(b),day(c){}
    4. 析构函数 :类名前面添加一个~ (c++中~是取反运算符) ~Time()
    5. 析构函数的调用顺序与构造函数刚好相反.
    6. ==类中的静态成员:==
       1. 使用static关键字声明
       2. 类的所有对象中的静态数据成员的值都一样.
       3. 静态数据成员占用内存
       4. 静态成员在一个公共的内存当中,不属于任何一个对象.因此访问时使用Time::munse
    7. 静态成员函数:使用static声明
       1. 只允许使用静态成员函数访问静态成员变量
    8. ==友元函数==
       1. 在类的定义中可以声明一个外部普通函数为友元函数.
             ```` c++
            class Time{
                pubilc:
                    Time();
                    Time(int a,int b);
                    friend void display(Time &);
                private:
                int hour;
                int minute;
            }
              friend void display(Time &t){
                  cout<<t.hour<<t.minute<<endl;
              }
             ````
        2. 友元函数不仅可以是一个普通的函数,也可以是另一个类的成员函数.==想访问哪个类(a)的成员,需要在哪个类(a)中声明外部的友元函数.
        3. 友元类:不仅可以将一个方法生命为友元函数,也可以将一个类声明为友元类.这有友元类就可以访问另一个类中所有的成员.
    9. 类模板
       1.  template<class 类型参数名>
           ````C++ 
            template<class numbertype>   //不需要添加分号
             class Compare{
             public :
             Compare(numbertype a,numbertype b);
             numbertype max();
             }
             //外部定义
            numbertypr Compare<numbertype> :: max(){}

            //定义对象
            Compare<int> com(4,7);

           ````
5. ==运算符重载==
   1. 运算符重载的本质是函数的重载
   2. 运算符重载的一般格式:
      1. ==函数类型 opeartor 运算符名称 (形参表)==
   3. 一般运算符的重载是对类进行操作.一般的有两种处理方式,一个是作为成员函数,另一个是作为友元函数.
   4. ==重载流插入和提取运算符==
       1. 重载流插入运算符"<<"
         ````C++ 
         ostream & operateor <<(ostream &output,另一个参数){ /
            //函数主体
            return output;
         }
         ````
       2. 重载流输出运算符">>"
        ````C++
        istream & operater >>(istream & inputstream ,另一个参数){

            return inputstream;
        }
        ````

6. 类型转换
   1. c类型转换 (int)a
   2. C++类型转换 int (a);

##面向对象程序设计
1. 继承:pubilc private protected
    C++中默认继承方式为私有继承
2. 派生类的构造函数
   1. ==派生类构造函数名(总参列表):基类构造函数名(参数表){派生类中新加成员的初始化语句}
    ```C++ 
    Student1::Student1(int n,int name,char s,int a,string ad):Student(n,name,s);
    Student1::Student1(int n,int name ,char s,int a,string ad):Student(n,name,s),age(a),addr(ad){}
    ```
3. 多重继承声明方式
    class D :public A ,private B ,protected C {D中新加的成员}
4. 多重继承类的构造函数 
    派生类构造函数名(总参列表):基类1中的构造函数(参数列表),基类二中的构造函数(总参列表),基类三中的构造函数(参数列表){派生类中新增数据成员的赋值语句}
5. 虚基类:在继承同一个基类的时候只保留一份成员.
    ```C++
    class A{ }  

    classB :virtual public A {}   

    class C :virtual A { }  

    class D:public A,public B {}  
    ```
6. 虚函数 :
   1. 复杂着呢
   2. 纯虚函数
      1. 定义:virtual 函数类型名 函数名(参数列表)=0;=0 并不是赋值语句而是声明这是一个纯虚函数,纯虚函数无法定义对象,只是被子类作为调用的接口.



#输入输出流
**C++的输入输出更加安全,建议使用C++的输入输出**
1. C++的输入输出有两个基类:iOS类和streambuf类
   类名| 作用 | 头文件
   ---| --- | ---|
   iostream|通用输入输出流的基类|iostream
   fstream|输入输出文件流| fstream
   strstream| 输入输出字符串流|strstream
2. 流成员的控制符
    流成员函数 | 与之相同的控制符 | 作用
    ---| --- | ---|
    precison()|setprecision()
    width()|setw()
    fill( )|setfill()
    setf()|setiosflags()|
    unsetf()|resetioflags()|


    个时标志| 作用
    ---| ---| 
    ios::left|左对齐
    ios::right|右对齐
    ios::internal|符号位左对齐,数值位右对齐,中间由字符填充
    ios::dec | 10进制
    ios :: oct |8进制
    ios:: hex | 基数为16
    ios::showbase |强制输出整数的基数(八进制0打头,16进制0x打头)
    iosshowpoint|强制输出浮点数的小数点和尾数0
    ios::uppercase|在以科学计数法格式E和以十六进制输出字母时大写
    ios::showpos |显示+号
    ios::scientific|科学计数法显示
    ios::fixed |浮点数以定点格式显示
    ios::unitbuf |每次输出之后刷新所有的流
    ios::stdio |每次输出之后清除stdout,stderr

3. ==流成员函数put输出字符==
   1. put函数只用来输出一个字符
   2. put()函数的参数可以是一个字符也可以是ASCII 代码
   3. 可以在一条语句中连续使用put()
    ```C++
    cout.put('a').put('b').put('c').put('d');
    ```
4. ==用于字符输入的流函数
   1. get() :用来从之指定的流中读取一个字符 cin.get()
   2. 该方法类似于c中的getchar()
   ```c++ 
   while((c=cin.get())!=EOF) //从键盘逐字读取一行字符
   ```
   3. 带参数的get() :用法为cin.get(ch);读取成功返回非0,结束或者失败返回0;
   4. ==带参数的get()==:cin.get(字符数组,字符个数,终止字符),遇到终止字符也会读取,但不会保存到数组当中去(指针会后移)
   5. ==getline()== :cin.getline(字符数组或者字符指针,字符个数,终止字符) cin.getline(ch,20,'/')==读取19个字符,最后添加/0存放到ch中
   6. **eof** end of file 
   7. **peek** peek 是观察的意思 cin.peek() 返回的是当前指针指向的当前字符 ,观察结束之后  指针并不会后移.






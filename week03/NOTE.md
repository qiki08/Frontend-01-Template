Expression -- 表达式
    1、运算符的优先级 -- 数的结构
        MemberExpression -- 访问成员，属性访问
            a.b
            a[b] -- b可以是变量，a['b']等同于a.b
            foo`String` 
            super.b -- super关键字，只能在构造函数中使用，调用父类的方法或属性，下同
            super[b] 
            new.target -- 只能在构造函数中使用
            new Foo() 带()的优先级更高  new new foo() == new (new foo())

        var name = 'winter';
        `hellow ${name} !`

        reference -- delete,assign
        Call -- 函数调用，优先级小于new foo
            foo()
            super()
            foo()['b']
            foo().b
            foo()`abc`
        Left handside & right handeside
            left: a.b = c
                  a + b = c
            right: a++,a--,++a,--a
        Unary -- 单步运算符
            delete a.b
            void foo() -- void后面不管跟什么，值都是undefined,最好用void 0代替undefined,因为有时局部变量会被覆盖
            typeof(a) -- 判断数据类型的方法还有Object.prototype.toString.call,instanceof
            +a
            ~a -- 取反
            -a
            !a  -- !!可以用来做类型转换
            await a

            函数自执行 IIFE（立即执行的函数）
            有几种写法：
            (function(i){})(i);
            void function(i){}(i); -- 更优

        Logical: 
            &&
            ||
            短路逻辑： 
                foo1()&&foo2() -- foo1()为false时，foo2()将不执行
                foo1()||foo2() -- foo1为true时，foo2()将不执行
                true?foo1():foo2(); -- foo2()不执行
                false?foo1():foo2() -- foo1()不执行
        Equality: 
            ==
            !=
            ===
            !==
        Bitwise:
            & ^ |
        
    2、装箱和拆箱
        new String('hello')与'hello'--typeof的值不同，转换到别的类型的方法也不同
        ! new String('') -- false
        ! '' -- true

        String(1),Number(1),Boolean(1) -- 都不是Object，new之后会自动转换类型

        装箱:
            Object(1) -- 带不带new 结果都一样
            Symbol -- 不可以new,但有constructor,prototype
            Object(Symbol(1))
            (function(){return this}).apply(Symbol('x))
        拆箱：
            valueOf
            toString
            Symbol.toPrimitive -- 优先级最高


    3、statement -- 语句
        简单语句
            Expressionstatement -- 表达式语句
            Emptystatement -- 空语句
            DebugerStatement
            ThrowStatement
            ContinueStatement
            BreakStatement
            ReturnStatement
        复合语句
            BlockStatement --代码块
                const 
                throw
                let
            Iteration
                while
                do...while
                for()
                for(...in...) -- 循环一个变量的所有的属性
                for(...of...)
                    for(let p of [1,2,3]) {
                        console.log(p)
                    }
        声明
            FunctionDeclaration
            GeneratorDeclaraton
            AsyncFunctionDeclaration
            AsyncGenertorDeclaration
            VariableStatement
            ClassDeclaration
            LexicalDeclaration

        var 与function都可以提升变量，但是war只提升了变量，但是变量值为undefined,function会将函数内容也提升
        class没有变量提升，不能重复声明

    4、Object
        任何一个对象都是唯一的，这与它本身的状态无关。即便状态完全一致的两个对象，也并不相等。我们用状态来描述对象，我们状态的改变即是行为。
        对象三要素：唯一性idenifier,状态state,行为behavior
        
        Data Property: 
            value
            writeable -- 是否可写
            enumerable -- 是否可枚举
            configurable -- 是否能被改变
        Accessor property
            get
            set
            enumerable
            configurable

        object api
            {},[],Object.defineProperty  -- 基本aoi，最基础的面向对象的能力
            Object.create,Object,setPrototypeOf,Object.getPrototypeOf -- 原型api,与下面的第三类不要混用
            new,class,extend -- 基于类的面向对象


javascript中有哪些对象：
    本地对象-引用类型：Nubmer对象，String对象，Boolean对象，Array对象，Date对象，Object对象，Function对象，RegExp对象，Error对象
    内置对象：Global和Math
    宿主对象：BOM(Browser Object Model)浏览器对象模型和DOM
        window
            document(anchors,forms,images,links,location),frames.history,location,navigator,screen

有哪些对象是我们无法实现的？----不明白这个问题的意思



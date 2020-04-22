JS

1、Atom
2、Expression
3、Statement
4、Structure
5、Program/model

1、unicode--字符集
	包含128个ASCCII，超出128用codePointAt(0).toString(),<128的用String.fromChartCode()
	（1）block
			LINE FEED --回车
			SPACE -- 空格
			CJK -- 中文字符 china korea jepan

			js中可以用中文做变量名：  var 厉害 = 1;console.log(厉害);//输出1
								等同于： var \u5389\u5bb3 = 1;console.log(厉害);//输出1
	（2）categories -- separator space

2、inputElement --词法
	whitespace -- 空格
	LineTerminator -- 换行
	comment -- 注释
	Token -- 标记、记号、一切有效的

	（1）whitespace 
	    <TAB> -- CHARACTER TABULATION 制表符 '\t' '\u0009'
	    <VT> -- 纵向制表符 '\v' '\u0011'
	    <FF> -- '\u0010'
	    <SP> -- 普通空格 '\u0020'
	    <NBSP> -- &nbsp NO-BREAK SPACE '\U00A0'
	      Java &nbsp script 不把两个词分开，用于处理排版
	    <ZWNBSP> -- 零宽空格 zero width NO-BREAK SPACE '\UFEFF'
	    <USP>
	  (2) LineTerminator -- 换行符
	     <LF> -- '\U00A' '\n' 换行
	     <CR> -- '\U00D' '\r' carriage return 回车
	     <LS> -- 不建议使用，超出128
	     <PS> -- 不建议使用，超出128
	  (3) comment -- 多行、单行
	  (4) token
	    ideatifier  标识符 var a;其中的a
	    Punctuator  符号，不包括除号，因为容易与正则混淆 +,-,*...
	    Literal  直接量 1,true,false...
	    keywords 关键字  for,let...
		
		A.  结构： Puncturator,keywords
			内容： Identifier 包含变量名(不能与关键字重合)+属性(可以与关键字重合)
				   Literal
			例：get a(){}  //get不在关键字里，缺起到了关键字的作用
			   var get; //get还可以做变量
			   undefined //不是关键字，也不是标识符

			identifierName:
			    keywords
			    identifier
			    Future reserved keywords: ennm

		B.  Literal -- 7种数据类型
			Number
			String
			Boolean
			Null
			Undefined
			Object
			Symbol

			a. Number IEEE 754 Double Float 双精度浮点数
				十进制 -- DecimalLiteral
				八进制 --  BinaryIntegerLiteral Oo10
				二进制 -- OctalIntegerLiteral Ob
				十六进制 -- HexIntegerLiteral Ox

			 	safe integer
			 	float compare -- Math.abs(0.1+0.2-0.3) <= Number.EPSILON //比较浮点数
			b. String 
			   CHARACTER  词法
			   code point 码点
			   encoding

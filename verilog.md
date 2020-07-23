## 模块整体结构

```verilog
module module_name(portA,portB);
    //端口声明+参量声明
	#parameter pA=1'b0,pB=1'b1;
    input [7:0]portA;//八根线
    input sel;
    output portB;
    wire A,B,C;
    
    //模块声明（包含自定义模块）
	xor K1(A,B,C);
    and K2(A,B,C);
    or  K3(A,B,C);
    not K4(A,B);
    
    
endmodule
```

## 常用运算符

基本与C语言相同

```verilog
	?:		
    ^ | & ~
    || && !          
	+ - * / %
	<< >>
    == !=
	> <
```

## 语句块与赋值

begin end 类似于C语言大括号用法

```verilog
always @(*)
    begin
               
    end
//敏感信号列表
posedge A; negedge A;
```


***always 块中被赋值信号需要被声明为reg***



```verilog
assign x=y;
```



#### 阻塞赋值： =

一般为组合信号



#### 非阻塞赋值：<=

一般为时序信号



## 条件语句

```verilog
case(sel)
    0: xxxx;
    1: xxxx;
    default: xxxx;
endcase
```

```verilog
if(A==1) xxxxx;
else if(B==1) xxxxx;
else xxxxx;
```



## 其它

x表示不确定状态
z为高阻抗状态

---

----



## 不可综合语法（Testbench）

```verilog
`timescale 1ns/1ps
initial begin
    clk=0;
    #10 x=1;y=2;c=3;
end

initial repeat(20) #7 clk=~clk; //产生时钟信号
$stop $finish //结束仿真


$display      //显示结果
$monitor
$random
wait()		  
```


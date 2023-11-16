# 合约结构
```
undefined pragma solidity ^0.8.3;

contract Contract {
	// 变量
	unit public i;

	function fun() public {
	}
}
```
# data type(数据类型)
## primitive data type
### uint(uint8~uint256)
### int(int8~int256)
### bool
### address
## refrence data type


### string
### array
#### fixed-size array(固定长度数据)
```
uint[1] public arr = [1];
```
#### dynamic array(可变长度数组)
```
uint[] public arr = [1,2,3];
```
###  mapping
```
mapping(address => uint) _map;
uint i = _map[address]; 获取
_map[address] = i; 设置
delete _map[address]; 删除
```
### structs
```
struct _struct{
  uint i;
  string name;
  bool b;
}

// 三种初始化方法
_struct(1, "name", true);
_struct(i: 1, name: "name", b: true);
_struct memory st;
st.i = 1;
st.name = "name";
st.b = true;
```
### enum
```
enum Enum1 {
	name1, name2, ...
} 

// 实例化
Enum1 enum1 = Enum1.name1; 
```

# variable(可见性)
## global variables 内置变量
如 msg.sender

## state variables 合约内的变量
```
contract Contract1 {
	unit public i;
}
```
## local variables 方法内的变量 
```
contract Contract1 {
	function fun() public {
  	uint i = 1;
	}
}
```
#  function
## view & pure
view 只读不写 state variables
pure 不读不写 state variable

## function & modifiers & constructors

modifiers
```
modifier _modifier() {

}
```


function
```
function f() public view _modifier {

}
```


constructors
```
constructor() {

}
```
## multiple named outputs
```
function f() public pure _modifier returns(int,bool) {
return (1, true);
}
function f() public pure modifier returns(int x,bool _y) {
return (1, true);
}
function f() public view modifier returns(int x,bool _y) {
_x = 1;
_y = true;
} 
```
# visiblity
|  | current_contract   | child_contract   | other_contract |
| --- | --- | --- | --- |
| private               | ✅ | ❌ | ❌ |
| internal              | ✅ | ✅ | ❌ |
| public                 | ✅ | ✅ | ✅ |
| external              | ❌ | ❌ | ✅ |

 state variables can not be external 
# control flow(流程控制)
## if/else
```
if (true) { 

} else if (true) {

} else {

}
```
## for & while & do while
```
for(uint i = 0l i < 10; i++) {
if(true) continue;
if(true) break;
}
while(true) {}
do {} while (true)
```
# Data Locations(数据存储位置)
storage 链上
memory 执行期间的内存中
calldata 仅用于方法参数变量，变量不可变
memory -> memory 创建引用
storage -> storage 创建引用
storage -> memory|calldata 创建副本

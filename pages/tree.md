---
title: tree
---

## typescript
### typescript

### type

### interface

### 映射类型

- Partial<T>

	- 每个属性都可选
	- type Partial<T> = { [P in keyof T]?: T[P] };

- Required<T>

	- 每个属性都必选
	- type Required<T> = { [P in keyof T]-?: T[P] };

- Readonly<T>

	- 每个属性都只读
	- type Readonly<T> = {readonly [P in keyof T]: T[P];}

- ReadonlyArray＜T＞

	- T类型的只读数组

- Pick<T, k>

	- 从参数中选几个属性成为属性
	- type Pick<T, K extends keyof T> = { [P in K]: T[P] };

- Record<K, T>

	- 构造一个类型，其属性名的类型为K，属性值的类型为T
	- type Record<K extends keyof any, T> = {[P in K]: T;};

- Omit<T,K>

	- 创建一个省略某些特定属性的新对象
	- type Omit<T, K extends keyof any> = Pick<T, Exclude<keyof T, K>>;

### 条件类型

- Exclude<T, U>

	- 从类型T中剔除所有可以赋值给U的属性

- Extract<T, U>

	- 从类型T中提取所有可以赋值给U的类型

- NonNullable<T>

	- 从T中剔除null和undefined

- ReturnType<T>

	- 由函数类型T的返回值类型构造一个类型

- InstanceType<T>

	- 由构造函数类型T的实例类型构造一个类型

- ThisType<T>

	- 启用--noImplicitThis
	- 指定this的类型

### enum

- 紧跟在计算成员后的枚举成员必须有初始值
- 成员必须是常量，可以是计算属性

### extends

- A extends B ? X : Y

	- 若A能分配给B，返回X类型，否则返回Y类型
	- infer

		- type Parameters<T> = T extends (...args: infer R) => any ? R : any;
		- 可以在extends三元判断中，声明一个类型变量，以供后续使用。例子中的R就是一个类型变量，是...args的类型

	- 分配的意思是A是否是B的超集，即interface A extends B

- 泛型约束

	- function loggingIdentity<T extends Lengthwise>(arg: T): T {
    console.log(arg.length);  // Now we know it has a .length property, so no more error
    return arg;
}
	- 约束一个泛型的类型，表示泛型实现了某个类型

### keyof

- 取一个接口所有key作为一个字符串联合类型
- keyof A === 'a' | 'b' | 'c'

### 类型保护

- 类型断言

	- as

		- (pet as Bird).fly()

	- 泛型

		- (<Bird>pet).fly()

- in

	- type Readonly<T> = {
    readonly [P in keyof T]: T[P];
}
	- 用来断言属于联合类型中的某一个
	- 用来判断属性是否存在某对象中

- instanceof

	- pet instanceof Bird

- typeof

	- typeof pet === 'number'
	- 返回后面的表达式的类型

- is

	- function isType(type: any): type is GraphQLType;
	- 用来断言参数类型

### interface和type的区别

- https://juejin.im/post/5c2723635188252d1d34dc7d
- type可以interface不行

	- type 可以声明基本类型别名，联合类型，元组等类型
	- type 语句中还可以使用 typeof 获取实例的 类型进行赋值
	- 索引签名可以使用联合类型

- interface 可以而 type 不行

	- interface 能够声明合并

### decorator

### 函数重载

- 根据不同的参数类型返回不同类型的值
- 为同一个函数提供多个函数类型定义来进行函数重载

### this

- 通常this会被ts识别为any，可以在函数参数中声明一个this参数，为他指定类型。这个参数是个加参数，它出现在参数列表最前面
- let deck: Deck = {
    suits: ["hearts", "spades", "clubs", "diamonds"],
    cards: Array(52),
    // NOTE: The function now explicitly specifies that its callee must be of type Deck
    createCardPicker: function(this: Deck) {
        return () => {
            let pickedCard = Math.floor(Math.random() * 52);
            let pickedSuit = Math.floor(pickedCard / 13);

            return {suit: this.suits[pickedSuit], card: pickedCard % 13};
        }
    }
}

### 非空断言

- const a = b!
- 断言b不可能是undefined或null

### ??操作符

- a ?? b 等同于a ? a : b
### <
## #+BEGIN_NOTE
112233
## #+END_NOTE

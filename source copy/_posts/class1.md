---
title: 第一节课讲义：认识 C++ 输入输出与基本变量类型
date: 2025-04-25 18:40:44
categories: 教学
---

# 第一节课讲义：认识 C++ 输入输出与基本变量类型

---

## 课程目标
1. **掌握 `cin` 和 `cout` 的基本用法**
2. **理解 `int`、`float`、`char` 三种变量的用途**
3. **能编写简单的输入输出程序**

---

## 一、C++ 程序的基本结构

### 1.1 代码框架
所有 C++ 程序都从 `main` 函数开始执行：
```cpp
#include <iostream>  // 引入输入输出库
using namespace std; // 使用标准命名空间

int main() {         // 程序入口
    // 你的代码写在这里
    return 0;        // 程序结束
}
```
- **`#include <iostream>`**：提供 `cin` 和 `cout` 功能。
- **`using namespace std;`**：避免重复写 `std::cout`，直接使用 `cout`。

---

## 二、输出内容：`cout` 的用法

### 2.1 输出文本与变量
- **语法**：`cout << 内容1 << 内容2 << endl;`
- **示例**：输出 "Hello, World!"
```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, World!" << endl;  // endl 表示换行
    return 0;
}
```
- **练习**：输出你的名字
```cpp
cout << "我的名字是：小蓝" << endl;  // 将 "小蓝" 改为你的名字
```

### 2.2 输出多个内容
```cpp
int age = 10;
cout << "我今年" << age << "岁！" << endl;
// 输出结果：我今年10岁！
```

---

## 三、输入内容：`cin` 的用法

### 3.1 基本输入操作
- **语法**：`cin >> 变量;`
- **示例**：输入年龄并输出
```cpp
#include <iostream>
using namespace std;

int main() {
    int age;                      // 声明变量
    cout << "请输入年龄：";       // 提示用户输入
    cin >> age;                   // 读取输入
    cout << "你的年龄是：" << age << "岁！" << endl;
    return 0;
}
```

### 3.2 输入不同类型的数据
```cpp
float height;
char initial;

cout << "输入身高（米）：";
cin >> height;                   // 输入小数，如 1.75

cout << "输入姓名首字母：";
cin >> initial;                  // 输入单个字符，如 'A'
```

---

## 四、变量的基本类型

### 4.1 变量的作用
- **存储数据**：像盒子一样保存程序中需要的数据（如数字、文字）。

### 4.2 常用变量类型
| 类型      | 用途           | 示例             | 注意事项                  |
|-----------|----------------|------------------|--------------------------|
| `int`     | 存储整数       | `int age = 15;`  | 不能存储小数             |
| `float`   | 存储小数       | `float pi = 3.14;` | 精度较低，适合一般计算   |
| `char`    | 存储单个字符   | `char grade = 'A';` | 必须用单引号 `' '`       |


### 4.3 变量的声明与赋值
```cpp
int score;        // 声明一个整数变量
score = 90;       // 赋值

float price = 19.99;  // 声明并初始化
char symbol = '$'; 
```

---

## 五、综合练习

### 5.1 任务：输入个人信息并输出
```cpp
#include <iostream>
#include <string>   // 必须包含此头文件才能使用 string
using namespace std;

int main()
{
    int age;
    float height;

    cout << "请输入你的年龄：";
    cin >> age;

    cout << "请输入你的身高（米）：";
    cin >> height;

    cout << endl << "===== 个人信息 =====" << endl;
    cout << "年龄：" << age << "岁" << endl;
    cout << "身高：" << height << "米" << endl;

    return 0;
}
```

---

## 六、常见错误与注意事项

1. **未包含头文件**  
   - 错误：`cout was not declared`
   - 解决：添加 `#include <iostream>` 和 `using namespace std;`

2. **变量未声明直接使用**  
   - 错误：`age was not declared`
   - 解决：使用变量前必须先声明，如 `int age;`

3. **错误使用引号**  
   - 错误：`char c = "A";`（双引号）
   - 正确：`char c = 'A';`（单引号）

---

## 课后任务

### 必做题：B3648 你几岁了
**要求**：输入年龄 `x`，输出 `I am x years old.`。

**输入样例**：
```
3
```

**输出样例**：
```
I am 3 years old.
```

---

### 选做题：B2025 输出字符菱形
**要求**：用 `*` 输出一个对角线长为 5 的菱形。

**输出样例**：
```
  *
 ***
*****
 ***
  *
```

**提示**：使用多个 `cout` 控制空格和 `*` 的数量。

---

**下节课预告**：学习运算符（加减乘除）和条件语句（if）！
---
title: 数组 array
date: 2025-02-18
categories: 数据结构
top_img: /img/top/6.png
---

# 数组 array



## 数组的特点：

1.  **固定大小**：数组在创建时必须指定大小，一旦定义，大小不能更改。这意味着，如果需要存储更多的数据，必须创建一个新的数组并复制数据。
2.  **元素类型相同**：数组中的所有元素必须是相同类型的数据（如整数、字符、浮点数等）。
3.  **按索引访问**：数组的每个元素都有一个唯一的索引，索引从0开始，允许直接访问任何元素。
4.  **连续内存**：数组的元素在内存中是连续存储的，这使得数组具有较快的访问速度。

## 数组的缺点：

1.  **固定大小**：数组一旦创建，其大小是固定的，无法动态扩展。如果数据量超出了原先设定的大小，必须重新分配更大的数组并复制数据，效率较低。
2.  **浪费内存**：如果你事先定义的数组大小过大，可能会浪费内存空间；如果大小过小，可能会导致无法存储所有数据。
3.  **插入和删除效率低**：数组中的元素是连续存储的，因此在数组中间插入或删除元素时，需要移动大量的数据，效率较低。

## 示例（C++）：

```c++
#include <iostream>
using namespace std;

int main() 
{
    // 声明并初始化一个包含5个整数的数组
    int arr[5] = {1, 2, 3, 4, 5};  

    // 访问数组元素
    cout << "数组的第一个元素: " << arr[0] << endl;  // 输出 1

    // 修改数组元素
    arr[2] = 10;  // 将数组中第三个元素修改为 10

    // 输出修改后的数组元素
    cout << "修改后的第三个元素: " << arr[2] << endl;  // 输出 10

    return 0;
}
```

### 数组的操作：

1.  **访问元素**：通过索引访问数组中的元素。例如，`arr[3]` 访问数组 `arr` 的第四个元素（索引从0开始）。
2.  **修改元素**：通过指定索引修改数组中的元素。例如，`arr[1] = 20` 将数组中第二个元素的值改为20。
3.  **遍历数组**：通过循环遍历数组中的每个元素。例如，使用 `for` 循环来访问所有元素。

```c++
for (int i = 0; i < 5; i++) 
{
    cout << arr[i] << " ";
}
```

4.  **数组初始化**：在声明时，你可以通过花括号 `{}` 初始化数组，或者使用循环动态赋值。

### 数组的应用：

1.  **存储一组相同类型的数据**：最常见的应用是存储同类型的数据集合，例如学生的成绩、多个传感器的测量值等。
    * 例：存储班级学生的数学成绩。

```c++
int scores[30];  // 存储30个学生的成绩
```

2.  **实现栈和队列**：通过数组可以实现栈（后进先出）和队列（先进先出）的数据结构。
    * 例：使用数组来实现一个队列：

```c++
int queue[100];
int front = -1, rear = -1;
```

3.  **数据处理和分析**：在数据科学和计算机科学中，数组广泛用于存储和处理数据。
    * 例：用数组存储每日气温数据，进行温度变化分析。
4.  **排序和查找**：数组是许多经典排序和查找算法（如冒泡排序、二分查找）的基础数据结构。
    * 例：使用数组进行排序：

```c++
for (int i = 0; i < 5; i++) 
{
    for (int j = 0; j < 5 - i - 1; j++) 
    {
        if (arr[j] > arr[j + 1]) 
        {
            swap(arr[j], arr[j + 1]);
        }
    }
}
```

5.  **图像处理**：在图像处理中，像素值通常以二维数组的形式存储，用于表示图像中的颜色和亮度。
    * 例：一个图像的RGB像素值可以用二维数组表示。

```c++
int image[100][100][3];  // 100x100像素的图像，每个像素有RGB三个值
```

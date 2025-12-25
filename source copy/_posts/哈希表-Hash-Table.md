---
title: 哈希表 Hash Table
date: 2025-02-18
categories: 数据结构
top_img: /img/top/12.png
---

# 哈希表 Hash Table

哈希表（Hash Table）是一种用于存储键值对（key-value pairs）的数据结构，它可以实现非常高效的查找、插入和删除操作。哈希表通过哈希函数将键映射到哈希表的索引位置，从而能在常数时间 O(1) 内完成查找、插入和删除操作。

## 哈希表的基本原理

1.  **哈希函数**：哈希表通过哈希函数将键（key）映射到哈希表中的一个特定位置（即索引）。哈希函数的目标是尽可能将不同的键映射到不同的索引，以减少冲突。
    * 哈希函数的一种常见实现方法是：`hash(key) = key % table_size`，这里的 `table_size` 是哈希表的大小。
2.  **冲突（Collision）**：不同的键可能通过哈希函数计算后得到相同的哈希值，从而映射到同一个位置，这时就发生了冲突。解决冲突的常见方法有：
    * **链式地址法（Separate Chaining）**：每个哈希表的槽位（bucket）存储一个链表，冲突的元素存储在同一个链表中。
    * **开放定址法（Open Addressing）**：当发生冲突时，哈希表会尝试在表中寻找其他空位，直到找到一个空槽。
3.  **负载因子（Load Factor）**：负载因子是哈希表中的元素数量与哈希表大小的比值，用来衡量哈希表的填充程度。负载因子过高可能导致哈希冲突增多，从而降低性能。通常当负载因子超过某个阈值时，会对哈希表进行扩容（rehash）。
4.  **扩容与再哈希（Rehashing）**：当哈希表的负载因子超过设定的阈值时，可以通过增加哈希表的大小并重新计算每个元素的哈希值来减少冲突，从而提高查找效率。

## 哈希表的基本操作

1.  **插入（Insert）**：
    * 使用哈希函数计算键的哈希值，并将其映射到对应的槽位。
    * 如果槽位已被占用，则根据解决冲突的方法（链式或开放定址法）处理冲突。
2.  **查找（Search）**：
    * 使用哈希函数计算键的哈希值，然后检查该槽位是否存在对应的值。如果有冲突，则需要继续检查链表或其他空槽。
3.  **删除（Delete）**：
    * 使用哈希函数找到元素的位置，并删除它。如果存在冲突（如链式法），需要相应地删除链表中的元素。
4.  **扩容（Rehashing）**：
    * 当哈希表的负载因子过高时，哈希表的大小需要扩大，通常是扩展为原来大小的两倍，然后重新计算每个元素的哈希值并重新插入。

## 哈希表的优缺点

#### 优点：

* **快速查找**：在理想情况下，哈希表的查找、插入和删除操作的时间复杂度是 O(1)，即常数时间操作。
* **高效存储**：由于哈希表通过哈希函数直接映射到槽位，因此可以在大规模数据存储时提供高效的访问。

#### 缺点：

* **哈希冲突**：当多个键映射到同一个位置时，会发生哈希冲突。虽然可以通过链式或开放定址法解决冲突，但会影响操作效率。
* **不适合排序**：哈希表中的元素没有顺序，不能直接支持按键排序。
* **空间开销**：哈希表为了避免过多冲突，通常需要比实际存储元素更多的空间。这可能导致内存浪费。

## 哈希表的应用

1.  **快速查找**：哈希表用于实现快速查找功能，广泛应用于数据库索引、缓存系统等。
2.  **去重**：通过将元素作为键存储，哈希表可以方便地去除重复元素。例如，在处理大数据时，通过哈希表去除重复记录。
3.  **计数统计**：哈希表可以用于统计每个元素出现的次数，广泛应用于词频统计、数据分析等。
4.  **实现集合操作**：哈希表常常用于实现集合（set）的操作，如交集、并集、差集等。

## 哈希表的示例实现（C++）

```c++
#include <iostream>
#include <list>
#include <vector>
using namespace std;

class HashTable {
private:
    vector<list<int>> table;  // 哈希表的桶（使用链表处理冲突）
    int size;  // 哈希表的大小
    
    int hashFunction(int key) {
        return key % size;  // 哈希函数（取模）
    }
    
public:
    HashTable(int s) {
        size = s;
        table.resize(s);  // 初始化哈希表
    }
    
    // 插入操作
    void insert(int key) {
        int index = hashFunction(key);  // 计算哈希值
        table[index].push_back(key);  // 在对应的槽位插入键
    }
    
    // 查找操作
    bool search(int key) {
        int index = hashFunction(key);
        for (int element : table[index]) {
            if (element == key) {
                return true;  // 找到元素
            }
        }
        return false;  // 未找到元素
    }
    
    // 删除操作
    void remove(int key) {
        int index = hashFunction(key);
        table[index].remove(key);  // 从链表中删除元素
    }
    
    // 打印哈希表
    void display() {
        for (int i = 0; i < size; i++) {
            cout << "Bucket " << i << ": ";
            for (int element : table[i]) {
                cout << element << " ";
            }
            cout << endl;
        }
    }
};

int main() {
    HashTable ht(7);  // 创建一个大小为7的哈希表
    
    ht.insert(10);
    ht.insert(20);
    ht.insert(15);
    ht.insert(7);
    ht.insert(30);
    
    ht.display();  // 显示哈希表
    
    cout << "Search 15: " << (ht.search(15) ? "Found" : "Not Found") << endl;
    cout << "Search 25: " << (ht.search(25) ? "Found" : "Not Found") << endl;
    
    ht.remove(15);
    cout << "After deleting 15:" << endl;
    ht.display();  // 删除元素后显示哈希表
    
    return 0;
}
```

## 代码解析

1.  **HashTable 类**：包含了哈希表的基本操作，如插入、查找、删除和显示哈希表。
2.  **insert()**：通过哈希函数计算插入元素的槽位，然后将元素插入到该槽位的链表中。
3.  **search()**：通过哈希函数找到槽位后，遍历链表检查是否有该元素。
4.  **remove()**：通过哈希函数找到槽位，并从该槽位的链表中删除元素。
5.  **display()**：显示哈希表的所有槽位及其存储的元素。

## 总结

哈希表是一种高效的键值对存储数据结构，能够提供常数时间复杂度的查找、插入和删除操作。它广泛应用于需要高效查找、去重和计数的场景。虽然哈希表在实际应用中需要解决哈希冲突问题，但通过合适的冲突解决方法，可以保证其高效性。

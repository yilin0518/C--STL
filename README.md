# C-STL
C++ STL summary

内容来自网络博客，链接如下：

* (vector)https://blog.csdn.net/Flag_ing/article/details/123380655
*  [C语言中文网](https://c.biancheng.net/)
## Vector

### Vector对象的定义和初始化方式

#### 常用的初始化方式及作用如下：

| 形式 | 功能 |
| ---- | ---- |
| vector<T> v1      	       | v1 是一个元素类型为 T 的空 vector |
| vector<T> v2(v1)          |	使用 v2 中所有元素初始化 v1 |
| vector<T> v2 = v1	       | 同上 |
| vector<T> v3(n, val)	v3   | 中包含了 n 个值为 val 的元素 |
| vector<T> v4(n)	         | v4 中包含了 n 个默认值初始化的元素 |
| vector<T> v5{a, b, c...}  | 使用 a, b, c... 初始化 v5 |
| vector<T> v1	                               | 同上                  |
| vector<vector<int>> matrix(M,vector<int>(N)); |  二维数组初始化 |

### 常用基础操作

| 形式 | 功能 |
| --- | --- |
|v.empty()|	如果 v 为空则返回 true，否则返回 false|
|v.size()	|返回 v 中元素的个数|
|v.push_back(val)	|向 vector 的尾端添加值为 val 的元素。 注意：vector 不支持 push_front 操作。|
|v.pop_back(val)	|删除尾元素，返回void。vector同样 不支持 pop_front 操作。若想在同时弹出元素的值，就必须在执行弹出之前保存它（可以使用 v.back()）。|
|v[n]	|返回 v 中第 n 个位置上元素的引用，不能用下标操作添加元素|
|v.back()|	返回 v 中最后一个元素的引用|
|v.front()	|返回 v 中第一个元素的引用|
|v1 = v2|	用 v2 中的元素替换 v1 中的元素|
|v1 = {a, b, c...}|	用元素 {a, b, c...} 替换 v1 中的元素|
|v1 == v2	|当且仅当拥有相同数量且相同位置上值相同的元素时，v1 与 v2 相等|
|v1 != v2	|自行体会|
|<, <=, >, >=	|以字典序进行比较|
|v.insert(p, n, val)|在迭代器 p 之前插入 n 个值为 val 的元素，返回新添加的第一个元素的迭代器。|
|v.erase(p)|删除迭代器 p 所指的元素，返回指向被删除元素之后元素的迭代器。|
|v.erase(b, e) |删除迭代器 b, e 之间的元素，返回指向最后一个被删除元素之后元素的迭代器。|

### vector 元素的重排操作（排序、逆序等）

容器的重排需要用到头文件 <algorithm> 中的算法

1. 排序 sort()

按输入序列的字典序升序排序，原位操作，无返回值

函数原型：

void std::sort<std::vector<int>::iterator>(std::vector<int>::iterator, std::vector<int>::iterator)

2. 消除相邻的重复元素 unique()

将输入序列相邻的重复项“消除”，返回一个指向不重复值范围末尾的迭代器，一般配合 sort() 使用，函数原型：

std::vector<int>::iterator std::unique<std::vector<int>::iterator>(std::vector<int>::iterator, std::vector<int>::iterator)

3. 逆序 reverse()

将输入序列按照下标逆序排列，原位操作，无返回值函数原型：

void std::reverse<std::vector<int>::iterator>(std::vector<int>::iterator, std::vector<int>::iterator)

### vector 中找最值

容器的重排同样需要用到头文件 <algorithm> 中的算法。

1. 最大值 auto it = max_element(v.begin, v,end())，返回最大值的迭代器，函数原型如下：

constexpr std::vector<int>::iterator std::max_element<std::vector<int>::iterator>(std::vector<int>::iterator, std::vector<int>::iterator)

2. 最小值 auto it = min_element(v.begin, v,end())，返回最小值的迭代器，函数原型如下：

constexpr std::vector<int>::iterator std::min_element<std::vector<int>::iterator>(std::vector<int>::iterator, std::vector<int>::iterator)

3. 相对位置大小 auto b = distance(x, y)，x、y 是迭代器类型，返回 x、y 之间的距离，可以用来获取最大/小值的索引，函数原型如下：

std::ptrdiff_t std::distance<std::vector<int>::iterator>(std::vector<int>::iterator __first, std::vector<int>::iterator __last)


## unordered_map

### 创建C++ unordered_map容器的方法

1. std::unordered_map<std::string, std::string> umap;

2. 在创建 unordered_map 容器的同时，可以完成初始化操作。比如：

std::unordered_map<std::string, std::string> umap{
    {"Python教程","http://c.biancheng.net/python/"},
    {"Java教程","http://c.biancheng.net/java/"},
    {"Linux教程","http://c.biancheng.net/linux/"} };

3. std::unordered_map<std::string, std::string> umap2(umap);

### C++ unordered_map容器的成员方法

|成员方法	|功能|
|---|---|
|begin()	|返回指向容器中第一个键值对的正向迭代器。|
|end() 	|返回指向容器中最后一个键值对之后位置的正向迭代器。|
|cbegin()|	和 begin() 功能相同，只不过在其基础上增加了 const 属性，即该方法返回的迭代器不能用于修改容器内存储的键值对。|
|cend()	|和 end() 功能相同，只不过在其基础上，增加了 const 属性，即该方法返回的迭代器不能用于修改容器内存储的键值对。|
|empty()	|若容器为空，则返回 true；否则 false。|
|size()|	返回当前容器中存有键值对的个数。|
|max_size()|	返回容器所能容纳键值对的最大个数，不同的操作系统，其返回值亦不相同。|
|operator[key]	|该模板类中重载了 [] 运算符，其功能是可以向访问数组中元素那样，只要给定某个键值对的键 key，就可以获取该键对应的值。注意，如果当前容器中没有以 key 为键的键值对，则其会使用该键向当前容器中插入一个新键值对。|
|at(key)	|返回容器中存储的键 key 对应的值，如果 key 不存在，则会抛出 out_of_range 异常。 |
|find(key)	|查找以 key 为键的键值对，如果找到，则返回一个指向该键值对的正向迭代器；反之，则返回一个指向容器中最后一个键值对之后位置的迭代器（如果 end() 方法返回的迭代器）。|
|count(key)|	在容器中查找以 key 键的键值对的个数。|
|equal_range(key)	|返回一个 pair 对象，其包含 2 个迭代器，用于表明当前容器中键为 key 的键值对所在的范围。|
|emplace()	|向容器中添加新键值对，效率比 insert() 方法高。|
|emplace_hint()	|向容器中添加新键值对，效率比 insert() 方法高。|
|insert() |	向容器中添加新键值对。|
|erase()|	删除指定键值对。|
|clear() 	|清空容器，即删除容器中存储的所有键值对。|
|swap()	|交换 2 个 unordered_map 容器存储的键值对，前提是必须保证这 2 个容器的类型完全相等。|
|bucket_count()	|返回当前容器底层存储键值对时，使用桶（一个线性链表代表一个桶）的数量。|
|max_bucket_count()|	返回当前系统中，unordered_map 容器底层最多可以使用多少桶。|
|bucket_size(n)	|返回第 n 个桶中存储键值对的数量。|
|bucket(key)|	返回以 key 为键的键值对所在桶的编号。|
|load_factor()	|返回 unordered_map 容器中当前的负载因子。负载因子，指的是的当前容器中存储键值对的数量（size()）和使用桶数（bucket_count()）的比值，即 load_factor() = size() / bucket_count()。|
|max_load_factor()	|返回或者设置当前 unordered_map 容器的负载因子。|
|rehash(n)|	将当前容器底层使用桶的数量设置为 n。|
|reserve()	|将存储桶的数量（也就是 bucket_count() 方法的返回值）设置为至少容纳count个元（不超过最大负载因子）所需的数量，并重新整理容器。|
|hash_function()|	返回当前容器使用的哈希函数对象。|

## unordered_set容器

### 创建C++ unordered_set容器

1. std::unordered_set<std::string> uset;
2. 在创建 unordered_set 容器的同时，可以完成初始化操作。
 std::unordered_set<std::string> uset{ "http://c.biancheng.net/c/",
                                      "http://c.biancheng.net/java/",
                                      "http://c.biancheng.net/linux/" };
3. 调用 unordered_set 模板中提供的复制（拷贝）构造函数，将现有 unordered_set 容器中存储的元素全部用于为新建 unordered_set 容器初始化。
std::unordered_set<std::string> uset2(uset);

### C++ unordered_set容器的成员方法

| 成员方法          | 功能                                                                                   |
|----------------|--------------------------------------------------------------------------------------|
| begin()        | 返回指向容器中第一个元素的正向迭代器。                                                     |
| end();         | 返回指向容器中最后一个元素之后位置的正向迭代器。                                               |
| cbegin()       | 和 begin() 功能相同，只不过其返回的是 const 类型的正向迭代器。                                   |
| cend()         | 和 end() 功能相同，只不过其返回的是 const 类型的正向迭代器。                                    |
| empty()        | 若容器为空，则返回 true；否则 false。                                                     |
| size()         | 返回当前容器中存有元素的个数。                                                              |
| max_size()     | 返回容器所能容纳元素的最大个数，不同的操作系统，其返回值亦不相同。                                |
| find(key)      | 查找以值为 key 的元素，如果找到，则返回一个指向该元素的正向迭代器；反之，则返回一个指向容器中最后一个元素之后位置的迭代器（如果 end() 方法返回的迭代器）。 |
| count(key)     | 在容器中查找值为 key 的元素的个数。                                                          |
| equal_range(key) | 返回一个 pair 对象，其包含 2 个迭代器，用于表明当前容器中值为 key 的元素所在的范围。                               |
| emplace()      | 向容器中添加新元素，效率比 insert() 方法高。                                                  |
| emplace_hint() | 向容器中添加新元素，效率比 insert() 方法高。                                                  |
| insert()       | 向容器中添加新元素。                                                                    |
| erase()        | 删除指定元素。                                                                         |
| clear()        | 清空容器，即删除容器中存储的所有元素。                                                        |
| swap()         | 交换 2 个 unordered_set 容器存储的元素，前提是必须保证这 2 个容器的类型完全相等。                                   |
| bucket_count() | 返回当前容器底层存储元素时，使用桶（一个线性链表代表一个桶）的数量。                                              |
| max_bucket_count() | 返回当前系统中，unordered_set 容器底层最多可以使用多少桶。                                      |
| bucket_size(n) | 返回第 n 个桶中存储元素的数量。                                                              |
| bucket(key)    | 返回值为 key 的元素所在桶的编号。                                                            |
| load_factor()  | 返回 unordered_set 容器中当前的负载因子。负载因子，指的是的当前容器中存储元素的数量（size()）和使用桶数（bucket_count()）的比值，即 load_factor() = size() / bucket_count()。 |
| max_load_factor() | 返回或者设置当前 unordered_set 容器的负载因子。                                                  |
| rehash(n)      | 将当前容器底层使用桶的数量设置为 n。                                                         |
| reserve()      | 将存储桶的数量（也就是 bucket_count() 方法的返回值）设置为至少容纳 count 个元（不超过最大负载因子）所需的数量，并重新整理容器。                        |
| hash_function() | 返回当前容器使用的哈希函数对象。                                                              |

## deque

### 使用方式

#include <deque>

using namespace std;

### 创建deque容器的几种方式

1. 创建一个没有任何元素的空 deque 容器：    std::deque<int> d;
2. 创建一个具有 n 个元素的 deque 容器，其中每个元素都采用对应类型的默认值：    std::deque<int> d(10);
3. 创建一个具有 n 个元素的 deque 容器，并为每个元素都指定初始值，例如：std::deque<int> d(10, 5)
4. 在已有 deque 容器的情况下，可以通过拷贝该容器创建一个新的 deque 容器，例如：    std::deque<int> d1(5);    std::deque<int> d2(d1);
5. 过拷贝其他类型容器中指定区域内的元素（也可以是普通数组），可以创建一个新容器，例如： std::deque<int>d(a, a + 5); //a为数组指针 std::deque<int>d(arr.begin()+2, arr.end()); //拷贝arr容器中的{13,14,15}

### deque容器可利用的成员函数

| 函数成员          | 函数功能                                                                                     |
|----------------|------------------------------------------------------------------------------------------|
| begin()        | 返回指向容器中第一个元素的迭代器。                                                                  |
| end()          | 返回指向容器最后一个元素所在位置后一个位置的迭代器，通常和 begin() 结合使用。                             |
| rbegin()       | 返回指向最后一个元素的迭代器。                                                                     |
| rend()         | 返回指向第一个元素所在位置前一个位置的迭代器。                                                          |
| cbegin()       | 和 begin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。                                 |
| cend()         | 和 end() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。                                  |
| crbegin()      | 和 rbegin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。                                |
| crend()        | 和 rend() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。                                 |
| size()         | 返回实际元素个数。                                                                               |
| max_size()     | 返回容器所能容纳元素个数的最大值。这通常是一个很大的值，一般是 2^32-1，我们很少会用到这个函数。                     |
| resize()       | 改变实际元素的个数。                                                                              |
| empty()        | 判断容器中是否有元素，若无元素，则返回 true；反之，返回 false。                                      |
| shrink_to_fit() | 将内存减少到等于当前元素实际所使用的大小。                                                             |
| at()           | 使用经过边界检查的索引访问元素。                                                                    |
| front()        | 返回第一个元素的引用。                                                                            |
| back()         | 返回最后一个元素的引用。                                                                           |
| assign()       | 用新元素替换原有内容。                                                                            |
| push_back()    | 在序列的尾部添加一个元素。                                                                         |
| push_front()   | 在序列的头部添加一个元素。                                                                         |
| pop_back()     | 移除容器尾部的元素。                                                                              |
| pop_front()    | 移除容器头部的元素。                                                                              |
| insert()       | 在指定的位置插入一个或多个元素。                                                                     |
| erase()        | 移除一个元素或一段元素。                                                                           |
| clear()        | 移出所有的元素，容器大小变为 0。                                                                    |
| swap()         | 交换两个容器的所有元素。                                                                           |
| emplace()      | 在指定的位置直接生成一个元素。                                                                       |
| emplace_front()| 在容器头部生成一个元素。和 push_front() 的区别是，该函数直接在容器头部构造元素，省去了复制移动元素的过程。                |
| emplace_back() | 在容器尾部生成一个元素。和 push_back() 的区别是，该函数直接在容器尾部构造元素，省去了复制移动元素的过程。                |

## List

### 使用方式

#include <list>

using namespace std;

### list容器的创建

1. 创建一个没有任何元素的空 list 容器： std::list<int> values;
2. 创建一个包含 n 个元素的 list 容器:  std::list<int> values(10);
3. 创建一个包含 n 个元素的 list 容器，并为每个元素指定初始值。例如： std::list<int> values(10, 5);
4. 在已有 list 容器的情况下，通过拷贝该容器可以创建新的 list 容器。
5. 通过拷贝其他类型容器（或者普通数组）中指定区域内的元素，可以创建新的 list 容器。

### list容器可用的成员函数

| 成员函数          | 功能                                                                                        |
|----------------|------------------------------------------------------------------------------------------|
| begin()        | 返回指向容器中第一个元素的双向迭代器。                                                                  |
| end()          | 返回指向容器中最后一个元素所在位置的下一个位置的双向迭代器。                                                 |
| rbegin()       | 返回指向最后一个元素的反向双向迭代器。                                                                 |
| rend()         | 返回指向第一个元素所在位置前一个位置的反向双向迭代器。                                                      |
| cbegin()       | 和 begin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。                                     |
| cend()         | 和 end() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。                                      |
| crbegin()      | 和 rbegin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。                                    |
| crend()        | 和 rend() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。                                     |
| empty()        | 判断容器中是否有元素，若无元素，则返回 true；反之，返回 false。                                          |
| size()         | 返回当前容器实际包含的元素个数。                                                                     |
| max_size()     | 返回容器所能包含元素个数的最大值。这通常是一个很大的值，一般是 2^32-1，所以我们很少会用到这个函数。                       |
| front()        | 返回第一个元素的引用。                                                                             |
| back()         | 返回最后一个元素的引用。                                                                            |
| assign()       | 用新元素替换容器中原有内容。                                                                        |
| emplace_front()| 在容器头部生成一个元素。该函数和 push_front() 的功能相同，但效率更高。                                       |
| push_front()   | 在容器头部插入一个元素。                                                                           |
| pop_front()    | 删除容器头部的一个元素。                                                                           |
| emplace_back() | 在容器尾部直接生成一个元素。该函数和 push_back() 的功能相同，但效率更高。                                       |
| push_back()    | 在容器尾部插入一个元素。                                                                           |
| pop_back()     | 删除容器尾部的一个元素。                                                                           |
| emplace()      | 在容器中的指定位置插入元素。该函数和 insert() 功能相同，但效率更高。                                            |
| insert()       | 在容器中的指定位置插入元素。                                                                        |
| erase()        | 删除容器中一个或某区域内的元素。                                                                     |
| swap()         | 交换两个容器中的元素，必须保证这两个容器中存储的元素类型是相同的。                                            |
| resize()       | 调整容器的大小。                                                                                |
| clear()        | 删除容器存储的所有元素。                                                                           |
| splice()       | 将一个 list 容器中的元素插入到另一个容器的指定位置。                                                       |
| remove(val)    | 删除容器中所有等于 val 的元素。                                                                      |
| remove_if()    | 删除容器中满足条件的元素。                                                                         |
| unique()       | 删除容器中相邻的重复元素，只保留一个。                                                                |
| merge()        | 合并两个事先已排好序的 list 容器，并且合并之后的 list 容器依然是有序的。                                       |
| sort()         | 通过更改容器中元素的位置，将它们进行排序。                                                             |
| reverse()      | 反转容器中元素的顺序。                                                                            |

## map

### 使用方法

#include <map>

using namespace std;

默认情况下，map 容器选用std::less<T>排序规则（其中 T 表示键的数据类型），其会根据键的大小对所有键值对做升序排序。当然，根据实际情况的需要，我们可以手动指定 map 容器的排序规则，既可以选用 STL 标准库中提供的其它排序规则（比如std::greater<T>），也可以自定义排序规则。

### 创建C++ map容器的几种方法

1. std::map<std::string, int>myMap;
2. 初始化：std::map<std::string, int>myMap{ {"C语言教程",10},{"STL教程",20} };
3. 初始化：std::map<std::string, int>myMap{std::make_pair("C语言教程",10),std::make_pair("STL教程",20)};
4. std::map<std::string, int>newMap(myMap);
5. std::map<std::string, int>newMap(++myMap.begin(), myMap.end());

### C++ map容器包含的成员方法

| 成员方法           | 功能                                                                                         |
|-------------------|--------------------------------------------------------------------------------------------|
| begin()           | 返回指向容器中第一个（已排好序的第一个）键值对的双向迭代器。如果是 const map，则返回 const 双向迭代器。                                  |
| end()             | 返回指向容器最后一个元素（已排好序的最后一个）所在位置后一个位置的双向迭代器。通常和 begin() 结合使用。如果是 const map，则返回 const 双向迭代器。                    |
| rbegin()          | 返回指向最后一个（已排好序的最后一个）元素的反向双向迭代器。如果是 const map，则返回 const 反向双向迭代器。                               |
| rend()            | 返回指向第一个（已排好序的第一个）元素所在位置前一个位置的反向双向迭代器。如果是 const map，则返回 const 反向双向迭代器。                        |
| cbegin()          | 和 begin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改容器内存储的键值对。                                                      |
| cend()            | 和 end() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改容器内存储的键值对。                                                       |
| crbegin()         | 和 rbegin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改容器内存储的键值对。                                                      |
| crend()           | 和 rend() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改容器内存储的键值对。                                                       |
| find(key)         | 在 map 容器中查找键为 key 的键值对，如果成功找到，则返回指向该键值对的双向迭代器；反之，则返回和 end() 方法一样的迭代器。如果是 const map，则返回 const 双向迭代器。 |
| lower_bound(key)  | 返回一个指向当前 map 容器中第一个大于或等于 key 的键值对的双向迭代器。如果是 const map，则返回 const 双向迭代器。                                 |
| upper_bound(key)  | 返回一个指向当前 map 容器中第一个大于 key 的键值对的迭代器。如果是 const map，则返回 const 双向迭代器。                                       |
| equal_range(key)  | 返回一个 pair 对象（包含 2 个双向迭代器），其中 pair.first 和 lower_bound() 方法的返回值等价，pair.second 和 upper_bound() 方法的返回值等价。如果是 const map，则返回 const 双向迭代器。 |
| empty()           | 若容器为空，则返回 true；否则 false。                                                        |
| size()            | 返回当前 map 容器中存有键值对的个数。                                                       |
| max_size()        | 返回 map 容器所能容纳键值对的最大个数，不同的操作系统，其返回值亦不相同。                                                                       |
| operator[]       | map容器重载了 [] 运算符，只要知道 map 容器中某个键值对的键的值，就可以向获取数组中元素那样，通过键直接获取对应的值。如果是 const map，则返回 const 引用。    |
| at(key)           | 找到 map 容器中 key 键对应的值，如果找不到，该函数会引发 out_of_range 异常。如果是 const map，则返回 const 引用。                                     |
| insert()          | 向 map 容器中插入键值对。                                                                        |
| erase()           | 删除 map 容器指定位置、指定键值对或者指定区域内的键值对。后续章节还会对该方法做重点讲解。                                                        |
| swap()            | 交换 2 个 map 容器中存储的键值对，这意味着，操作的 2 个键值对的类型必须相同。如果是 const map，则无法交换。                                        |
| clear()           | 清空 map 容器中所有的键值对，即使 map 容器的 size() 为 0。如果是 const map，则无法清空。                                                            |
| emplace()         | 在当前 map 容器中的指定位置处构造新键值对。其效果和插入键值对一样，但效率更高。                                                                  |
| emplace_hint()    | 在本质上和 emplace() 在 map 容器中构造新键值对的方式是一样的，不同之处在于，使用者必须为该方法提供一个指示键值对生成位置的迭代器，并作为该方法的第一个参数。如果是 const map，则无法使用。                  |
| count(key)        | 在当前 map 容器中，查找键为 key 的键值对的个数并返回。注意，由于 map 容器中各键值对的键的值是唯一的，因此该函数的返回值最大为 1。如果是 const map，则返回 0 或 1。  |

## set

### 使用方法

#include <set>

using namespace std;

map、multimap 容器都会自行根据键的大小对存储的键值对进行排序，set 容器也会如此，只不过 set 容器中各键值对的键 key 和值 value 是相等的，根据 key 排序，也就等价为根据 value 排序。

### 创建C++ set容器的几种方法
1. std::set<std::string> myset;
2. 初始化:std::set\<std::string\> myset{"http://c.biancheng.net/java/","http://c.biancheng.net/stl/","http://c.biancheng.net/python/"};
3. std::set<std::string> copyset(myset);
4. std::set<std::string> copyset(++myset.begin(), myset.end());
5. 手动修改 set 容器中的排序规则:std::set<std::string,std::greater<string> > myset{"http://c.biancheng.net/java/", "http://c.biancheng.net/stl/","http://c.biancheng.net/python/"};

### C++ STL set容器包含的成员方法

| 成员方法       | 功能                                                                                                                                                                |
|---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| begin()       | 返回指向容器中第一个（注意，是已排好序的第一个）元素的双向迭代器。如果 set 容器用 const 限定，则该方法返回的是 const 类型的双向迭代器。                                  |
| end()         | 返回指向容器最后一个元素（注意，是已排好序的最后一个）所在位置后一个位置的双向迭代器，通常和 begin() 结合使用。如果 set 容器用 const 限定，则该方法返回的是 const 类型的双向迭代器。  |
| rbegin()      | 返回指向最后一个（注意，是已排好序的最后一个）元素的反向双向迭代器。如果 set 容器用 const 限定，则该方法返回的是 const 类型的反向双向迭代器。                           |
| rend()        | 返回指向第一个（注意，是已排好序的第一个）元素所在位置前一个位置的反向双向迭代器。如果 set 容器用 const 限定，则该方法返回的是 const 类型的反向双向迭代器。                |
| cbegin()      | 和 begin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改容器内存储的元素值。                                                                          |
| cend()        | 和 end() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改容器内存储的元素值。                                                                            |
| crbegin()     | 和 rbegin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改容器内存储的元素值。                                                                         |
| crend()       | 和 rend() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改容器内存储的元素值。                                                                           |
| find(val)     | 在 set 容器中查找值为 val 的元素，如果成功找到，则返回指向该元素的双向迭代器；反之，则返回和 end() 方法一样的迭代器。另外，如果 set 容器用 const 限定，则该方法返回的是 const 类型的双向迭代器。 |
| lower_bound(val) | 返回一个指向当前 set 容器中第一个大于或等于 val 的元素的双向迭代器。如果 set 容器用 const 限定，则该方法返回的是 const 类型的双向迭代器。                              |
| upper_bound(val) | 返回一个指向当前 set 容器中第一个大于 val 的元素的迭代器。如果 set 容器用 const 限定，则该方法返回的是 const 类型的双向迭代器。                                       |
| equal_range(val) | 该方法返回一个 pair 对象（包含 2 个双向迭代器），其中 pair.first 和 lower_bound() 方法的返回值等价，pair.second 和 upper_bound() 方法的返回值等价。也就是说，该方法将返回一个范围，该范围中包含的值为 val 的元素（set 容器中各个元素是唯一的，因此该范围最多包含一个元素）。 |
| empty()       | 若容器为空，则返回 true；否则 false。                                                                                                                               |
| size()        | 返回当前 set 容器中存有元素的个数。                                                                                                                                 |
| max_size()    | 返回 set 容器所能容纳元素的最大个数，不同的操作系统，其返回值亦不相同。                                                                                             |
| insert()      | 向 set 容器中插入元素。                                                                                                                                              |
| erase()       | 删除 set 容器中存储的元素。                                                                                                                                          |
| swap()        | 交换 2 个 set 容器中存储的所有元素。这意味着，操作的 2 个 set 容器的类型必须相同。                                                                                |
| clear()       | 清空 set 容器中所有的元素，即令 set 容器的 size() 为 0。                                                                                                             |
| emplace()     | 在当前 set 容器中的指定位置直接构造新元素。其效果和 insert() 一样，但效率更高。                                                                                      |
| emplace_hint()| 在本质上和 emplace() 在 set 容器中构造新元素的方式是一样的，不同之处在于，使用者必须为该方法提供一个指示新元素生成位置的迭代器，并作为该方法的第一个参数。                                                        |
| count(val)    | 在当前 set 容器中，查找值为 val 的元素的个数，并返回。注意，由于 set 容器中各元素的值是唯一的，因此该函数的返回值最大为 1。                                        |

## queue

### queue 容器适配器支持的成员函数

| 成员函数                   | 功能                                                                                   |
|---------------------------|----------------------------------------------------------------------------------------|
| empty()                   | 如果 queue 中没有元素的话，返回 true。                                                  |
| size()                    | 返回 queue 中元素的个数。                                                              |
| front()                   | 返回 queue 中第一个元素的引用。如果 queue 是常量，就返回一个常引用；如果 queue 为空，返回值是未定义的。|
| back()                    | 返回 queue 中最后一个元素的引用。如果 queue 是常量，就返回一个常引用；如果 queue 为空，返回值是未定义的。|
| push(const T& obj)       | 在 queue 的尾部添加一个元素的副本。这是通过调用底层容器的成员函数 push_back() 来完成的。    |
| emplace()                 | 在 queue 的尾部直接添加一个元素。                                                       |
| push(T&& obj)             | 以移动的方式在 queue 的尾部添加元素。这是通过调用底层容器的具有右值引用参数的成员函数 push_back() 来完成的。|
| pop()                     | 删除 queue 中的第一个元素。                                                             |
| swap(queue<T> &other_queue) | 将两个 queue 容器适配器中的元素进行互换，需要注意的是，进行互换的 2 个 queue 容器适配器中存储的元素类型以及底层采用的基础容器类型，都必须相同。|

## priority_queue

### 定义

template <typename T,
        typename Container=std::vector<T>,
        typename Compare=std::less<T> >
class priority_queue{
    //......
}
priority_queue 容器适配器模板类最多可以传入 3 个参数，它们各自的含义如下：
* typename T：指定存储元素的具体类型；
* typename Container：指定 priority_queue 底层使用的基础容器，默认使用 vector 容器。
* typename Compare：指定容器中评定元素优先级所遵循的排序规则，默认使用std::less<T>按照元素值从大到小进行排序，还可以使用std::greater<T>按照元素值从小到大排序，但更多情况下是使用自定义的排序规则。
### 创建priority_queue的几种方式

#include <queue>
using namespace std;

1. 创建一个空的 priority_queue 容器适配器，第底层采用默认的 vector 容器，排序方式也采用默认的 std::less<T> 方法： std::priority_queue<int> values;
2. 使用普通数组或其它容器中指定范围内的数据，对 priority_queue 容器适配器进行初始化：
//使用普通数组
int values[]{4,1,3,2};
std::priority_queue<int>copy_values(values,values+4);//{4,2,3,1}
//使用序列式容器
std::array<int,4>values{ 4,1,3,2 };
std::priority_queue<int>copy_values(values.begin(),values.end());//{4,2,3,1}
3. 手动指定 priority_queue 使用的底层容器以及排序规则：
int values[]{ 4,1,2,3 };
std::priority_queue<int, std::deque<int>, std::greater<int> >copy_values(values, values+4);//{1,3,2,4}

### priority_queue提供的成员函数

| 成员函数               | 功能                                                                                                 |
|-----------------------|------------------------------------------------------------------------------------------------------|
| empty()               | 如果 priority_queue 为空的话，返回 true；反之，返回 false。                                           |
| size()                | 返回 priority_queue 中存储元素的个数。                                                               |
| top()                 | 返回 priority_queue 中第一个元素的引用形式。                                                         |
| push(const T& obj)    | 根据既定的排序规则，将元素 obj 的副本存储到 priority_queue 中适当的位置。                              |
| push(T&& obj)         | 根据既定的排序规则，将元素 obj 移动存储到 priority_queue 中适当的位置。                                |
| emplace(Args&&... args) | Args&&... args 表示构造一个存储类型的元素所需要的数据。此函数的功能是根据既定的排序规则，在容器适配器适当的位置直接生成该新元素。 |
| pop()                 | 移除 priority_queue 容器适配器中第一个元素。                                                          |
| swap(priority_queue<T>& other) | 将两个 priority_queue 容器适配器中的元素进行互换，需要注意的是，进行互换的 2 个 priority_queue 容器适配器中存储的元素类型以及底层采用的基础容器类型，都必须相同。|


## c++常用算法

### 排序函数 需要使用#include\<algorithm\>

| 函数名                     | 用法                                                                                                                                                 |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| sort(first, last)         | 对容器或普通数组中 [first, last) 范围内的元素进行排序，默认进行升序排序。                                                                              |
| stable_sort(first, last)  | 和 sort() 函数功能相似，不同之处在于，对于 [first, last) 范围内值相同的元素，该函数不会改变它们的相对位置。                                         |
| partial_sort(first, middle, last) | 从 [first,last) 范围内，筛选出 middle-first 个最小的元素并排序存放在 [first，middle) 区间中。                                                    |
| partial_sort_copy(first, last, result_first, result_last) | 从 [first, last) 范围内筛选出 result_last-result_first 个元素排序并存储到 [result_first, result_last) 指定的范围中。                            |
| is_sorted(first, last)    | 检测 [first, last) 范围内是否已经排好序，默认检测是否按升序排序。                                                                                    |
| is_sorted_until(first, last) | 和 is_sorted() 函数功能类似，唯一的区别在于，如果 [first, last) 范围的元素没有排好序，则该函数会返回一个指向首个不遵循排序规则的元素的迭代器。     |
| nth_element(first, nth, last) | 找到 [first, last) 范围内按照排序规则（默认按照升序排序）应该位于第 nth 个位置处的元素，并将其放置到此位置。同时使该位置左侧的所有元素都比其存放的元素小，该位置右侧的所有元素都比其存放的元素大。 |

###  merge()和inplace_merge() 需要使用#include <algorithm>

#### merge()

merge() 函数用于将 2 个有序序列合并为 1 个有序序列，前提是这 2 个有序序列的排序规则相同（要么都是升序，要么都是降序）。并且最终借助该函数获得的新有序序列，其排序规则也和这 2 个有序序列相同。

** 语法格式 **
```cpp
//以默认的升序排序作为排序规则
OutputIterator merge (InputIterator1 first1, InputIterator1 last1,
                      InputIterator2 first2, InputIterator2 last2,
                      OutputIterator result);
//以自定义的 comp 规则作为排序规则
OutputIterator merge (InputIterator1 first1, InputIterator1 last1,
                      InputIterator2 first2, InputIterator2 last2,
                      OutputIterator result, Compare comp);
```

可以看到，first1、last1、first2 以及 last2 都为输入迭代器，[first1, last1) 和 [first2, last2) 各用来指定一个有序序列；result 为输出迭代器，用于为最终生成的新有序序列指定存储位置；comp 用于自定义排序规则。同时，该函数会返回一个输出迭代器，其指向的是新有序序列中最后一个元素之后的位置。

举例：
``` cpp
#include <iostream>     // std::cout
#include <algorithm>    // std::merge
#include <vector>       // std::vector
using namespace std;
int main() {
    //first 和 second 数组中各存有 1 个有序序列
    int first[] = { 5,10,15,20,25 };
    int second[] = { 7,17,27,37,47,57 };
    //用于存储新的有序序列
    vector<int> myvector(11);
    //将 [first,first+5) 和 [second,second+6) 合并为 1 个有序序列，并存储到 myvector 容器中。
    merge(first, first + 5, second, second + 6, myvector.begin());
    //输出 myvector 容器中存储的元素
    for (vector<int>::iterator it = myvector.begin(); it != myvector.end(); ++it) {
        cout << *it << ' ';
    }   
    return 0;
}
```

#### inplace_merge()函数

``` cpp
//默认采用升序的排序规则
void inplace_merge (BidirectionalIterator first, BidirectionalIterator middle,
                    BidirectionalIterator last);
//采用自定义的 comp 排序规则
void inplace_merge (BidirectionalIterator first, BidirectionalIterator middle,
                    BidirectionalIterator last, Compare comp);
```

举例：
```cpp
#include <iostream>     // std::cout
#include <algorithm>    // std::merge
using namespace std;
int main() {
    //该数组中存储有 2 个有序序列
    int first[] = { 5,10,15,20,25,7,17,27,37,47,57 };
    //将 [first,first+5) 和 [first+5,first+11) 合并为 1 个有序序列。
    inplace_merge(first, first + 5,first +11);

    for (int i = 0; i < 11; i++) {
        cout << first[i] << " ";
    }
    return 0;
}
```

### find 系列函数 引入头文件#include \<algorithm\>

#### C++ find_if()函数

和 find() 函数相同，find_if() 函数也用于在指定区域内执行查找操作。不同的是，前者需要明确指定要查找的元素的值，而后者则允许自定义查找规则。

语法格式：
```cpp
InputIterator find_if (InputIterator first, InputIterator last, UnaryPredicate pred);
```
例子：
```cpp
#include <iostream>     // std::cout
#include <algorithm>    // std::find_if
#include <vector>       // std::vector
using namespace std;
//自定义一元谓词函数
bool mycomp(int i) {
    return ((i % 2) == 1);
}
//以函数对象的形式定义一个 find_if() 函数的查找规则
class mycomp2 {
public:
    bool operator()(const int& i) {
        return ((i % 2) == 1);
    }
};
int main() {
    vector<int> myvector{ 4,2,3,1,5 };
    //调用 find_if() 函数，并以 IsOdd() 一元谓词函数作为查找规则
    vector<int>::iterator it = find_if(myvector.begin(), myvector.end(), mycomp2());
    cout << "*it = " << *it;
    return 0;
}
```
#### find_end()
常用于在序列 A 中查找序列 B 最后一次出现的位置。
语法格式:
```cpp
//查找序列 [first1, last1) 中最后一个子序列 [first2, last2)，默认pred 参数，该参数指定的是一种相等规则，即在 [first1, last1) 范围内查找和 [first2, last2) 中各个元素对应相等的子序列；
ForwardIterator find_end (ForwardIterator first1, ForwardIterator last1,
                          ForwardIterator first2, ForwardIterator last2);
//查找序列 [first2, last2) 中，和 [first2, last2) 序列满足 pred 规则的最后一个子序列
ForwardIterator find_end (ForwardIterator first1, ForwardIterator last1,
                          ForwardIterator first2, ForwardIterator last2,
                          BinaryPredicate pred);
//find_end() 函数会返回一个正向迭代器，当函数查找成功时，该迭代器指向查找到的子序列中的第一个元素；反之，如果查找失败，则该迭代器的指向和 last1 迭代器相同。
```
举例：
```cpp
#include <iostream>     // std::cout
#include <algorithm>    // std::find_end
#include <vector>       // std::vector
using namespace std;
//以普通函数的形式定义一个匹配规则
bool mycomp1(int i, int j) {
    return (i%j == 0);
}

//以函数对象的形式定义一个匹配规则
class mycomp2 {
public:
    bool operator()(const int& i, const int& j) {
        return (i%j == 0);
    }
};

int main() {
    vector<int> myvector{ 1,2,3,4,8,12,18,1,2,3 };
    int myarr[] = { 1,2,3 };
    //调用第一种语法格式
    vector<int>::iterator it = find_end(myvector.begin(), myvector.end(), myarr, myarr + 3);
    if (it != myvector.end()) {
        cout << "最后一个{1,2,3}的起始位置为：" << it - myvector.begin() << ",*it = " << *it << endl;
    }

    int myarr2[] = { 2,4,6 };
    //调用第二种语法格式
    it = find_end(myvector.begin(), myvector.end(), myarr2, myarr2 + 3, mycomp2());
    if (it != myvector.end()) {
        cout << "最后一个{2,3,4}的起始位置为：" << it - myvector.begin() << ",*it = " << *it;
    }
    return 0;
}
```
#### find_first_of()

在 A 序列中查找和 B 序列中任意元素相匹配的第一个元素

语法格式:
```cpp
//以判断两者相等作为匹配规则
InputIterator find_first_of (InputIterator first1, InputIterator last1,
                             ForwardIterator first2, ForwardIterator last2);
//以 pred 作为匹配规则
InputIterator find_first_of (InputIterator first1, InputIterator last1,
                             ForwardIterator first2, ForwardIterator last2,
                             BinaryPredicate pred);
//find_first_of() 函数用于在 [first1, last1) 范围内查找和 [first2, last2) 中任何元素相匹配的第一个元素。如果匹配成功，该函数会返回一个指向该元素的输入迭代器；反之，则返回一个和 last1 迭代器指向相同的输入迭代器。

#### lower_bound()
于在指定区域内查找不小于目标值的第一个元素。也就是说，使用该函数在指定范围内查找某个目标值时，最终查找到的不一定是和目标值相等的元素，还可能是比目标值大的元素。
语法格式：
```cpp
//在 [first, last) 区域内查找不小于 val 的元素
ForwardIterator lower_bound (ForwardIterator first, ForwardIterator last,
                             const T& val);
//在 [first, last) 区域内查找第一个不符合 comp 规则的元素
ForwardIterator lower_bound (ForwardIterator first, ForwardIterator last,
                             const T& val, Compare comp);
```

#### upper_bound()
用于在指定范围内查找大于目标值的第一个元素。
语法格式：
```cpp
//查找[first, last)区域中第一个大于 val 的元素。
ForwardIterator upper_bound (ForwardIterator first, ForwardIterator last,
                             const T& val);
//查找[first, last)区域中第一个不符合 comp 规则的元素
ForwardIterator upper_bound (ForwardIterator first, ForwardIterator last,
                             const T& val, Compare comp);
    ```

#### equel_range()
用于在指定范围内查找等于目标值的所有元素。
语法格式：
```cpp
//找到 [first, last) 范围中所有等于 val 的元素
pair<ForwardIterator,ForwardIterator> equal_range (ForwardIterator first, ForwardIterator last, const T& val);
//找到 [first, last) 范围内所有等于 val 的元素
pair<ForwardIterator,ForwardIterator> equal_range (ForwardIterator first, ForwardIterator last, const T& val, Compare comp);
```
举例：
```cpp
#include <iostream>     // std::cout
#include <algorithm>    // std::equal_range
#include <vector>       // std::vector
using namespace std;
//以普通函数的方式定义查找规则
bool mycomp(int i, int j) { return i > j; }
//以函数对象的形式定义查找规则
class mycomp2 {
public:
    bool operator()(const int& i, const int& j) {
        return i > j;
    }
};
int main() {
    int a[9] = { 1,2,3,4,4,4,5,6,7};
    //从 a 数组中找到所有的元素 4
    pair<int*, int*> range = equal_range(a, a + 9, 4);
    cout << "a[9]：";
    for (int *p = range.first; p < range.second; ++p) {
        cout << *p << " ";
    }

    vector<int>myvector{ 7,8,5,4,3,3,3,3,2,1 };
    pair<vector<int>::iterator, vector<int>::iterator> range2;
    //在 myvector 容器中找到所有的元素 3
    range2 = equal_range(myvector.begin(), myvector.end(), 3,mycomp2());
    cout << "\nmyvector：";
    for (auto it = range2.first; it != range2.second; ++it) {
        cout << *it << " ";
    }
    return 0;
}
//输出
//a[9]：4 4 4
//myvector：3 3 3 3
```

#### binary_search()
用于查找指定区域内是否包含某个目标元素。
语法格式：
```cpp
//查找 [first, last) 区域内是否包含 val
bool binary_search (ForwardIterator first, ForwardIterator last,
                      const T& val);
//根据 comp 指定的规则，查找 [first, last) 区域内是否包含 val
bool binary_search (ForwardIterator first, ForwardIterator last,
                      const T& val, Compare comp);
```

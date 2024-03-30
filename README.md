# C-STL
C++ STL summary

内容来自网络博客，链接如下：

(1) (vector)https://blog.csdn.net/Flag_ing/article/details/123380655
(2) (unordered_map)https://c.biancheng.net/view/7231.html
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

(1) 排序 sort()

按输入序列的字典序升序排序，原位操作，无返回值

函数原型：

void std::sort<std::vector<int>::iterator>(std::vector<int>::iterator, std::vector<int>::iterator)

(2) 消除相邻的重复元素 unique()

将输入序列相邻的重复项“消除”，返回一个指向不重复值范围末尾的迭代器，一般配合 sort() 使用，函数原型：

std::vector<int>::iterator std::unique<std::vector<int>::iterator>(std::vector<int>::iterator, std::vector<int>::iterator)

(3) 逆序 reverse()

将输入序列按照下标逆序排列，原位操作，无返回值函数原型：

void std::reverse<std::vector<int>::iterator>(std::vector<int>::iterator, std::vector<int>::iterator)

### vector 中找最值

容器的重排同样需要用到头文件 <algorithm> 中的算法。

(1) 最大值 auto it = max_element(v.begin, v,end())，返回最大值的迭代器，函数原型如下：

constexpr std::vector<int>::iterator std::max_element<std::vector<int>::iterator>(std::vector<int>::iterator, std::vector<int>::iterator)

(2) 最小值 auto it = min_element(v.begin, v,end())，返回最小值的迭代器，函数原型如下：

constexpr std::vector<int>::iterator std::min_element<std::vector<int>::iterator>(std::vector<int>::iterator, std::vector<int>::iterator)

(3) 相对位置大小 auto b = distance(x, y)，x、y 是迭代器类型，返回 x、y 之间的距离，可以用来获取最大/小值的索引，函数原型如下：

std::ptrdiff_t std::distance<std::vector<int>::iterator>(std::vector<int>::iterator __first, std::vector<int>::iterator __last)


## unordered_map

### 创建C++ unordered_map容器的方法

(1) std::unordered_map<std::string, std::string> umap;

(2) 在创建 unordered_map 容器的同时，可以完成初始化操作。比如：

std::unordered_map<std::string, std::string> umap{
    {"Python教程","http://c.biancheng.net/python/"},
    {"Java教程","http://c.biancheng.net/java/"},
    {"Linux教程","http://c.biancheng.net/linux/"} };

(3) std::unordered_map<std::string, std::string> umap2(umap);

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

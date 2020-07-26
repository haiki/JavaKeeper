### 数组

数组可以说是最基本最常见的数据结构。数组一般用来存储相同类型的数据，可通过数组名和下标进行数据的访问和更新。数组中元素的存储是按照先后顺序进行的，同时在内存中也是按照这个顺序进行连续存放。数组相邻元素之间的内存地址的间隔一般就是数组数据类型的大小。



因为 `字符串` 是由字符数组形成的，所以二者是相似的。大多数面试问题都属于这个范畴。



## 前言

具体介绍数组之前，我们先来了解一下集合、列表和数组的概念之间的差别。

### 集合

------

集合一般被定义为：由一个或多个确定的元素所构成的整体。

通俗来讲，集合就是将一组事物组合在一起。你可以将力扣的题库看作一个集合：

![1.png](https://pic.leetcode-cn.com/3561000569d63aeed8957e9e45a63c67991900ca463234a3aa8a9299794bde27-1.png)

 

也可以将力扣商店里的礼品看作一个集合：

![2.png](https://pic.leetcode-cn.com/c26f86483c1cdd909fa3788f32292113fc0876cdd60cbd0bb4692da722ec80e5-2.png)

甚至可以将桌面上的物品当作一个集合。

集合有什么特性呢？

首先，**集合里的元素类型不一定相同。** 你可以将商品看作一个集合，也可以将整个商店看作一个集合，这个商店中有人或者其他物品也没有关系。

其次，**集合里的元素没有顺序。** 我们不会这样讲：我想要集合中的第三个元素，因为集合是没有顺序的。

事实上，这样的集合并不直接存在于编程语言中。然而，实际编程语言中的很多数据结构，就是在集合的基础上添加了一些规则形成的。

 

### 列表

------

列表（又称线性列表）的定义为：是一种数据项构成的有限序列，即按照一定的线性顺序，排列而成的数据项的集合。

列表的概念是在集合的特征上形成的，它具有顺序，且长度是可变的。你可以把它看作一张购物清单：

![3.png](https://pic.leetcode-cn.com/6453f8d5b22edca6906f8a26df2c06758102f78939cc497407ac63c5c2e4c1d9-3.png)

在这张清单中：

- 购物清单中的条目代表的类型可能不同，但是按照一定顺序进行了排列；
- 购物清单的长度是可变的，你可以向购物清单中增加、删除条目。

在编程语言中，列表最常见的表现形式有数组和链表，而我们熟悉的栈和队列则是两种特殊类型的列表。除此之外，向列表中添加、删除元素的具体实现方式会根据编程语言的不同而有所区分。

 

### 数组

------

数组是列表的实现方式之一，也是面试中经常涉及到的数据结构。

正如前面提到的，数组是列表的实现方式，它具有列表的特征，同时也具有自己的一些特征。然而，在具体的编程语言中，数组这个数据结构的实现方式具有一定差别。比如 C++ 和 Java 中，数组中的元素类型必须保持一致，而 Python 中则可以不同。Python 中的数组叫做 list，具有更多的高级功能。

那么如何从宏观上区分列表和数组呢？这里有一个重要的概念：**索引**。

首先，数组会用一些名为 `索引` 的数字来标识每项数据在数组中的位置，且在大多数编程语言中，索引是从 `0` 算起的。我们可以根据数组中的索引，快速访问数组中的元素。

![4.png](https://pic.leetcode-cn.com/628b6f699aa49ffcc9d3c75806457c4a1a66ffe025bb651d9f8e78b4242249b9-4.png)

**而列表中没有索引，这是数组与列表最大的不同点**。

其次，数组中的元素在内存中是连续存储的，且每个元素占用相同大小的内存。

 

![5.png](https://pic.leetcode-cn.com/7b17543e4e39ae894bba0b2b6f8431b40d3df04556df06a3b974146d9e5c7d0d-5.png)

 

相反，列表中的元素在内存中可能彼此相邻，也可能不相邻。比如列表的另一种实现方式——链表，它的元素在内存中则不一定是连续的。



## 数组的操作

### 读取元素

读取数组中的元素，即通过数组的索引访问数组中的元素。

这里的索引其实就是内存地址，值得一提的是，计算机可以跳跃到任意的内存地址上，这就意味着只要计算出数组中元素的内存地址，则可以一步访问到数组中的元素。

可以形象地将计算机中的内存看作一系列排列好的格子，这些格子中，每一个格子对应一个内存地址，数据会存储在不同的格子中。

![1.png](https://pic.leetcode-cn.com/401fd00075501cac82e3605f91fa64ead061cfcabf839b2ba5a2eb87cd784b73-1.png)

而对于数组，计算机会在内存中申请一段 **连续** 的空间，并且会记下索引为 `0` 处的内存地址。例如对于一个数组 `['oranges', 'apples', 'bananas', 'pears', 'tomatoes']`，为了方便起见，我们假设每个元素只占用一个字节，它的索引与内存地址的关系如下图所示。

![2.png](https://pic.leetcode-cn.com/65312e6dff56fc0c2ffad8752d6ca08da9bb7ec03211619754abd407e05147e8-2.png)

当我们访问数组中索引为 `3` 处的元素时，计算机会进行如下计算：

- 找到该数组的索引 `0` 的内存地址： `2008`；
- `pears` 的索引为 `3`，计算该元素的内存地址为 `2008 + 3 = 2011`；

接下来，计算机就可以在直接通过该地址访问到数组中索引为 `3` 的元素了，计算过程很快，因此可以将整个访问过程只看作一个动作，因此时间复杂度为 $O(1)$。

 

### 查找元素

前面我们谈到计算机只会保存数组中索引为 `0` 处元素的内存地址，因此当计算机想要知道数组中是否包含某个元素时，只能从索引 `0` 处开始，逐步向后查询。

还是上面的例子，如果我们要查找数组中是否包含元素 `pears`，计算机会从索引 `0` 开始，逐个比较对应的元素，直到找到该元素后停止搜索，或到达数组的末尾后停止。

![3.gif](https://pic.leetcode-cn.com/e592cf43d44a9e8f7a15b85c9fd6679668fc36134b10161bfc430b85491c8b9e-3.gif)

我们发现，该数组的长度为 `5`，最坏情况下（比如我们查找元素 `tomatoes` 或查找数组中不包含的元素），我们需要查询数组中的每个元素，因此时间复杂度为$ O(N)$，*N* 为数组的长度。

 

### 插入元素

假如我们想在原有的数组中再插入一个元素 `flowers` 呢？

如果要将该元素插入到数组的末尾，只需要一步。即计算机通过数组的长度和位置计算出即将插入元素的内存地址，然后将该元素插入到指定位置即可。

![4.gif](https://pic.leetcode-cn.com/c3074c34fd36fd6f8b042421660705e2b376046fe50bc4af9fddc176e19f3eab-4.gif)

然而，如果要将该元素插入到数组中的其他位置，则会有所区别，这时我们首先需要为该元素所要插入的位置`腾出` 空间，然后进行插入操作。比如，我们想要在索引 `2` 处插入 `flowers`。

![5.gif](https://pic.leetcode-cn.com/27ee29524a3538e4c1de14953698a66b3e860e6b4984c1f454eb91fa9fbbc2f3-5.gif)

我们发现，如果需要频繁地对数组元素进行插入操作，会造成时间的浪费。事实上，另一种数据结构，即链表可以有效解决这个问题。

 

### 删除元素

删除元素与插入元素的操作类似，当我们删除掉数组中的某个元素后，数组中会留下 `空缺` 的位置，而数组中的元素在内存中是连续的，这就使得后面的元素需对该位置进行 `填补` 操作。

以删除索引 `1` 中的元素 `apples` 为例，具体过程如图所示。

![6.gif](https://pic.leetcode-cn.com/20e80a7fd6d2d34ec8d59dffe1da115c76dd1c06a9a2959a03d3261a1eab67a4-6.gif)

同样地，数组的长度为 `5`，最坏情况下，我们删除第一个元素，后面的 `4` 个元素需要向前移动，加上删除操作，共需执行 `5` 步，因此时间复杂度为 $O(N)$，*N* 为数组的长度。





## 二维数组

二维数组是一种结构较为特殊的数组，只是将数组中的每个元素变成了一维数组。

![1.png](https://pic.leetcode-cn.com/e64116dc9c9c8f9f8ad2a5c251c0e76a677ba874a3bab0e22ce164384237a55c-1.png)

所以二维数组的本质上仍然是一个一维数组，内部的一维数组仍然从索引 `0` 开始，我们可以将它看作一个矩阵，并处理矩阵的相关问题。

 

### 示例

类似一维数组，对于一个二维数组 `A = [[1, 2, 3, 4],[2, 4, 5, 6],[1, 4, 6, 8]]`，计算机同样会在内存中申请一段 **连续** 的空间，并记录第一行数组的索引位置，即 `A[0][0]` 的内存地址，它的索引与内存地址的关系如下图所示。

![2.png](https://pic.leetcode-cn.com/bf1bd2a80e026f8ce335724e54a457301f5909cfd8ae5a25f8d2692c7cdae720-2.png)

注意，实际数组中的元素由于类型的不同会占用不同的字节数，因此每个方格地址之间的差值可能不为 `1`。

实际题目中，往往使用二维数据处理矩阵类相关问题，包括矩阵旋转、对角线遍历，以及对子矩阵的操作等。





## 刷题

### 排序算法















### 双索引技巧-对撞指针

### 双索引技巧-滑动窗口













### 稀疏数组
[toc]
# 1. 函数式数据处理
## 1.1 简介
我们可以将流看作是一个遍历数据集的高级迭代器。另外流还可以透明地并行处理，我们无需再写任何多线程代码。流主要分为中间操作以及终端操作。  
中间操作有：
1. filter
2. map
3. limit
4. sorted
5. distinct 
  
终端操作有：
1. forEach
2. count
3. collect

## 1.2 使用流
### 1.2.1 筛选和切片
**filter方法**
该操作会接受一个返回boolean型的函数作为参数，并返回一个包含所有符合条件的元素的流。例如：  
```
List<Dish> vegetarianMenu = menu.stream().filter(Dish::isVegetarian).collect(toList());
```
**distinct方法**  
流支持一个叫作distinct的方法，它会返回一个元素各异的流。例如：  
```
List<Integer> numbers = Arrays.asList(1,2,1,3,3,2,4);
numbers.stream().filter(i->i%2==0).distinct().forEach(System.out.println);
```
**limit**
流支持limit(n)方法用来截断流，该方法会返回一个不超过给定长度的流。例如：  
```
List<Dish> dishes  = menu.stream().filter(d->d.getCalories()>300).limit(3).collect(toList());
```
**skip**
流还支持skip(n)方法，返回一个扔掉了前n个元素的流。如果流中元素不足n个则返回一个空流。skip和limit搭配可用来做分页操作。例如：  
```
List<Dish> dishes = menu.stream().filter(d->d.getCalories()>300).skip(3).collect(toList());
```  
### 1.2.2 映射



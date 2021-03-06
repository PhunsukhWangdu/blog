##reduce

reduce是es5中的数组的一个方法，对累加器和数组中的每个元素（从左到右）应用一个函数，将其减少为单个值。函数签名为：

	arr.reduce(function (accumulator, currentValue, currentIndex, array) {}[, initialValue])

* callback是执行数组中每个元素的函数，这个函数接收几个参数：
* accumulator:上一次callback调用的返回值，如果是第一次调用，则这个值就是initialValue。如果没有提供initialValue则使用数组的第一个元素。
* currentValue: 数组正在处理的元素
* currentIndex: 数组正在处理的元素的当前的索引
* array: 调用reduce方法的数组

**回调函数第一次执行时，accumulator 和currentValue的取值有两种情况：**

* 如果调用reduce()时提供了initialValue，accumulator取值为initialValue，currentValue取数组中的第一个值；

* 如果没有提供 initialValue，那么accumulator取数组中的第一个值，currentValue取数组中的第二个值。

注意：如果没有提供initialValue，reduce 会从索引1的地方开始执行 callback 方法，跳过第一个索引。如果提供initialValue，从索引0开始。

* 如果数组为空且没有提供initialValue，会抛出TypeError 。
* 如果数组仅有一个元素（无论位置如何）并且没有提供initialValue， 此唯一值将被返回并且callback不会被执行

		[1].reduce(()=> {console.log(111)})
		//1
		[2].reduce(()=> {console.log(111)})
		//2
* 有提供initialValue但是数组为空，那么此唯一值将被返回并且callback不会被执行。

		[].reduce(()=> {console.log(111)}, 0)
		//0
		[].reduce(()=> {console.log(111)}, 1)
		//1
		[].reduce(()=> {console.log(111)}, [])
		//[]

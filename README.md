# JavaScript Arrays

## 目标

- 解释数组是什么以及为什么使用它
- 创建一个数组
- 向数组添加一个元素
- 访问数组中的元素
- 从数组中删除元素

## 说明

你将在`arrays.js`中编码. 有一些测试可以确保你走在正确的轨道上.

## 介绍

比方说, 我们有一份烤面包干酪的配料清单(在控制台上的代码):

``` javascript
var ingredient1 = "bread"
var ingredient2 = "mild cheese"
var ingredient3 = "sharp cheese"
var ingredient4 = "butter"
var ingredient5 = "tomato"
var ingredient6 = "garlic"
```
但是如果我们想做番茄酱呢？ 嗯, 我们已经有大蒜和西红柿了, 但是我们不知道它们属于什么配方.  很快, 我们将很难保持我们的配方安全, 最后我们会在番茄酱中加面包.

![noooooooo](http://i.giphy.com/fIyBQtxwwZYhq.gif)

这是一个公认的例子, 但是它表明我们不能把所有东西都放在一个变量中, 并希望记住放进里面的顺序. 它还表明, 有时候能够对项目进行分组会很有帮助.

在JavaScript中，我们可以将对象中的项目分组 (JavaScript中的所有内容都是一个对象 - 但更多的是在其他时间) 称为_array_. 数组是由逗号分割的一个有序的列表 (称为数组的元素).

数组看起像这样: `[1, 2, 3]`.

或者像这样:

``` javascript
var grilledCheeseIngredients = [
  'bread',
  'mild cheese',
  'sharp cheese',
  'butter',
  'tomato',
  'garlic'
]

var tomatoSauceIngredients = [
  'tomato',
  'garlic',
  'olive oil',
  'basil',
  'oregano'
]
```

## 创建
JavaScript数组可以包含所有类型的值, 它们可以是混合类型. 您可以通过两种不同的方式创建数组, 最常见的方法是在一对方括号中列出值.  这些被称为**数组文字**

```javascript
var myArray = [element0, element1, ..., elementN];
```

Examples:

```javascript
var primeNumbers = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37];

var tvShows = ["game of thrones", "true detective", "the good wife", "empire"];

var weirdGreeting = [ "he", 110, "w", 0, "r", 1, "d" ];

var empty = [];
```

Array 构造器函数是另一种创建新数组的方法.

```javascript
var evenNumbers = new Array();
```

数组是_ordered_, 意味着它们中的元素将始终以相同的顺序出现. 数组`[1,1,2]`与数组`[1,2,1]`不同.

**TODO**: 在`arrays.js`中，定义一个名为 "CopyToAtBar" 的变量. 它的值应该是一组字符串 `snickers`, `hundred grand`, `kitkat`, and `skittles`.

## 添加一个元素

JavaScript允许我们将元素 `push` 推入到数组的末尾：

```javascript
var superheroines = ["catwoman", "she-hulk", "mystique"];

superheroines.push("wonder woman");
// superheroines is now ["catwoman", "she-hulk", "mystique", "wonder woman"]
```

我们也可以在一个数组的开头`unshift`插入元素：

``` javascript
var cities = ["New York", "San Francisco"]

cities.unshift("Philadelphia")

// cities is now ["Philadelphia", "New York", "San Francisco"]
```

这些动作_change_改变底层数组 - 换句话说，它们**改变**它的值。

大多数现代浏览器（Chrome，FireFox和Safari）支持所谓的**扩展运算符** - 它连续三个点：`...`. 当与数组一起使用时, 它会扩展数组的内容.

我们可以使用spread运算符来创建一个新数组，而不是修改原始数组。 我们来试试吧！

``` javascript
var cities = ["New York", "San Francisco"]

["Philadelphia", ...cities] // ["Philadelphia", "New York", "San Francisco"]

cities // ["New York", "San Francisco"]
```

哇！ 你看到了吗？ 当我们使用扩展操作:`...cities`，我们的`cities`阵列没有被触及. 我们可以在数组的开头做同样的事情:

``` javascript
var cities = ["New York", "San Francisco"]

[...cities, "Philadelphia"] // ["New York", "San Francisco", "Philadelphia"]
```
要保留新数组，我们需要将其分配给变量:

``` javascript
var cities = ["New York", "San Francisco"]

// we can assign it to the existing `cities` variable
cities = ["Philadelphia", ...cities]

// but if we have a const
const cats = ["Milo", "Garfield"]

// we need a new variable:
const moreCats = ["Felix", ...cats]
```

虽然我们_can_直接在特定索引处向数组添加元素

``` javascript
var myArray = [1, 2, 3]

myArray[5] = 5

myArray // [1, 2, 3, undefined, undefined, 5]
```

最好不要上面操作. 我们应该将数组视为可以**任意长度**的有序信息列表，因此更新特定索引应该感觉像是一件奇怪的事情. 此外，如果我们还需要增加数组的长度，添加元素会直接插入`undefined`（如上所示）, 这可能会导致意外行为.

**TODO**： 在`arrays.js`中，定义两个函数，`addElementToBeginningOfArray`和`destructivelyAddElementToBeginningOfArray`. 这两个函数都有两个参数,一个数组和一个元素添加到数组的开头，两个函数都应该将元素添加到数组的开头,然后返回整个数组. 破坏性函数`destructivelyAddElementToBeginningOfArray`应该改变传入的原始数组; 另一方面，`addElementToBeginningOfArray`应返回一个新数组**而不是修改原始**.

**TODO**：定义另外两个函数, `addElementToEndOfArray`和`destructivelyAddElementToEndOfArray`. 这些函数还有两个参数，一个数组和一个元素添加到数组的末尾. `addElementToEndOfArray` **不应该**改变原始数组; `destructivelyAddElementToEndOfArray` **应该**改变原始数组.

## 访问元素

如果你知道它们的索引，你可以从数组中获取元素。 数组元素的索引从0开始并递增1，因此第一个元素的索引是“0”，第二个元素的索引是“1”，第三个元素的索引是“2”，等等。

```javascript
var entrepreneurs = ["Oprah Winfrey", "Laurene Powell Jobs", "Arianna Huffington"];

// the line below will print the string "Oprah Winfrey"
console.log(entrepreneurs[0]);

// the code below will print the string "Arianna Huffington is the co-founder and editress-in-chief of The Huffington Post"
var bio = " is the co-founder and editress-in-chief of The Huffington Post";
console.log(entrepreneurs[2] + bio);

// the line below will return undefined
entrepreneurs[9];
```

**TODO**：在`arrays.js`中定义一个名为`accessElementInArray`的函数. 该函数应该接受一个数组和一个索引, 并返回该索引处的元素.

## 删除元素

### 从数组的开头

要从数组的开头删除元素, 我们可以使用`shift`方法:

``` javascript
const days = ["Monday", "Tuesday", "Wednesday"]

days.shift() // returns the removed element, in this case "Monday"

days // ["Tuesday", "Wednesday"]
```
和`unshift`一样，这个方法是_destructive_破坏; 它**改变**底层数组。

**TODO** ：在`arrays.js`中定义一个名为`destructivelyRemoveElementFromBeginningOfArray`的函数，它以数组作为唯一参数并删除第一个元素。 然后你的函数应该返回整个数组，它应该**改变数组**。

因为我们倾向于避免破坏，所以还有一种方法可以在不更改底层数组的情况下从数组中删除第一个元素：我们可以使用`slice`方法。

[`slice`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice) 正如它的名字所暗示的那样：它从它的数组中获取一个切片.第一个参数指定切片的起始位置,第二个参数指定切片的结束位置. 如果没有第二个参数,则切片从第一个参数（开始）到数组的结尾. 这意味着删除第一个元素就像`slice（1）`一样简单。

``` javascript
var cats = ["Milo", "Garfield", "Otis"]

cats.slice(1) // ["Garfield", "Otis"]

cats // ["Milo", "Garfield", "Otis"]
```

与其他非破坏性方法一样, 我们需要将结果分配给新变量以保存我们的更改：

``` javascript
var cats = ["Milo", "Garfield", "Otis"]

cats = cats.slice(1) // ["Garfield", "Otis"]

cats // ["Garfield", "Otis"]
```

`slice`如果我们知道我们想要数组的最后一个`n`元素, 那么它也很方便：传递一个负数索引.

``` javascript
var cats = ["Milo", "Garfield", "Otis"]

// get the last 2 cats
cats.slice(-2) // ["Garfield", "Otis"]

// get the last 1 cat
cats.slice(-1) // ["Otis"]
```

**TODO** : 在`arrays.js`中定义一个名为`removeElementFromBeginningOfArray`的函数. 它需要一个`array`作为唯一的参数. 该函数应该删除数组中的第一个元素. 这个函数应该在同一行返回_entire_整个的数组,它**不应该**改变原始数组.

### 从数组的末尾开始

要从数组的末尾删除元素,我们可以使用`pop`方法:

``` javascript
var iceCreams = ["chocolate", "vanilla", "raspberry"]

iceCreams.pop() // returns the removed element, in this case "raspberry"

iceCreams // ["chocolate", "vanilla"]
```
和`push`一样，这个方法是_destructive_破坏; 它**改变**底层数组。

**TODO**：在`arrays.js`中定义一个名为`destructivelyRemoveElementFromEndOfArray`的函数, 它以数组作为唯一参数并删除最后一个元素. 你的函数应该返回整个数组，它应该**改变数组**。

我们可以使用`slice`来执行上述操作,而无需更改底层数组. 它比删除第一个元素要花费更多的工作,因为我们希望切片从索引"0"（记住,第一个元素在索引"0"!）到结尾. 嗯 - 数组有什么属性可以帮助我们？`length`!

``` javascript
var iceCreams = ["chocolate", "vanilla", "raspberry"]

iceCreams.slice(0, iceCreams.length - 1) // ["chocolate", "vanilla"]

iceCreams // ["chocolate", "vanilla", "raspberry"]
```

**TODO**: 在`arrays.js`中定义一个名为`removeElementFromEndOfArray`的函数,它以数组作为唯一参数并删除最后一个元素. 你的函数应该返回没有最后一个元素的数组，它**不应该**改变原始数组。

### 从数组的中间

在JavaScript中从数组中间删除元素比从开头或结尾删除元素有点棘手. 我们有`splice`方法,它将数组中的索引作为其第一个参数,将要删除的元素数作为其第二个参数,以及在第二个参数之后添加为任何参数的任意数量的元素. 所有参数都是可选的,但是没有参数,`splice（）`返回一个空数组,对目标数组不执行任何操作.

参考可能会有所帮助[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)除了我们的示例之外,还要查看他们的示例.

``` javascript
let items = [1, 2, 3, 4]

// this will remove everything after index 1 (inclusive)
// it returns the removed items: [2, 3, 4]
items.splice(1)

items // [1]

items = [1, 2, 3, 4]

 // "at index 1, remove 1 item"
 // it returns the removed item(s): [2]
items.splice(1, 1)

items // [1, 3, 4]

items = [1, 2, 3, 4]

// "at index 1, remove 1 item and add 6 and add 7"
// it returns the removed items: [2]
// and adds the items to add starting at the removal index
items.splice(1, 1, 6, 7)

items // [1, 6, 7, 3, 4]
```
正如我们上面提到的，在数组中间的特定索引处添加元素_feels_感觉不可思议 - 这是难以做到的，与对象一起（我们有键而不是顺序索引）这样做更自然。

**意外收获**

我们可以使用`slice`,结合扩展运算符,使得从数组中间删除更容易.

``` javascript
var items = [1, 2, 3, 4, 5]

// let's remove the third element

// a slice from the start up to but not including index 2 (the third element)
// and a slice from index 3 to the end
[...items.slice(0, 2), ...items.slice(3)] // [1, 2, 4, 5]
```

稍微玩一下,直到它有意义. 这是你到目前为止遇到的最棘手的事情, 所以想要不出汗, 就需要一点点了解它！

## Array Wackiness

### 数组索引并不完全是它们看起来的样子

如果你有猜测，你会说数组索引是*数字*还是*字符串*？想一想，然后继续读下去

数组索引实际上是_strings_字符串,尽管我们通常把它们称为数字.但是你不相信我的话:试着在控制台上键入`"Object.keys([1, 2, ,3])"`键`([1,2,3])`,看看什么会回来.

最终，这意味着数组索引是可以使用括号通过数组样式表示法访问的字符串，当在引擎盖下需要时，数字将被*强制*为字符串。在控制台中，尝试使用字符串访问索引，以便自己查看：

```javascript
var arr = ["under", "the", "hood"];

arr[0];  // "under"
arr['0']; // "under"
arr[02]; // 02 the number *is* 2, so you get "hood"
arr['02']: // '02' the string is *not* 2, so you get undefined
```

如果您试图通过无意中使用字符串给数组索引赋值，这个小点子可能会派上用场。比如说，通过从一个零填充格式化的字符串列表中获取数组位置，这些字符串存储为字符串，然后使用这些字符串访问数组元素。

或者用一个数组索引一个变量，该变量的内容不以任何方式表示一个数字——比如键入`myArray['bonobo monkey'] = 27`.

你不会得到任何抱怨，因为你不给数组添加一个索引，而是添加了一个**属性**。说到哪一个…

### 我们可以将属性添加到数组中

在JavaScript中，一切最终都是一个对象。我们将进一步探讨在覆盖对象时这意味着什么，但是现在，要知道这意味着我们可以将_properties_属性添加到几乎所有内容中，包括数组。

属性是一个命名的信息片段。 它们是_kind of_有点像变量(不要用那个类推太过分),但是我们只能参照属性所有者来获得这些信息

那么，是什么使数组特别呢?数组通过`length` 属性跟踪它们中有多少元素: `[1, 2, 3].length // 3`. `length` 不像对象/数组中的其他键/索引那样工作——它自动更新, 如果更改它,则更改整个数组.

``` javascript
var myArray = [1, 2, 3]

myArray.length // 3

myArray.length = 1

myArray // [1] (!!!)
```

重要的是要记住JavaScript中的数组有点不太好. 您可以将属性分配给它们:

```js
var array = [1, 2, 3];

array.myProperty = "I'm a property!";
```

会导致奇怪的行为:

```js
array;
// [1, 2, 3];

// Where did our property go?
array.myProperty;
// "I'm a property!";

array.length;
// 3 - Would you have expected 3 or 4?
```

我们并不是故意去做这些事情,但重要的是要意识到它们会发生,这样你就可以很好地了解到何时/何时出现奇怪的bug.

## Resources

* [MDN - Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
* [Codecademy - Arrays](http://www.codecademy.com/glossary/javascript)

<p class='util--hide'>显示 <a href='https://learn.co/lessons/javascript-arrays'>JavaScript Arrays</a>在Celn.Co上，开始免费学习代码。</p>

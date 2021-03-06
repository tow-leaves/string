概述
split() 方法通过把字符串分割成子字符串来把一个 String 对象分割成一个字符串数组。

语法
str.split([separator][, limit])

参数
separator
指定用来分割字符串的字符（串）。separator 可以是一个字符串或正则表达式。 如果忽略 separator，则返回整个字符串的数组形式。如果 separator 是一个空字符串，则 str 将会把原字符串中每个字符的数组形式返回。
limit
一个整数，限定返回的分割片段数量。split 方法仍然分割每一个匹配的 separator，但是返回的数组只会截取最多 limit 个元素。
描述EDIT
split 方法返回一个数组。

当找到一个 seperator 时，separator 会从字符串中被移除，返回存进一个数组当中的子字符串。如果忽略 separator 参数，则返回的数组包含一个元素，该元素是原字符串。如果 separator 是一个空字符串，则 str 将被转换为由字符串中字符组成的一个数组。

如果 separator 是一个正则表达式，且包含捕获括号（capturing parentheses），则每次匹配到 separator 时，捕获括号匹配的结果将会插入到返回的数组中。然而，不是所有浏览器都支持该特性。

Note: 当字符串为空时，split 返回一个包含一个空字符串的数组，而不是一个空数组。
示例EDIT
例子：使用 split

下例定义了一个函数：使用指定的分隔符将一个字符串分割成一个字符串数组。分隔字符串后，该函数依次输出原始字符串信息，被使用的分隔符，返回数组元素的个数，以及返回数组中所有的元素。

function splitString(stringToSplit, separator) {
  var arrayOfStrings = stringToSplit.split(separator);

  print('The original string is: "' + stringToSplit + '"');
  print('The separator is: "' + separator + '"');
  print("The array has " + arrayOfStrings.length + " elements: ");

  for (var i=0; i < arrayOfStrings.length; i++)
    print(arrayOfStrings[i] + " / ");
}

var tempestString = "Oh brave new world that has such people in it.";
var monthString = "Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec";

var space = " ";
var comma = ",";

splitString(tempestString, space);
splitString(tempestString);
splitString(monthString, comma);
上例输出下面结果：

The original string is: "Oh brave new world that has such people in it."
The separator is: " "
The array has 10 elements: Oh / brave / new / world / that / has / such / people / in / it. /

The original string is: "Oh brave new world that has such people in it."
The separator is: "undefined"
The array has 1 elements: Oh brave new world that has such people in it. /

The original string is: "Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec"
The separator is: ","
The array has 12 elements: Jan / Feb / Mar / Apr / May / Jun / Jul / Aug / Sep / Oct / Nov / Dec /
例子：移出字符串中的空格

下例中，split 方法会查找“0 或多个空白符接着的分号，再接着 0 或多个空白符”模式的字符串，找到后，就将空白符从字符串中移除，nameList 是 split 的返回数组。

var names = "Harry Trump ;Fred Barney; Helen Rigby ; Bill Abel ;Chris Hand ";

print(names);

var re = /\s*;\s*/;
var nameList = names.split(re);

print(nameList);
上例输出两行，第一行输出原始字符串，第二行输出结果数组。

Harry Trump ;Fred Barney; Helen Rigby ; Bill Abel ;Chris Hand
Harry Trump,Fred Barney,Helen Rigby,Bill Abel,Chris Hand
例子：限制返回值中分割元素数量

下例中，split 查找字符串中的 0 或多个空格，并返回找到的前 3 个分割元素（splits）。

var myString = "Hello World. How are you doing?";
var splits = myString.split(" ", 3);

print(splits);
上例输出：

Hello,World.,How
例子：捕获括号（Capturing parentheses）

如果 separator 包含捕获括号（capturing parentheses），则其匹配结果将会包含在返回的数组中。

var myString = "Hello 1 word. Sentence number 2.";
var splits = myString.split(/(\d)/);

print(splits);
上例输出：

Hello ,1, word. Sentence number ,2,.

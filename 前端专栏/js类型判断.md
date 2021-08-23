对js中元素类型判断做个总结。

# 1.typeof
typeof可以区分的类型：String Number undefined Boolean Symbol BigInt。

# 2.Array.isArray()
是否是数组

# 3.其他
除以上的数据类型还有Null、Date等，可以使用`Oject.prototype.toString.call(Car).slice(8, -1).toLowerCase()`来判断。这种方法其实概括了上述的两种方法，在使用中直接使用次方法即可，如下示例：
```
> Object.prototype.toString.call([]).slice(8, -1).toLowerCase()
< "array"
> Object.prototype.toString.call('').slice(8, -1).toLowerCase()
< "string"
> Object.prototype.toString.call(1).slice(8, -1).toLowerCase()
< "number"
```
PS: instanceof
用于检测构造函数的 prototype 属性是否出现在某个实例对象的原型链上.(也就是此实例是否继承此类)
```
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
const auto = new Car('Honda', 'Accord', 1998);
console.log(auto instanceof Car);
// true
```

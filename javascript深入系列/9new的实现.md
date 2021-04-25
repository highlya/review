new的实现
  1.创建一个新的对象obj
  2.传入第一个参数为构造函数，
  3.将obj的原型指向构造函数，这样obj能访问到构造函数原型中的属性
  4.使用apply改变构造函数的this指向到obj，这样obj能访问到构造函数中的属性
  5.返回obj或函数执行结果

function objectFactory() {
    var obj = new Object(),
    Constructor = [].shift.call(arguments);
    obj.__proto__ = Constructor.prototype;
    var ret = Constructor.apply(obj, arguments);
    return typeof ret === 'object' ? ret : obj;
};
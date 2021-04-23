call()  在使用一个指定this的值和若干个参数值的前提下，调用某个函数或方法
var foo={
  value:1
}
function bar(){
  console.log(this.value)
}
bar.call(foo)
模拟步骤：
1.将函数设为对象的属性
2.执行该函数
3.删除该函数
Function.prototype.call2=function(context){
  context.fn=this
  context.fn()
  delete context.fn
}
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
Function.prototype.apply=function(context){
  var context = context || window;
  context.fn = this;
  var args=[]
  for(var i=1;i<=arguments.length;i++){
    args.push('arguments[' + i + ']');
  }
  var result = eval('context.fn(' + args +')');
  delete context.fn
  return result 
}
Function.prototype.call=function(context,arr){
  var context = context || window;
  context.fn = this;
  var args=[]
  if(!arr){
    result=context.fn()
  }
  for(var i=1;i<=arr.length;i++){
    args.push('arr[' + i + ']');
  }
  var result = eval('context.fn(' + args +')');
  delete context.fn
  return result 
}
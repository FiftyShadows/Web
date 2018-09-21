数组的filter可以很容易地实现并集（Union）、交集（Intersect）和差集（Difference)


Set提供了去除数组重复成员的另一种方法

function dedupe(array) {
  return Array.from(new Set(array));
}


let unique = [...new Set(arr)];
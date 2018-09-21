Set提供了去除数组重复成员的另一种方法

function dedupe(array) {
  return Array.from(new Set(array));
}
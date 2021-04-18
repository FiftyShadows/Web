# 6.面向对象

## 面向对象类

* 类与实例
  * 类的声明
  * 生成实例
* 类与继承
  * 如何实现继承
  * 继承的几种方式

## 类的声明两种方式

1. 用构造函数模拟一个类
2. ES6中对class的声明

## 生成实例

如果构造函数没有参数，new后边的（）可以省略。

## 如何实现继承

* 借助构造函数实现继承
  * 缺点：只实现了部分继承，如果父类的属性和方法都在构造函数里没问题，如果父类的原型对象上还有属性和方法，子类获取不到
* 借助原型链实现继承
  * 缺点：继承的方法和属性指向同一地址，一旦改变，所有的实例都会改变
* 组合方式
  * 缺点：属性和方法冗余
* 组合继承的优化1
  * 缺点：instance不能准确判断

## 继承的几种方式

```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>面向对象</title>
</head>
<body>
    <script type="text/javascript">
        /**
         *类的声明
         */
        function Animal() {
            this.name = 'name';
        }

        /**
         *ES6中的class的声明
         */
        class Animal2 {
            constructor() {
                this.name = name;
            }
        }

        /**
         *实例化
         */
        console.info(new Animal(), new Animal2());

        /**
         *借助构造函数实现继承
         */
        function Parent1() {
            this.name = 'parent1';
        }
        Parent1.prototype.say = function (){};
        function Child1() {
            Parent1.call(this);
            this.type = 'child1';
        }

        console.info(new Child1);
        // console.info(new Child1().say());

        /**
         *借助原型链实现继承
         */
        function Parent2() {
            this.name = 'parent2';
            this.play = [1, 2, 3];
        }
        function Child2() {
            this.type = 'child2';
        }
        Child2.prototype = new Parent2();

        console.info(new Child2());

        var s1 = new Child2();
        var s2 = new Child2();
        console.info(s1.play, s2.play);
        s1.play.unshift(4);
        console.info(s1.play, s2.play);

        /**
         *组合方式
         */
        function Parent3() {
            this.name = 'parent3';
            this.play = [1, 2, 3];
        }
        function Child3() {
            Parent3.call(this);
            this.type = 'child3';
        }
        Child3.prototype = new Parent3();

        var s3 = new Child3();
        var s4 = new Child3();
        s3.play.push(4);
        console.info(s3.play, s4.play);

        /**
         *组合继承的优化1
         */
        function Parent4() {
            this.name = 'parent4';
            this.play = [1, 2, 3];
        }
        function Child4() {
            Parent3.call(this);
            this.type = 'child3';
        }
        Child4.prototype = Parent4.prototype;

        var s5 = new Child4();
        var s6 = new Child4();
        s5.play.push(4);
        console.info(s5, s6);

        console.info(s5 instanceof Child4, s5 instanceof Parent4);

        /**
         *组合继承的优化2
         */
        function Parent5() {
            this.name = 'parent5';
            this.play = [1, 2, 3];
        }
        function Child5() {
            Parent3.call(this);
            this.type = 'child3';
        }
        Child5.prototype = Object.create(Parent5.prototype);
        Child5.prototype.constructor = Child5;

        var s7 = new Child5;
        console.info(s7 instanceof Child5, s7 instanceof Parent5);
        console.info(s7.constructor );
    </script>    
</body>
</html>
```


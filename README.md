本人的第一个博客。记录
JavaScript中的继承
1）对象冒充

![mao chong](http://ol5jsz3yf.bkt.clouddn.com/extendVir.png)

红色里面三行代码最关键。《问题》相同方法会覆盖
2）call方法方式《任何方法都有call()这个方法》
call 方法是Function对象中的方法，因此我们定义的每个函数都拥有该方法。可以通过函数名来调用call方法，call方法的第一个参数会被传递给函数中的this，从第二个参数开始，逐一赋给函数中的参数。

![call in](http://ol5jsz3yf.bkt.clouddn.com/extendCall.png)

//使用call方式实现对象的继承、
   ```      
  function Parent(username){
        this.username=username;
        this.sayHello=function()
        {
            alert(this.username);
        }
    }
    function Child(username,password){
        Parent.call(this,username);
        this.password=password;
        this.sayWorld=function(){
            alert(this.password);
        }
    }
    var parent =new Parent("HFJEW");
    var child= new Child("lisf","1233");
    parent.sayHello();
    child.sayHello();
    child.sayWorld();
```
3）applay方法方式

![applay in](http://ol5jsz3yf.bkt.clouddn.com/extendApply.png)

4）通过原型链的方式实现对象继承

![prototype in](http://ol5jsz3yf.bkt.clouddn.com/extendPrototype.png)

5）混合方式《推荐》

![fixed in](http://ol5jsz3yf.bkt.clouddn.com/extendFix.png)  

创建对象，用原型扩展方法，继承等的练习。实现测三角形面积和矩形面积和边为多少。
```
<head>
    <title></title>
</head>
<body>
<script>
//父对象
    function Shape(height,width){
        this.height=height;
        this.width=width;

    }
    Shape.prototype.getArea=function(){
        var height=this.height;
        var width=this.width;

            if(this.edg==3){
            area= height * width / 2;
            alert(area);
        }else if(this.edg==4){
            area= height * width ;
            alert(area);
        }else{
            return false;
        }
        }
《！。。。。。。。。。！》
//子对象
    function Trige(height,width){
        Shape.call(this,height,width); //继承父对象属性
        this.edg=3;
    }
    Trige.prototype= new Shape(); //继承父对象方法
    /*Trige.prototype.getArea=function(height,width){
        var height=this.height;
        var width=this.width;
        area= height * width / 2;

        alert(area);
    }*/
    Trige.prototype.getEdge=function(){
        alert(this.edg);
    }
    function Fourige(height,width){
        Shape.call(this,height,width);
        this.edg=4;
    }
    Fourige.prototype= new Shape();
    /*Fourige.prototype.getArea=function(height,width){
        var height=this.height;
        var width=this.width;
        area= height * width;
        alert(area);
    }*/

    Fourige.prototype.getEdge=function(){
        alert(this.edg);
    }

    var tri= new Trige("2","4");
    var four= new Fourige(4,8);
    tri.getEdge();

    tri.getArea();
    four.getEdge();
    four.getArea();
</script>
</body>
</html>
```

教师的方法

![teach in](http://ol5jsz3yf.bkt.clouddn.com/extendTeach.png)  


### 变量

### 函数 

### 函数  带参数


### 嵌套

将&放到当前选择器之后，就会将当前选择器插入到所有的父选择器之前。



.a{
  .b{
    .c{
      color: 123;
    }
  }
}

.a{
  .b{
    .c&{
      color: 123;
    }
  }
}

它们的编译结果 分别是：
 
.a .b .c {
  color: 123;
}
.c.a .b {
  color: 123;
}
 


### import 引用

  @import "lib.less";
  @import "lib";

### 运算 加减乘除


### &  串联选择器


### mixin


### color 函数  HSL
  - spin 色调
  - saturate,desaturate 饱和度  
  - lighten,darken 明度
  - fadein,fadeout,fade 透明度
  - mix(@color1,@color2) 混合2个颜色

  ```css
  lighten(@color, 10%);     // return a color which is 10% *lighter* than @color
  darken(@color, 10%);      // return a color which is 10% *darker* than @color

  saturate(@color, 10%);    // return a color 10% *more* saturated than @color
  desaturate(@color, 10%);  // return a color 10% *less* saturated than @color

  fadein(@color, 10%);      // return a color 10% *less* transparent than @color
  fadeout(@color, 10%);     // return a color 10% *more* transparent than @color
  fade(@color, 50%);        // return @color with 50% transparency

  spin(@color, 10);         // return a color with a 10 degree larger in hue than @color
  spin(@color, -10);        // return a color with a 10 degree smaller hue than @color

  mix(@color1, @color2);    // return a mix of @color1 and @color2
  ```

  ### Math 函数

  round,ceil,floor
  percentage    //percentage(0.5)  return '50%'


  ### 命名空间

    ```
      #bundle {
      .button () {
        display: block;
        border: 1px solid black;
        background-color: grey;
        &:hover { background-color: white }
      }
      .tab { ... }
      .citation { ... }
    }
   
    //你只需要 这样引入 .button:

    #header a {
      color: orange;
      #bundle > .button;
    }
    ```


### JavaScript 表达

  @var: `"hello".toUpperCase() + '!'`;  //@var:"HELLO@";

  //也可以访问JavaScript环境:
  @height: `document.body.clientHeight`;
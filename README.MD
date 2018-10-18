## 面试技巧（ 基本技能篇 初次面试 ）
### 目录
---------------------
* 页面布局
* CSS 盒子模型
* Dom 事件
* HTTP协议
* 面向对象
* 原型链
* 通信
* 安全
* 算法
---------------------
#### 页面布局
+ 页面布局案例
> 题目：假设高度已知,请写出三栏布局,其中左右栏宽度为300PX,中间自适应，如下图：
![在GitHub能显示](https://github.com/CaiweiGG/img-RemoteReference/blob/master/images/imagesMD/FirstInterview/tableDemo.jpg)
#### 第一种布局方式 “浮动大法”
``` <style media="screen">
        /* CSS reset */
        *{
            margin: 0;
            padding: 0;
            list-style: none;
        }
        /* 全局样式控制 */
        .layout article div {
            min-height: 150px;
        }
    </style>
    <body>
       <section class="layout float">
           <style media="screen">
               .layout .left{
                   width: 300px;
                   float: left;
                  border: 3px solid #ccc;
               }
               .layout .right{
                   float: right;
                   width: 300px;
                   border: 3px solid #ccc;
               }
               .layout .center{
                   border: solid 2px red;
               }
           </style>
           <article class="left-right-center clearfloat">
               <div class="left"></div>
               <div class="right"></div>
               <div class="center">
                   <h1>通过浮动来解决</h1>
                    这是三栏的中间部分
               </div> 
           </article>
       </section>
</body>
```
> 温馨提示：这个布局方式一定要注意center盒子要放在三个盒子的最下方，否则会出现right盒子跌落的情况。
#### 第二种布局方式 “定位大法”
```
       <section class="layout absolute">
           <style media="screen">
               .left-right-center{
                   position: relative;
               }
               .layout .left{
                   width: 300px;
                   position: absolute;
                  border: 3px solid #ccc;
                  left: 0;
                  top: 0;
               }
               .layout .right{
                   right: 0;
                   top: 0;
                   position: absolute;
                   width: 300px;
                   border: 3px solid #ccc;
               }
               .layout .center{
                   border: solid 2px red;
                   padding: 0 300px 0 300px;
               }
           </style>
           <article class="left-right-center">
               <div class="left"></div>
               <div class="right"></div>
               <div class="center">
                   <h1>通过绝对定位来实现</h1>
                    这是三栏的中间部分
               </div> 
           </article>
       </section>
</body>
```
> 温馨提示：如果两边不设置padding内容将会被隐藏。
#### 第三种布局方式 ”Flex 弹性布局“
```
<section class="layout flex">
           <style media="screen">
               .left-right-center{
                   display: flex;
               }
               .left-right-center .left,.left-right-center .right{
                   background-color: blue;
                   width:300px;
               }
               .left-right-center .center{
                   flex: 1;
               }
           </style>
           <article class="left-right-center">
               <div class="left"></div>
               <div class="center">
                    <h1>通过弹性布局来实现</h1>
                     这是三栏的中间部分
                </div> 
               <div class="right"></div>
           </article>
       </section>
```
> 温馨提示：建议还不明白弹性盒子模型的，可以参考[弹性布局教程](https://www.runoob.com/w3cnote/flex-grammar.html)!
#### 第四种布局方式 ”表格布局“
```
# React用户界面开发框架
React是Facebo内部的一个JavaScript内部类库，于2013年开源。它引入了一种全新的方式来处理浏览器Dom。那些需要手动更新Dom的日子将一去不复返。

React发源于Facebook的PHP框架XHP的一个分支。XHP作为PHP框架，旨在每次有请求进来是渲染整个页面。React的产生就是为了重新渲染整个页面的PHP式工作流程带到客户端应用来。

React本质上是一个“状态机”，可以帮助开发者管理复杂的随时间而改变的状态。它以一个精简的模型实现了这一点。React只关心两件事：

- 更新DOM
- 响应事件

React不处理Ajax、路由和数据存储，也不规定数据组织方式。它不是一个MVC框架。非问它是什么，它就是MVC中的"V"。

传统的处理方式，在每次状态改变是，使用JavaScript重新渲染整个页面会异常慢，这应该归咎于读取和更新DOM的性能问题。React运用一个[虚拟DOM](#2-dom)实现了一个非常强大的渲染系统，在React中对DOM**只更新不读取**。

React在整个应用中只使用单个事件处理器，并且会把所有事件委托到这个处理器上。这一点也提升了React的性能，因为如果有很多事件处理器也会导致性能问题。
## 学习资源
- [10 个 ReactJS 入门资源](http://www.oschina.net/translate/10-resources-to-get-you-started-with-reactjs)

## React新概念
### 1. JSX

JSX(JavaScript XML) 是`js`内定义的一套XML语法，可以解析出目标js代码,颠覆传统`js`写法。实质上`HTML`也是`xml`协议，有由浏览器解析，而`JSX`是由`js`解析。当让也可以通过构建工具先解析生成，如`grunt`、`webpack`,这样可以减少代码这行中js解析JSX的时间，这个后面会专题讲诉。JSX原本是使用官方自己提供的方法处理，2015-7-12日官方[博客文章](http://facebook.github.io/react/blog/2015/06/12/deprecating-jstransform-and-react-tools.html)声明其自身用于JSX语法解析的编译器JSTransform已经过期，不再维护，`React JS`和`React Native`已经全部采用第三方`Babel`的JSX编译器实现。

#### 1.1 用法
[英文版官方说明](http://docs.reactjs-china.com/react/docs/jsx-in-depth.html) [中文版官方说明](http://reactjs.cn/react/docs/jsx-in-depth.html)

看个简单例子example01

```html
<!DOCTYPE html>
<html>
    <head>
        <script src="../build/react.js"></script>
        <script src="../build/react-dom.js"></script>
        <script src="../build/browser.min.js"></script>
    </head>
    <body>
        <div id="example"></div>
        <script type="text/babel"><!--注意type声明是babel（当前用法），之前是JSX-->
            ReactDOM.render(
            	<h1>Hello, world!</h1>, document.getElementById('example') 
            );
        </script>
    </body>
</html>
```
#### 1.2 JSX优点

- `更加熟悉`，语法跟HTML非常相似（90以上相似度）
- `更加语义化`，允许自定义标签及组件。
- `更加直观`，标签处理方式，更加可读。
- `抽象化`，React的升级，不需要改动任何JSX代码。
- `关注点分离`，JSX以干净且简洁的方式保证了组件中的标签与所有业务逻辑的互相分离。

### 2. 虚拟DOM

虚拟DOM，简单来说，是一个模拟DOM树的JavaScript对象。React对UI的更新，并没有使用传统的方式: 移除指定区域的所有DOM节点，然后把新节点添加进去，而是采用了差异更新的办法。

React会在内存中保留一份指定的原始DOM对应的JavaScript对象，更新之前对比其和新DOM树的JavaScript对象之间的差异，并精确计算出差异所在，然后对存在差异的DOM的属性或文本进行更新。

例如，使用Ajax更新列表的内容，由第一页转向第二页的过程中，如果两页数据形成的DOM树有完全相同的结构，则不会有任何DOM的删除或添加操作，React仅仅会更新存在差异的原始DOM的属性或文本值。差异更新的办法，将DOM的添加、删除的操作频次降到了最低，也因而减轻了DOM渲染效率低的限制，从而让React对UI的操作获得了极大的速度提升。

## React知识点
### 
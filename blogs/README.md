# 从“零”开始 ：Spring MVC
**Author : ToMax**

> 本学期的设计模式课设要求使用spring之类的Java web框架实现一个B/S架构的应用，一方面，通过该系列博客复习spring mvc的一些知识，另一方面，帮助一些从未接触过web开发的同学能够快速的开始课设。

## 简介

> 系列博客主要构成为开发环境搭建、spring简介、spring之HelloWorld、简单网页开发（想要更好效果的页面开发效果请参考addoneG的相关博客）、数据库开发、登录注册功能的实现、简单留言功能的实现

## 目录

1. [开发环境搭建](https://github.com/XingToMax/DesignPatternDemo/blob/master/blogs/%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.md)
2. [建立一个Spring mvc项目，Hello world！](https://github.com/XingToMax/DesignPatternDemo/blob/master/blogs/Helloworld.md)
3. [讲一个和Java web项目中mvc有关的情景](https://github.com/XingToMax/DesignPatternDemo/blob/master/blogs/mvc.md)
4. [前后端的数据交互](https://github.com/XingToMax/DesignPatternDemo/blob/master/blogs/%E5%89%8D%E5%90%8E%E7%AB%AF%E6%95%B0%E6%8D%AE%E4%BA%A4%E4%BA%92.md)
5. [增加数据库支持](https://github.com/XingToMax/DesignPatternDemo/blob/master/blogs/%E5%A2%9E%E5%8A%A0%E6%95%B0%E6%8D%AE%E5%BA%93%E6%94%AF%E6%8C%81.md)
6. [登录注册功能的实现](https://github.com/XingToMax/DesignPatternDemo/blob/master/blogs/%E7%99%BB%E5%BD%95%E6%B3%A8%E5%86%8C%E5%8A%9F%E8%83%BD%E7%9A%84%E5%AE%9E%E7%8E%B0.md)
7. [简单留言功能的实现](https://github.com/XingToMax/DesignPatternDemo/blob/master/blogs/%E7%AE%80%E5%8D%95%E7%95%99%E8%A8%80%E5%8A%9F%E8%83%BD%E7%9A%84%E5%AE%9E%E7%8E%B0.md)
8. [总结](https://github.com/XingToMax/DesignPatternDemo/blob/master/blogs/%E6%80%BB%E7%BB%93.md)
9. [问题跟踪和更新说明](https://github.com/XingToMax/DesignPatternDemo/blob/master/blogs/%E9%97%AE%E9%A2%98%E8%B7%9F%E8%B8%AA%E5%92%8C%E6%9B%B4%E6%96%B0%E8%AF%B4%E6%98%8E.md)

## 阅读须知

+ 本系列博客的主要目的为快速完成课设的要求，所以会尽量回避一些概念性的东西，为了方便理解，会用一些比较通俗却不一定准确的描述解释一些功能

+ 博客间有一定的连贯性，所以部分解释会在一篇博客之后的博客中给出，所以，见到不是很理解的地方，不需要太关心，继续读下去

+ 会有详细的代码给出，同时会讲解如何在并不熟悉spring的情况下通过一些模仿来实现非复杂功能。所以，大家可以通过系列博客的教程来获取完成课设的手段，但是，具体的功能及实现，需要自己去研究

+ 本系列博客比较适合几乎没有web开发经验的同学、不打算深入学习spring的同学，需要对于java有最起码的了解，熟悉面向对象编程，如果不了解java，在阅读博客前尽量用半天时间完成java基础的学习

+ **提前学习一下java中的一些命名规范，保证编程时所有单词拼写的正确性，避免不必要的错误，这一点很重要**

+ 默认读者对于html、css、javascript有最起码的认识

+ 博客过程中如果发现一些不熟的概念，可以通过百度去了解，但是有可能会出现很多不熟悉的概念，所以尽量根据自身的需要做出取舍，一些概念会在后续的某个地方得到解答，也可能会忽略，但尽量会避免因为概念的理解而影响过程的开发

+ 代码中可能会有很多个人开发的痕迹，切勿抄袭，否则后果自负

## 对于课设与项目区别的一些理解

+ 课设主要用于呈现对于一些知识的掌握，将学习的知识实践，重在练习与展现；项目是对于具体问题的解决方案，需要面向用户，存在大量知识的延伸。
+ 课设对于应用健壮性的要求较低，基本能满足在开发环境下运行，特定的用例即可；项目产出的应用需要有一定的健壮性，不仅要在开发环境下进行完备的单元测试，还要保证在不同的需求应用背景下正常运行，具有兼容性，同时需要构造充分的测试用例
+ 课设的实现通常没有一个明确的流程，基本只包含开发与报告输出两个过程；项目的实现有一个比较明确的流程，从需求分析、设计、开发、测试到发布，再到运维，开发仅是其中比较关键的一部分。
+ 课设基本不存在团队协作，通常开发人数不超过两人；项目则通常会由团队协作进行，团队规模不定，涉及团队建设与管理
+ 课设通常不考虑程序的并发性；项目需要考虑用户量，做相应的并发处理
+ 课设的生命周期通常始于问题的提出，终于验收；而项目在发布后还需要团队定期维护，修复一些存在的问题，发布优化、更新的版本
+ 还有很多......

[下一篇：开发环境搭建](https://github.com/XingToMax/DesignPatternDemo/blob/master/blogs/%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.md)

<br>

> 如果有帮助的话，来颗star吧
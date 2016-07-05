---
layout:     post
title:      "PHP设计模式之单例模式"
subtitle:   ""
date:       2016-07-5 12:00:00
author:     "Jason"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 设计模式
---

##描述
确保某一个类只有一个实例，而且自行实例化并向整个系统提供这个实例，这个类成为单例类，它提供全局访问的方法。

单例模式有三个要点：
>
1.	某个类只能有一个实例; 
2.	它必须自省创建这个实例; 
3.	必须自行向整个系统提供这个实例。

结构图：
![单例模式](http://7xtw1r.com1.z0.glb.clouddn.com/1333305124_9327.gif)

角色：
>	singleton(单例):在单例类的内部实现只能生成一个实例，同时提供一个静态getInstance()工厂方法，让客户可以访问他的唯一实例。
	为防治外部对其实例化，将其构造函数设计为私有;单例类内部定义一个静态对象，作为外部共享的唯一实例。

代码实现

```PHP
class Singleton 
{

    //私有静态成员变量,存储唯一实例
    private static $instance;

    //为防止外部对其实例化,将构造函数设计为私有
    private function __construct () {}

    //单例类内部定义一个静态对象,作为外部共享的唯一实例
    public static function getInstance() 
    {
        if (self::$instance == null) {
            self::$instance = new self;
        }

        return self::$instance;
    }
    
    public static function display($arg) 
    {
        echo "This is Singleton pattern {$arg} !\n";
    }

    //防止被克隆
    private function __clone () {}

}
//客户端
$SingletonA = Singleton::getInstance();
// $SingletonB = Singleton::getInstance();
// $SingletonC = Singleton::getInstance();

$SingletonA::display('A');
// $SingletonB->display('B');

```


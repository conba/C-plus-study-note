# qt

## qt应用程序框架

```c++
#include "mywidget.h"
// QApplication应用程序类
// QT头文件没有.h
// 头文件和类名一样
// 前两个子目大写
#include <QApplication>
int main(int argc, char* argv[])
{
    // 应用程序只有一个应用程序类对象
    QApplication a(argc, argv);
    // MyWidget继承于QWidget, QWidget是一个窗口基类
    // MyWidget也是窗口类
    // w就是一个窗口
    MyWidget w;
    
    w.show(); 
    // 执行消息循环
    return a.exec();
}
```

## 项目文件

```c++
#-------------------------------------------------
#
# Project created by QtCreator 2021-04-08T18:18:59
#
#-------------------------------------------------

// 模块
QT       += core gui

// 为了兼容qt4
greaterThan(QT_MAJOR_VERSION, 4): QT += widgets

// 应用程序的名字
TARGET = 01

// 执行makefile的类型， app（根据代码生成的程序类型，app是应用程序，也可以是lib，也就是库）
TEMPLATE = app

# The following define makes your compiler emit warnings if you use
# any feature of Qt which as been marked as deprecated (the exact warnings
# depend on your compiler). Please consult the documentation of the
# deprecated API in order to know how to port your code away from it.
DEFINES += QT_DEPRECATED_WARNINGS

# You can also make your code fail to compile if you use deprecated APIs.
# In order to do so, uncomment the following line.
# You can also select to disable deprecated APIs only up to a certain version of Qt.
#DEFINES += QT_DISABLE_DEPRECATED_BEFORE=0x060000    # disables all the APIs deprecated before Qt 6.0.0


SOURCES += \
        main.cpp \
        widget.cpp

HEADERS += \
        widget.h
```

## 自定义信号和槽

```c++
class Teacher: public QObject
{
	Q_OBJECT
public:
    explicit Student(QObject *parent = 0);
signals:
	// 自定义信号， 写到signals下
    // 返回值是void，只需要声明，不需要实现
    // 可以后参数，可以重载
    void hungry(); // 饿了
public slots:
    // 早期QT版本，必须要写到public slots，也可以写到public或者全局下
    // 返回值void，需要声明，也需要实现
    // 可以有参数，可以发生重载
    void treat(); // 请客
};

// 手动触发信号
{
    emit object.hungry();
}
```


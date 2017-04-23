/*第二章是高级图形用户界面的设计，这一章会非常有意思。我们首先看一下高级用户界面的标准模版，来了解j2me基本的编程思想。

import javax.microedition.midlet.MIDlet;
import javax.microedition.lcdui.*;
//我们用“*”加载图形包中所有类，因为Display显示类，以及以后会学的提示Alert类、表单Form类、按钮Command类等都是该包的类，一个一个写会非常麻烦

public class Midlet extends MIDlet{

    //声明类的变量，因为这些变量不仅在startApp中用到，还可能在其他方法中用到，所以应该写到这里，让类中所有方法都能用
    Display display;
    
    //构造函数，常进行类的初始化操作，注意构造函数没有返回值类型！！！
    public Midlet()
    {
        //我们通过Display.getDisplay(this)获取对当前屏幕图像的控制权
        display=Display.getDisplay(this);}
    
    public void startApp(){
        //display.setCurrent(可以在屏幕上显示的类);
        //可以在屏幕上显示的类都是Screen类的子类，主要有提示框Alert类，表单Form类，文本界面TextBox类，列表ListBox类，当然你也可以自己写个继承于Screen类的类
        //display.setCurrent的意思就是让当前屏幕显示后面的类型
        }
    
    public void pauseApp(){}
    
    public void destroyApp(boolean unconditional){}
}

这就是用户界面的标准模版，我们在以后的每节中都会用到该模版。
其实，j2me的编程思路其实就是“填空（方法）游戏”。类库中的类其实就是很多模版，并在适当的位置给你留了空（方法），你编程时只需把这些空填起来即可，你也可以给继承你的类的类留空，让子类填空。这要比函数思想编程简单的多！

下面我们就开始正式学习提示Alert类。看代码：*/

import javax.microedition.midlet.MIDlet;
import javax.microedition.lcdui.*;

public class Midlet extends MIDlet{
    Display display;
    Alert alert;
    
    public Midlet()
    {
        display=Display.getDisplay(this);
        alert=new Alert("重要提示","我们在学j2me编程！",null,AlertType.INFO);
        //Alert中的参数分别是标题，提示内容，图片，提示类型。其中，图片应该是Image类的实例，这里设为null，表示不添加图片。
        //提示类型有以下几种：
        //AlertType.INFO信息提示
        //AlertType.ERROR错误提示
        //AlertType.CONFIGURATION确定提示
        //AlertType.WARNING警告提示
        //为了简单，Alert也可以这样使用：
        //alert=new Alert("我们在学j2me编程！");
        
        alert.setTimeout(5000);
        //设置为提示5秒后消失
        }
    
    public void startApp(){
        //当前屏幕设为提示框
        display.setCurrent(alert);
        }
    
    public void pauseApp(){}
    
    public void destroyApp(boolean unconditional){}
}

/*效果图见图片，本节也可以直接修改后缀为java进行编译。另外，教程包中也有做好的软件。另外，Alert类还有一些不常用的方法，如下：
int getDefaultTimeout();
//获取默认显示时长，另外上述程序不用setTimeout，也是显示默认时长
Image getImage();
//获取图像
String getString();
//获取字符串
int getTimeout();
//获取当前时长
AlertType getType();
//获取类型
void setImage(Image image);
//设置图片
void setString(String string);
//设置显示内容，这个可能有用

好了，这节就到这里！

作者：tengge 
QQ：930372551

*/
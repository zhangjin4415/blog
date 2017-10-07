title: Android开发
date: 2016-03-24 19:42:20
categories: "Android"
tags: "Android"
---
主要内容：
<!--more-->

第一章 环境搭建
===================
Windows10+jdk8+android studio
android studio下载http://www.android-studio.org/

第二章 Android基础知识
===================
1.介绍
------------
本阶段包含Android理论知识，是Android应用开发的根基，要想以后有更长足的提高，这部分的知识需要耐心学习实践,在这里你将渐渐熟悉Android的方方面面目录结构：
![image](img/android/1.png)
Manifests：配置目录AndroidManifest.xml默认内容如下：
```
<?xml version="1.0"encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
package="com.example.administrator.helloworld">
<application
android:allowBackup="true"//是否允许备份应用的数据，默认是true,当备份数据的时候，它的数据会被备份下来。如果设为false，那么绝对不会备份应用的数据，即使是备份整个系统。
android:icon="@mipmap/ic_launcher"//应用程序图标
android:label="@string/app_name"	//应用程序名字
android:theme="@style/AppTheme"><!--声明作为程序入口的Activity-->
<activity
android:name=".MainActivity"//Activity用来与用户交互的主要工具，是用户打开程序的初始界面.此处为引用程序默认启动的Activity
android:label="@string/app_name">
<intent-filter>//IntentFilter类表示Intent过滤器,大部分情况下,每一个component都会定义一个或多个IntentFilter,用于表明其可处理的Intent(Intent用于启动Activity,Service,以及BroadcastReceiver三种组件,同时还是组件之间通信的重要媒介。)。定义的方法:在<activity>,<receiver>,<service>元素中增加一个或多个<intent-filter>子元素//android.intent.action.MAIN决定一个应用程序最先启动那个组 件,android.intent.category.LAUNCHER决定应用程序是否显示在程序列表里(说白了就是是否在桌面上显示一个图标)
这两个属性组合情况：
第一种情况：有MAIN,无LAUNCHER，程序列表中无图标
原因：android.intent.category.LAUNCHER决定应用程序是否显示在程序列表里 
第二种情况：无MAIN,有LAUNCHER，程序列表中无图标
原因：android.intent.action.MAIN决定应用程序最先启动的Activity，如果没有Main，则不知启动哪个Activity，故也不会有图标出现
所以这两个属性一般成对出现。
如果一个应用中有两个组件intent-filter都添加了android.intent.action.MAIN和
android.intent.category.LAUNCHER这两个属性， 则这个应用将会显示两个图标， 写在前面的组件先运行。
<action android:name="android.intent.action.MAIN"/>//"android.intent.action.MAIN"这个action的filter都能通过action测试
<category android:name="android.intent.category.LAUNCHER"/>//如果一个intent没有定义category,则所有filter都可以通过category测试
</intent-filter>
</activity>
</application>
</manifest>
```
Res：资源文件夹
Layout：布局 menu：菜单 mipmap：图片 values：dimens尺寸 strings字符串 styles样式


2.Activity组件
---------------------
Activity是Android四大基本组件之一，可以通过setContentView方法绑定一个布局用于呈现界面与用户进行交互，是Android开发必不可少的学习内容
核心内容：1.认识Activity 2.Activity绑定视图3.启动Activity软件环境：Android Studio
(1)认识ActivityActivity就是界面字符串引用规范(string.xml)
```
android:label="@string/app_name"Strings.xml:<resources>
<string name="app_name">HelloWorld</string>
<string name="hello_world">Hello world!</string>
<string name="action_settings">Settings</string>
</resources>
```
java下的mainactivity：
```
protected void onCreate(Bundle savedInstanceState){
super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);//指定一个视图用来呈现视图，去掉则运行时没有界面
}
```
R.java：自动生成

(2)Activity绑定视图
修改activity绑定的布局：点击Layout右键单击->new->layout resource fille
![image](img/android/2.png)
生成的mylayout.xml内容如下：
```
<?xml version="1.0"encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
android:orientation="vertical"//vertical:垂直布局，如往里面拉按钮将垂直排布

android:layout_width="match_parent"
android:layout_height="match_parent">
</LinearLayout>
```
java下的mainactivity
```
protected void onCreate(Bundle savedInstanceState){
super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);//指定一个视图用来呈现视图，去掉则运行时没有界面,将setContentView(R.layout.activity_main);改为setContentView(R.layout.mylayout);就完成了
```

(3)启动Activity
本课讲解如何创建一个 Activity，如何在 Manifest 文件中对Activity进行配置，以及如何使用 startActivity 函数启动一个 Activity。
java目录下mainactivity如下：
```
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.mylayout);
}
```
res目录的layout下的mylayout.xml：
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">
//此处是一个按钮
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="启动另外一个Ativity"
        android:id="@+id/btnStartAnotherAty" />
</LinearLayout>
```
主程序mainactivity下：
```
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.mylayout);
    findViewById(R.id.btnStartAnotherAty).setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            
        }
    });
}
```
创建一个新的activity
注意：在java目录下也可以
![image](img/android/3.png)
新建的activity让其.xml输出如下
```
<TextView android:text="这是另外一个activity" android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```
Main中点击事件修改如下：
```
public void onClick(View v) {
startActivity(new Intent(MainActivity.this,AnotherAty.class));
}
```
如此可以运行：
点击按钮->进入另外一个界面，按返回键回到按钮界面
改成如下可以跳转到网页
```
public void onClick(View v) {
// startActivity(new Intent(MainActivity.this,AnotherAty.class));
     startActivity(new Intent(Intent.ACTION_VIEW, Uri.parse("http://jikexueyuan.com")));
 }
```

2.认识 Activity 的生命周期
------------------------
核心内容：查看帮助文档;Activity生命周期
(1)查看帮助文档
帮助文档：
如下选中Documentation for Android SDK进行下载
![image](img/android/4.png)
之后有以下文件，打开就可以
F:/Android/sdk/docs/develop/index.html
之后点击develop->reference   点击See all API packages. 搜索activity如下，随便点击一个，因为都是继承来自activity的
![image](img/android/5.png)
![image](img/android/6.png)
选中android.app.Activity下拉如下：activity的生命周期图
![image](img/android/7.png)
如何看开发文档(是一本书)
点击develop下的API Guides从上往下看，整个能够看完就会是一个安卓高手
![image](img/android/8.png)

(2)认识 Activity 的生命周期
在mainactivity中添加如下代码：
和帮助文档一样-----7个函数
```
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        System.out.print("onCreate");
    }

    @Override
    protected void onResume() {
        super.onResume();
        System.out.print("onResume");
    }

    @Override
    protected void onPause() {
        super.onPause();
        System.out.print("onPause");
    }

    @Override
    protected void onStop() {
        super.onStop();
        System.out.print("onStop");
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        System.out.print("onDestroy");
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        System.out.print("onRestart");
    }
@Override
    protected void onStart() {
        super.onStart();
        System.out.print("onStart");
    }

```
启动后效果如下：
![image](img/android/9.png)
Activity打开
![image](img/android/10.png)
启动模拟器之后执行oncreate onstart onresume 之后进入activity界面
按下home键进入桌面（activity界面消失）执行的是onpause onstop
点击最右边个键（呈现最近应用列表）：重新呈现activity界面，执行的函数是onrestart onstart onresume进入界面
按下后退键，界面消失，执行的是onpause,onstop,ondestory
点击最右边个键（呈现最近应用列表）：重新呈现activity界面，执行的函数是oncrate  onstart onresume进入界面,这是一个全新的生命周期
![image](img/android/11.png)

(3)在 Activity 跳转过程中的生命周期
新建一个activity，mainactivity（A）和anotherAty（B）
A代码如下：
Activity_main:添加按钮
```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="启动B Activity"
    android:id="@+id/btn_B_StartAnotherAty"
    android:layout_alignParentTop="true"
    android:layout_alignParentStart="true" />
```
Main.java
```
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        findViewById(R.id.btnStartAnotherAty).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                startActivity(new Intent(MainActivity.this,AnotherAty.class));
            }
        });

        System.out.print("A onCreate");
    }

    @Override
    protected void onResume() {
        super.onResume();
        System.out.print("A onResume");
    }

    @Override
    protected void onPause() {
        super.onPause();
        System.out.print("A onPause");
    }

    @Override
    protected void onStop() {
        super.onStop();
        System.out.print("A onStop");
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        System.out.print("A onDestroy");
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        System.out.print("A onRestart");
    }

    protected void onStart() {
        super.onStart();
        System.out.print("A onStart");
    }
```
B.java:
```
public class AnotherAty extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_another_aty);
        System.out.print("B onCreate");
    }

    @Override
    protected void onResume() {
        super.onResume();
        System.out.print("B onResume");
    }

    @Override
    protected void onPause() {
        super.onPause();
        System.out.print("B onPause");
    }

    @Override
    protected void onStop() {
        super.onStop();
        System.out.print("B onStop");
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        System.out.print("B onDestroy");
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        System.out.print("B onRestart");
    }

    protected void onStart() {
        super.onStart();
        System.out.print("B onStart");
    }
```
运行程序：
执行A onCreate , A onStart ,A onResume, A界面显示
点击A按钮，依次执行A onPouse,B onCreate,B onstart,B resume,A stop，显示B界面
此时用的B是不透明的，完全遮住了A，如果B透明，不完全遮住A呢？
在AndroidMainfest.xml下设置B，使他为一个对话框
代码如下：（我自己添加的有问题—应该是差什么包）
```
android:theme="@style/Base.Theme.AppCompat.Dialog"
```
极客学院如下：
![image](img/android/12.png)
此时执行A onPouse, B onCreate,B onstart,B onResume,此时B明A暗
在B外的其他空白处点击一下，B关闭，执行B onPause,.A onResume,B onStop,B onDestory.A显示

3.在 Activity 之间传递参数
--------------------------
核心内容：在 Activity 之间传递简单数据;在 Activity 之间传递复杂数据;在 Activity 之间传递自定义值对象
(1)传递简单数据
设置activity_another_aty.xml如下：
设置输出框id=tv
```
<TextView android:text="这是另外一个activity" android:layout_width="wrap_content"
    android:layout_height="wrap_content" android:id="@+id/tv"/>
```
Activity_main.xml下加按钮
```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="启动另一个Activity"
    android:id="@+id/btn_B_StartAnotherAty"
    android:layout_alignParentTop="true"
    android:layout_alignParentStart="true" />
```
设置mainactivity.java
```
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
    findViewById(R.id.btn_B_StartAnotherAty).setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            Intent i = new Intent(MainActivity.this, AnotherAty.class);
            i.putExtra("data","hello,me");//传参数
            startActivity(i);
        }
    });
}
```
anotheraty.java中获取：
```
public class AnotherAty extends Activity {

    private TextView tv;//访问已经写好的Textview---输出框
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_another_aty);

        Intent i = getIntent();
        tv = (TextView) findViewById(R.id.tv);//findViewById返回为view类型，需要强转
        tv.setText(i.getStringExtra("data"));        //为输出框设置字符串(getStringExtra("data")-获取到一个字符串的数据,名字是data)
    }
```
如上运行之后点击按钮就可以跳转到另外一个界面：输出hello，me

(2)传递数据包Bundle
对上面的代码进行一定的修改就可以
Mainactivity.java
```
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
    findViewById(R.id.btn_B_StartAnotherAty).setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            Intent i = new Intent(MainActivity.this, AnotherAty.class);
           // i.putExtra("data","hello,me");//传参数  名字是data 值是hello,me
            Bundle b = new Bundle();//数据包
            b.putString("name","liming");
            b.putInt("age", 2);
            b.putString("sex", "man");
            i.putExtras(b);//区别于putExtra
            startActivity(i);
        }
    });
}
```
AnotherAty.java
```
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_another_aty);

    Intent i = getIntent();
     tv = (TextView) findViewById(R.id.tv);
   // tv.setText(i.getStringExtra("data"));        //为输出框设置字符串(getStringExtra("data")-获取到一个字符串的数据,名字是data)
    Bundle data = i.getExtras();
    tv.setText(String.format("name=%s,age=%d,sex=%s,name1=%s",data.getString("name"),data.getInt("age"),data.getString("sex","woman"),data.getString("name1","张")));
    //name1再包里面没有输出为这里设置的默认值，sex传入有值，将不再用这里设置的默认值
}
```
效果图
![image](img/android/13.png)
![image](img/android/14.png)
当然，也可以用putextra(String name,Bundle value)传递Bundle
Mainactivity.java
```
public void onClick(View v) {
    Intent i = new Intent(MainActivity.this, AnotherAty.class);
   // i.putExtra("data","hello,me");//传参数  名字是data 值是hello,me
    Bundle b = new Bundle();//数据包
    b.putString("name","liming");
    b.putInt("age", 2);
    b.putString("sex", "man");
   // i.putExtras(b);//区别于putExtra
    i.putExtra("data",b);
    startActivity(i);
}
```
AnotherAty.java
```
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_another_aty);

    Intent i = getIntent();
     tv = (TextView) findViewById(R.id.tv);
   // tv.setText(i.getStringExtra("data"));        //为输出框设置字符串(getStringExtra("data")-获取到一个字符串的数据,名字是data)
  //  Bundle data = i.getExtras();   //getExtras()传参数时接收函数
    Bundle data = i.getBundleExtra("data");//getExtra()传包时接收函数
    tv.setText(String.format("name=%s,age=%d,sex=%s,name1=%s",data.getString("name"), data.getInt("age"),data.getString("sex","woman"),data.getString("name1","张")));
    //name1再包里面没有输出为这里设置的默认值，sex传入有值，将不再用这里设置的默认值
}
```
运行效果同上

(3)传递值对象
值对象：自定义的有数据类型的对象
如传递一个数据类型user
新建一个user.java类：
```
public class User {
    private String name;
    private int age;

    public User(int age, String name) {
        this.age = age;
        this.name = name;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
}
```
mainactivity.java
```
i.putExtra("User",new User("张三丰",25));//提示错误！
```
![image](img/android/15.png)
User需要实现parcelable或者Serializable序列化
修改User
```
import java.io.Serializable;

/**
 * Created by zhang on 2016/1/11.
 */
public class User implements Serializable{
    private String name;
    private int age;

    public User( String name,int age) {
        this.age = age;
        this.name = name;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
}
```
mainactivity.java传参数：
```
        public void onClick(View v) {
                Intent i = new Intent(MainActivity.this, AnotherAty.class);
               // i.putExtra("data","hello,me");//传参数  名字是data 值是hello,me
//                Bundle b = new Bundle();//数据包
//                b.putString("name","liming");
//                b.putInt("age", 2);
//                b.putString("sex", "man");
//               // i.putExtras(b);//区别于putExtra
//                i.putExtra("data",b);
                i.putExtra("User",new User("张三丰",25));
                startActivity(i);
            }
```
anotheraty.java获取参数：
```
protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_another_aty);

        Intent i = getIntent();
         tv = (TextView) findViewById(R.id.tv);
       // tv.setText(i.getStringExtra("data"));        //为输出框设置字符串(getStringExtra("data")-获取到一个字符串的数据,名字是data)
      //  Bundle data = i.getExtras();   //getExtras()传参数时接收函数
//        Bundle data = i.getBundleExtra("data");//getExtra()传包时接收函数
//        tv.setText(String.format("name=%s,age=%d,sex=%s,name1=%s",data.getString("name"), data.getInt("age"),data.getString("sex","woman"),data.getString("name1","张")));
        //name1再包里面没有输出为这里设置的默认值，sex传入有值，将不再用这里设置的默认值

        //取User
        User user= (User)i.getSerializableExtra("User");
//注意：传参获取必须名字一样：getSerializableExtra("User")不能用小写的"user",因为传参用的大写i.putExtra("User",new User("张三丰",25));否则编译通过，不能运行
tv.setText(String.format("user.info(name=%s,age=%d)",user.getName(), user.getAge()));
    }
```
运行点击按钮时显示：user.info(name=张三丰,age=25)

但是与parcelable相比，Serializable效率低
Parcelable是安卓的，速度快，但是要实现两个方法
describeContents() 
writeToParcel(Parcel dest, int flags)需要手动写数据 执行过程中会自动执行到这个函数
再创建一个泛型
Parcelable具体实现如下：
User.java
```
import android.os.Parcel;
import android.os.Parcelable;

//import java.io.Serializable;

/**
 * Created by zhang on 2016/1/11.
 */
//public class User implements Serializable{
public class User implements Parcelable{
    private String name;
    private int age;

    public User( String name,int age) {
        this.age = age;
        this.name = name;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public int describeContents() {
        return 0;
    }

    @Override
    public void writeToParcel(Parcel dest, int flags) {
        dest.writeString(getName());//这里怎么写的Creator中怎么读 多个string时可以用Bundle
        dest.writeInt(getAge());
    }

    //创建一个泛型
    public static final Creator<User> CREATOR = new Creator<User>() {
        @Override
        public User createFromParcel(Parcel source) {
            return new User(source.readString(),source.readByte());
        }

        @Override
        public User[] newArray(int size) {
            return new User[size];
        }
    };
}
```
mainactivity.java
```
public void onClick(View v) {
                Intent i = new Intent(MainActivity.this, AnotherAty.class);
               // i.putExtra("data","hello,me");//传参数  名字是data 值是hello,me
//                Bundle b = new Bundle();//数据包
//                b.putString("name","liming");
//                b.putInt("age", 2);
//                b.putString("sex", "man");
//               // i.putExtras(b);//区别于putExtra
//                i.putExtra("data",b);
                i.putExtra("User",new User("张三丰",25));
                startActivity(i);
            }
```
anotheraty.java
```
protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_another_aty);

        Intent i = getIntent();
         tv = (TextView) findViewById(R.id.tv);
       // tv.setText(i.getStringExtra("data"));        //为输出框设置字符串(getStringExtra("data")-获取到一个字符串的数据,名字是data)
      //  Bundle data = i.getExtras();   //getExtras()传参数时接收函数
//        Bundle data = i.getBundleExtra("data");//getExtra()传包时接收函数
//        tv.setText(String.format("name=%s,age=%d,sex=%s,name1=%s",data.getString("name"), data.getInt("age"),data.getString("sex","woman"),data.getString("name1","张")));
        //name1再包里面没有输出为这里设置的默认值，sex传入有值，将不再用这里设置的默认值

        //取User
//        User user= (User)i.getSerializableExtra("User");//用什么方法实现的就用什么方法获取
        //注意：传参获取必须名字一样：getSerializableExtra("User")不能用小写的"user",因为传参用的大写i.putExtra("User",new User("张三丰",25));否则编译通过，不能运行
       User user= i.getParcelableExtra("User");//用什么方法实现的就用什么方法获取
        tv.setText(String.format("user.info(name=%s,age=%d)",user.getName(), user.getAge()));
    }
```
运行效果与上面一样

(4)获取 Activity 的返回参数
Activity_another_aty设置垂直排列并设置一个输入框和按钮，并在对应java中进行设置
Activity_main中添加一个输出框textview,对应main.Java中进行定义
Activity_Main.xml:
```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools" android:layout_width="match_parent"
    android:orientation="vertical"
    android:layout_height="match_parent" android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    android:paddingBottom="@dimen/activity_vertical_margin" tools:context=".MainActivity">

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="启动另一个Activity"
        android:id="@+id/btn_B_StartAnotherAty"
        android:layout_alignParentTop="true"
        android:layout_alignParentStart="true" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="New Text"
        android:id="@+id/textView" />

</LinearLayout>
```
Activity_another_aty.xml:
```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools" android:layout_width="match_parent"
    android:layout_height="match_parent" android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    android:paddingBottom="@dimen/activity_vertical_margin"

    android:orientation="vertical"
    tools:context="com.example.zhang.helloworld.AnotherAty">

    <TextView android:text="这是另外一个activity" android:layout_width="wrap_content"
        android:layout_height="wrap_content" android:id="@+id/tv"/>

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/editText" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Send Back"
        android:id="@+id/button" />


</LinearLayout>
```
Main.java
```
public class MainActivity extends Activity {

    private TextView textView;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        textView = (TextView) findViewById(R.id.textView);

        findViewById(R.id.btn_B_StartAnotherAty).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent i = new Intent(MainActivity.this, AnotherAty.class);
               // i.putExtra("data","hello,me");//传参数  名字是data 值是hello,me
//                Bundle b = new Bundle();//数据包
//                b.putString("name","liming");
//                b.putInt("age", 2);
//                b.putString("sex", "man");
//               // i.putExtras(b);//区别于putExtra
//                i.putExtra("data",b);
                i.putExtra("User", new User("张三丰", 25));
//                startActivity(i);//因为要接收传回的参数，所以不能再用这个函数
                startActivityForResult(i,0);//0---请求的代码：请求的代码传过去再传回来，可以用于代表此次请求的意义是什么
            }
        });
    }

    //重写函数
    @Override
    //此函数可以获取到请求码，也可以获取到结果码
    //data对应的是传进来的setResult(1,i);中的i
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        textView.setText("另一个activity返回的是"+data.getStringExtra("data"));
    }
```
another_aty.java
```
package com.example.zhang.helloworld;

import android.app.Activity;
import android.content.Intent;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

public class AnotherAty extends Activity {

    private  TextView tv;
    private EditText editText;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_another_aty);

        Intent i = getIntent();
        tv = (TextView) findViewById(R.id.tv);
        editText= (EditText) findViewById(R.id.editText);//初始化
        // tv.setText(i.getStringExtra("data"));        //为输出框设置字符串(getStringExtra("data")-获取到一个字符串的数据,名字是data)
        //  Bundle data = i.getExtras();   //getExtras()传参数时接收函数
//        Bundle data = i.getBundleExtra("data");//getExtra()传包时接收函数
//        tv.setText(String.format("name=%s,age=%d,sex=%s,name1=%s",data.getString("name"), data.getInt("age"),data.getString("sex","woman"),data.getString("name1","张")));
        //name1再包里面没有输出为这里设置的默认值，sex传入有值，将不再用这里设置的默认值

        //取User
//        User user= (User)i.getSerializableExtra("User");//用什么方法实现的就用什么方法获取
        //注意：传参获取必须名字一样：getSerializableExtra("User")不能用小写的"user",因为传参用的大写i.putExtra("User",new User("张三丰",25));否则编译通过，不能运行
        User user= i.getParcelableExtra("User");//用什么方法实现的就用什么方法获取
        tv.setText(String.format("user.info(name=%s,age=%d)",user.getName(), user.getAge()));

        findViewById(R.id.button).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent i=new Intent();
                i.putExtra("data",editText.getText().toString());
                setResult(1, i);//设置返回值setResult(状态码，值)
                finish();//直接把当前的activity给结束掉
            }
        });
    }
    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_another_aty, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();
        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            return true;
        }

        return super.onOptionsItemSelected(item);
    }
}
```
运行效果：输出返回值
![image](img/android/16.png)

4.Android 中 Activity 启动模式
------------------------
核心内容：Activity Standard 启动模式;Activity SingleTop 启动模式;Activity SingleTask 启动模式;Activity SingleInstance 启动模式
(1)标准启动模式
标准启动模式就是默认的启动模式
Activity_main.xml:
```
<TextView android:text="@string/hello_world" android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:id="@+id/tv"
/>
```
Mainactivity.java:
```
private TextView tv;
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    tv= (TextView) findViewById(R.id.tv);
    //TaskID----任务ID    Current activity id：当前activity的实例ID
    tv.setText(String.format("TaskID:%d\n,Current activity id:%s",getTaskId(),toString()));
}
```
运行效果
![image](img/android/17.png)
再加一个button之后
Activity_main.xml:
```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools" android:layout_width="match_parent"
    android:layout_height="match_parent" android:paddingLeft="@dimen/activity_horizontal_margin"
    android:orientation="vertical"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    android:paddingBottom="@dimen/activity_vertical_margin" tools:context=".MainActivity">

    <TextView android:text="@string/hello_world" android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/tv"
    />
<!-- android:textAllCaps="false":取消默认的全部大写 -->
    <Button
        android:textAllCaps="false"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="启动mainactivity"
        android:id="@+id/btnStartSelf" />

</LinearLayout>
```
Mainactivity.java:
```
private TextView tv;
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    tv= (TextView) findViewById(R.id.tv);
    //TaskID----任务ID    Current activity id：当前activity的实例ID
    tv.setText(String.format("TaskID:%d\n,Current activity id:%s",getTaskId(),toString()));

    findViewById(R.id.btnStartSelf).setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            startActivity(new Intent(MainActivity.this,MainActivity.class));
        }
    });
}
```
运行效果
![image](img/android/18.png)
点击按钮后taskid没有变，而当前activity的id改变
任务栈：启动的第一个实例放入其中，第2,3…个实例也是放入其中
按后退键可以弹出栈点的实例，呈现上一个activity的实例
在Androidmanifest.xml中可以进行启动模式配置
默认的是stadard
![image](img/android/19.png)

(2)SingleTop 模式
把上面的Androidmanifest.xml中配置改为SingleTop后运行
![image](img/android/20.png)
此时点击按钮显示没有任何改变
再建一个activity测试
注意：同一个文件设置ID不能一样，不同的文件设置ID可以相同
程序如下：
Activity_main.xml与activity_baty.xml完全一样
```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools" android:layout_width="match_parent"
    android:layout_height="match_parent" android:paddingLeft="@dimen/activity_horizontal_margin"
    android:orientation="vertical"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    android:paddingBottom="@dimen/activity_vertical_margin" tools:context=".MainActivity">

    <TextView android:text="@string/hello_world" android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/tv"
    />
<!-- android:textAllCaps="false":取消默认的全部大写 -->
    <Button
        android:textAllCaps="false"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="启动mainactivity"
        android:id="@+id/btnStartMain" />

    <Button
        android:textAllCaps="false"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="启动BAty"
        android:id="@+id/btnStartBty" />

</LinearLayout>
```
Mainactivity.java
```
public class MainActivity extends Activity {

    private TextView tv;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        tv= (TextView) findViewById(R.id.tv);
        //TaskID----任务ID    Current activity id：当前activity的实例ID
        tv.setText(String.format("TaskID:%d\n,Current activity id:%s",getTaskId(),toString()));

        findViewById(R.id.btnStartMain).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                startActivity(new Intent(MainActivity.this, MainActivity.class));
            }
        });

        findViewById(R.id.btnStartBty).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                startActivity(new Intent(MainActivity.this, BAty.class));
            }
        });
    }
```
BAty.java
```
public class BAty extends Activity {
    private TextView tv;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_baty);

        tv= (TextView) findViewById(R.id.tv);
        tv.setText(String.format("TaskID:%d\n,Current activity id:%s", getTaskId(), toString()));

        findViewById(R.id.btnStartMain).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                startActivity(new Intent(BAty.this, MainActivity.class));
            }
        });

        findViewById(R.id.btnStartBty).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                startActivity(new Intent(BAty.this, BAty.class));
            }
        });
    }
```
效果如下
![image](img/android/21.png)
在主界面（main界面）点击跳转到自己, taskid不变，实例ID不变
在主界面（main界面）点击跳转到Bty, taskid不变，实例ID改变
在Bty界面点击跳转到main界面，taskid不变，实例ID改变，而且与前次的实例ID不一样
在Bty界面点击跳转到自己界面，taskid不变，实例ID改变
点击后退可以一直退

(3)SingleTask 与 SingleInstance 模式
将androidmainfest.xml设置为singletask
```
android:launchMode="singleTask" >
```
其他与2.4.2相同，运行如下
在主界面（main界面）点击跳转到自己, taskid不变，实例ID不变
在主界面（main界面）点击跳转到Bty, taskid不变，实例ID改变
在Bty界面点击跳转到main界面，taskid不变，实例ID改变，而且与前次的实例ID一样
在Bty界面点击跳转到自己界面，taskid不变，实例ID改变
点击后退退到main界面，在main界面点击后退直接退出
Main activity永远只有一个

将androidmainfest.xml设置为SingleInstance时main与Bty不是同一个栈
在主界面（main界面）点击跳转到自己, taskid不变，实例ID不变
在主界面（main界面）点击跳转到Bty, taskid改变，实例ID改变
在Bty界面点击跳转到main界面，taskid改变，实例ID改变，而且与前次的实例ID一样taskid也是相同
在Bty界面点击跳转到自己界面，taskid不变，实例ID改变
在一个界面点击后退后退到的界面如果是栈顶，再点击后退这个栈退出，如果有退到另外一个栈，则显示另外一个栈，点击后退如果是这个栈的栈顶则直接退出！


5.在 Android 中 Intent 的概念及应用
-------------------------------
核心内容：隐式 Intent;显式 Intent
(1)显式Intent
分别新建一个类和一个activity,并将他们绑定，需要在androidmainfest.xml注册才能用！最后进行intent配置。
Activity_main.xml
```
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools" android:layout_width="match_parent"
    android:layout_height="match_parent" android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    android:paddingBottom="@dimen/activity_vertical_margin" tools:context=".MainActivity">

    <TextView android:text="@string/hello_world" android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/textView2" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="startMyAty"
        android:id="@+id/btnStartMyAty"
        android:layout_below="@+id/textView2"
        android:layout_toEndOf="@+id/textView2"
        android:layout_marginTop="81dp" />

</RelativeLayout>
```
MyAty.java
```
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.btnStartMyAty).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                startActivity(new Intent(MainActivity.this,MyAty.class));//这是一个显示的Intent,因为显示的写出了被启动的MyAty.class
            }
        });
    }
```
myAty.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="New Text"
        android:id="@+id/textView" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="New Button"
        android:id="@+id/button" />
</LinearLayout>
```
MyAty.java
```
import android.app.Activity;
import android.os.Bundle;

/**
 * Created by zhang on 2016/1/11.
 */
public class MyAty extends Activity {
    //重写oncreate函数
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.myaty);//将这个activity与视图myaty绑定
    }
}
```
androidmainfest.xml
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.zhang.learnintent" >

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme" >
        <activity
            android:name=".MainActivity"
            android:label="@string/app_name" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <!-- 注册MyAty,前面加一点是因为程序运行时会加直接在package="com.example.zhang.learnintent"后面 也可以com.example.zhang.learnintent.MyAty -->
        <activity android:name=".MyAty"/>
        <!--<activity android:name="com.example.zhang.learnintent.MyAty"/>-->
    </application>

</manifest>
```
运行效果：点击按钮跳转到另外一个界面

(2)隐式 Intent
androidmainfest.xml中指定category，category为DEFAULT时，其行为方式为activity
action可以是任意的字符串，启动的时候根据字符串启动就可以啦，在main.java中用这个字符串（不能有中文）就可以
改动androidmainfest.xml和main.java，其他不变
androidmainfest.xml
```
<activity android:name=".MyAty">
    <intent-filter>
        <category android:name="android.intent.category.DEFAULT"/><!-- android.intent.category.DEFAULT此处不能全部用大写 -->
        <action android:name="acdsndslvdjsldvms.a"/>
    </intent-filter>
</activity>
```
main.java
```
public void onClick(View v) {
    startActivity(new Intent("acdsndslvdjsldvms.a"));//这是一个显示的Intent,因为显示的写出了被启动的MyAty.class
}
```
运行效果与上面的一样
但是上面用随意的字符串可读性太差，可以用约定成俗的格式com.zhang.LearnIntent.intent.action.MyAty,一看就知道启动哪个activity
这太长，还是很难记，一般在被启动的activity（MyAty.java）中添加常量

androidmainfest.xml
```
<activity android:name=".MyAty">
    <intent-filter>
        <category android:name="android.intent.category.DEFAULT"/><!-- android.intent.category.DEFAULT此处不能全部用大写 -->
        <action android:name="com.zhang.LearnIntent.intent.action.MyAty"/>
    </intent-filter>
</activity>
```

MyAty.java
```
public class MyAty extends Activity {

    public static final String ACTION = "com.zhang.LearnIntent.intent.action.MyAty";
    //重写oncreate函数
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.myaty);//将这个activity与视图myaty绑定
    }
}
```
main.java
```
public void onClick(View v) {
    startActivity(new Intent(MyAty.ACTION));
}
```
运行效果与上面的一样


不同应用间通过ACTION启动
再创建一个新的项目App1用new Module---在同一个界面显示
App1中：
Main.xml
```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Start MyAty from App1"
    android:id="@+id/btnStartMyAty"
    android:layout_below="@+id/textView"
    android:layout_alignParentStart="true"
    android:layout_marginTop="52dp" />
```
Main.java
```
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    findViewById(R.id.btnStartMyAty).setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            startActivity(new Intent("com.zhang.LearnIntent.intent.action.MyAty"));
        }
    });
}
```
通过软件App1可以启动跳转到LearnIntent的界面MyAty
如果不允许其他应用访问我应用的activity,只允许自己访问，该怎么配置呢？
只需要将该应用的activity的androidmainfest.xml进行如下配置，则其他应用不能访问这个activity
```
<activity android:name=".MyAty" android:exported="false">
```
？？？但是不知道为啥，我的加了这个语句还是可以访问！

(3)Intent 过滤器相关选项
多个activity的intent一样会出现什么情况呢？
没有去掉MyAty的android:exported="false"时，会直接显示MyAty1
去掉后会如下，让你自己选择
![image](img/android/22.png)
可以选择just once或者always
选择always后下次将默认启动这项，取消需要在设置里面弄
将软件LearnIntent拉到info里面，点击CLEAR DEFAULTS将默认设置都清掉，则可以重新选择（我的模拟器不行（清后还是默认的）—应该是安卓版本太低）
![image](img/android/23.png)
过滤器里面还有一个属性data
在MyAty1下加入data项如下
```
<activity
    android:name=".MyAty1"
    android:label="@string/title_activity_my_aty1" >
    <intent-filter>
        <category android:name="android.intent.category.DEFAULT" />
        <action android:name="com.zhang.LearnIntent.intent.action.MyAty" />
        <data android:scheme="app"/>
    </intent-filter>
</activity>
```
在APP1中如何找到指定的activity呢？
两个activity：MyAty是通过默认配置，而MyAty1是通过添加schme(指明的协议是”app”)
Data属性下还有很多常用的属性，自己下来看
App1-main.java中
```
public void onClick(View v) {
    startActivity(new Intent("com.zhang.LearnIntent.intent.action.MyAty", Uri.parse("app://hello")));// app://后面参数任意，不一定是hello
}
```
如此，启动App1后点击按钮直接到MyAty1


(4) 通过浏览器链接启动本地 Activity
先建一个activity,再到再mainfest.xml下配置activity
Localaty.xml
```
<TextView android:text="这是浏览器链接的本地的activity" android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```
mainfest.xml
```
<activity
    android:name=".LocalAty"
    android:label="@string/title_activity_local_aty" >
    <intent-filter>
        <category android:name="android.intent.category.BROWSABLE"/>  <!-- 可以被浏览器启动配置 -->
        <category android:name="android.intent.category.DEFAULT"/>

        <action android:name="android.intent.action.VIEW"/>
        <data android:scheme="app"/>
    </intent-filter>
</activity>
```
配置完成后，写一个浏览器的页面------用软件WebStorm开发，当然也可以用任何html编辑软件
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>App</title>

    <!-- 调整文字的大小 -->
    <style>
        a{
            font-size: 50pt;
        }
    </style>

</head>
<body>
<a href="app://hello">Launch My APP</a>
</body>
</html>
```
直接在电脑浏览器上无法访问到app,因为不能处理APP协议
![image](img/android/24.png)

在手机上打开：手机用本地地址：10.0.2.2
注意要加端口，地址全名：http：//10.0.2.2:63343/App/index.html
如下所示
![image](img/android/25.png)
如此实现了浏览器打开APP的activity,但是如何接收到参数呢？
通过（Android.net下的）Uri.可以获取信息
![image](img/android/26.png)
Localaty.java
```
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_local_aty);

    Uri uri = getIntent().getData();
    System.out.println(uri);// System.out.print(uri)会由于缓存原因没有输出，所以用println
}
```
安装APP，打开网页点击打开activity,输出信息：
![image](img/android/27.png)

6.Android 中 Context 的理解及使用
----------------------------------
Context 是 Android 中一个非常重要的概念，用于访问全局信息，几乎所有的基础组件都继承自 Context，理解 Context 对于学习 Android 四大基本组件非常有帮助。
核心内容：理解 Context;理解 Application
(1) Context 的作用
Context:用于访问全局信息（如用于程序的资源：图片，字符串）的接口，如activity也是继承自Context
那么如何通过context进行资源的访问呢？
![image](img/android/28.png)
TextView里面最少要有一个context.而activity继承自context,所以可以用activity
Main.java
```
public class MainActivity extends Activity {

    private TextView tv;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
//        setContentView(R.layout.activity_main);
        tv = new TextView(MainActivity.this);//不是内部类，MainActivity.this可以直接用this
        tv.setText("hello android");
        setContentView(tv);
    }
```
运行输出字符串hello android
可以获取任意的字符串资源如
```
tv.setText(R.string.app_name);//app_name在string.xml中，为LearnContext
```
图片资源
```
    ImageView iv = new ImageView(this);
    iv.setImageResource(R.mipmap.ic_launcher);
    setContentView(iv);
```
运行如下：
![image](img/android/29.png)

(2)Application 的用途
信息共享
创建一个类APP继承自Application
之后打开androidmainfest.xml配置
```
<application
    android:name=".App"
```
如此则自定义了一个安卓的Application, Application才是一个真正的全局上下文对象
在main.java中通过getApplicationContext()就可以获取到Application的全局的对象
下面实现一个全局共享的数据
App.java中写一个字符串，在为他写一个set,get方法，代码如下
```
import android.app.Application;

/**
 * Created by zhang on 2016/1/12.
 */
public class App extends Application {
    private String textdata = "default";

    public String getTextdata() {
        return textdata;
    }

    public void setTextdata(String textdata) {
        this.textdata = textdata;
    }
}
```
新建一个main2.java继承自activity
重写oncreate函数
```
import android.app.Activity;
import android.os.Bundle;
/**
 * Created by zhang on 2016/1/12.
 */
public class Main2 extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
    }
}
```
打开androidmainfest.xml添加上这个activity
复制mainactivity的配置让这个activity也是默认启动(category.LAUNCHER)
Label一个设置main1,一个main2
```
<activity
    android:name=".MainActivity"
    android:label="Main1" >
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />

        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
<activity android:name=".Main2" android:label="Main2">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />

        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```
安装后发现有两个软件，一个main1启动的是main1，另一个main2启动的是main2
下面让他们实现数据共享
新建linearlayout,如下main1,main2，删掉原来的mainactivity.xml
![image](img/android/30.png)
两个activity分别绑定两个视图
Mainactivity.java
```
setContentView(R.layout.main1);
```
main2.java
```
setContentView(R.layout.main2);
```

main1.activity中放入输出输入文本框和按钮，main2.activity与main1相同
```
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="New Text"
    android:id="@+id/textView"
    android:layout_weight="0.03" />

<EditText
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:id="@+id/editText" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="保存"
    android:id="@+id/btnSave"
    android:layout_weight="0.03" />
```
保存和读取Application数据中的信息
Mainactivity.java与main2.java一样
```
public class Main2 extends Activity {
    private TextView textView;
    private EditText editText;

    @Override
    protected void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);
        setContentView(R.layout.main2);
        textView = (TextView) findViewById(R.id.textView);
        editText = (EditText) findViewById(R.id.editText);
        textView.setText("共享的数据是：" + getApp().getTextdata());

        findViewById(R.id.btnSave).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                ((App) getApplicationContext()).setTextdata(editText.getText().toString());
                textView.setText("共享的数据是：" + editText.getText().toString());
            }
        });
    }

    public App getApp() {
        return (App) getApplicationContext();
    }
}
```
main1运行：点击输入保存看到共享的数据
![image](img/android/31.png)
退出main1打开main2如下：成功读取数据，同样，在main2中改的在main1中可以收到
![image](img/android/32.png)

(3) Application 生命周期
App.java
```
public class App extends Application {
    private String textdata = "default";

    public String getTextdata() {
        return textdata;
    }

    public void setTextdata(String textdata) {
        this.textdata = textdata;
    }

    @Override//创建
    //比被启动的activity的oncreate先执行--方便做一些初始化操作
    public void onCreate() {
        super.onCreate();
        System.out.println("App oncreate()");
    }

    @Override//结束----一般情况不执行，只是模拟情况下执行
    public void onTerminate() {
        super.onTerminate();
        System.out.println("App onTerminate()");
    }

    @Override//低内存时执行
    public void onLowMemory() {
        super.onLowMemory();
        System.out.println("App onlowmemory()");
    }

    @Override//程序进行内存清理时执行
    public void onTrimMemory(int level) {
        super.onTrimMemory(level);
    }

    @Override//配置改变时执行
    public void onConfigurationChanged(Configuration newConfig) {
        super.onConfigurationChanged(newConfig);
    }

}
```
mainactivity.java
```
System.out.println("mainactivity oncreate()");
```
Main2.java
```
System.out.println("main2 oncreate()");
```
运行：不管启动哪个activity，app.java的oncreate函数先会执行
![image](img/android/33.png)
关闭main1后（不然好像不会再次启动app.java的oncreate函数）启动main2
![image](img/android/34.png)

7.认识 Android Service
--------------------------
课程背景：Service 是 Android 四大基本组件之一，是无界面的应用程序，可以长期在后台运行，在实际工作中非常重要，比如接收推送消息、在锁屏状态下侦听传感器信息。
核心内容：启动Service;绑定Service

(1) 使用 Service
新建一个项目learnservice
Java包下new->server->server 产生myserver.java
Exported:是否导出（向外界公开）   enabled：是否启用
如何启用呢？
myserver.java没动
Main.xml加入按钮
```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="启动服务"
    android:id="@+id/btnStartService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="停止服务"
    android:id="@+id/btnEndService" />
```
Main.java
```
public class MainActivity extends Activity {

    private Intent intent;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        intent = new Intent(MainActivity.this,MyService.class);

        findViewById(R.id.btnStartService).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
               // startService(new Intent(MainActivity.this, MyService.class));//启动服务
                startService(intent);
            }
        });

        findViewById(R.id.btnEndService).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
               // stopService(new Intent(MainActivity.this,MyService.class));//服务的操作在一个实例中只有一个，停止的是上面启动的
                stopService(intent);
            }
        });
    }
```
启动运行：
运行先不操作，按中间键进入桌面，查看setting->APPS（应用）->running(所有正在运行的程序) 能够看到正在运行的服务
点击按钮开始，再到上面地方看，发现多了一个这个项目的service（一个进程，一个服务）
点击停止服务，发现服务没有了

写一个实例：让他不断的在后台输出语句
Myservice.java
```
@Override
//外界执行startservice后会执行这个函数
public int onStartCommand(Intent intent, int flags, int startId) {
    //创建一个线程，让他不断输出语句
    new Thread(){
        @Override
        public void run() {
            super.run();
            while(true) {
                System.out.println("服务正在运行...");
                //休眠1S
                try {
                    sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }.start();

    return super.onStartCommand(intent, flags, startId);
}
```
运行点击启动服务
每隔1s后台不断输出 服务正在运行...
按左边个键退出程序服务仍然执行

(2) 绑定 Service
Main.xml
```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="启动服务"
    android:id="@+id/btnStartService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="停止服务"
    android:id="@+id/btnEndService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="绑定服务"
    android:id="@+id/btnBindService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="解除绑定服务"
    android:id="@+id/btnUnbindService" />
```
Main.java
```
// implements View.OnClickListener------实现接口后可以把
//findViewById(R.id.btnStartService).setOnClickListener(new View.OnClickListener() {
//@Override
//public void onClick(View v) {
//        // startService(new Intent(MainActivity.this, MyService.class));//启动服务
//        startService(intent);
//        }
//        });
//改为 findViewById(R.id.btnBindService).setOnClickListener(this);

public class MainActivity extends Activity implements View.OnClickListener, ServiceConnection {
    private Intent intent;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        intent = new Intent(MainActivity.this,MyService.class);
        findViewById(R.id.btnStartService).setOnClickListener(this);
        findViewById(R.id.btnEndService).setOnClickListener(this);
        findViewById(R.id.btnBindService).setOnClickListener(this);
        findViewById(R.id.btnUnbindService).setOnClickListener(this);
    }

    @Override
    public void onClick(View v) {
        switch (v.getId())
        {
            case R.id.btnStartService:
                startService(intent);
                break;
            case R.id.btnEndService:
                stopService(intent);
                break;
            case R.id.btnBindService:
                bindService(intent,this, Context.BIND_AUTO_CREATE);//bindService(intent；服务连接:听服务状态。让this实现监听service，同时实现下面两个函数；常量);
                break;
            case R.id.btnUnbindService:
                unbindService(this);
                break;
        }
    }

    @Override
    //标识服务连接成功
    public void onServiceConnected(ComponentName name, IBinder service) {
        System.out.println("Service connected!");
    }

    @Override
    public void onServiceDisconnected(ComponentName name) {

    }

```
Myservice.java
```
public class MyService extends Service {
    public MyService() {
    }

    @Override
    public IBinder onBind(Intent intent) {
        // TODO: Return the communication channel to the service.
       // throw new UnsupportedOperationException("Not yet implemented");
        return new Binder();
    }
    @Override
    //外界执行startservice后会执行这个函数
    public int onStartCommand(Intent intent, int flags, int startId) {
        //创建一个线程，让他不断输出语句
        new Thread(){
            @Override
            public void run() {
                super.run();
                while(true) {
                    System.out.println("服务正在运行...");
                    //休眠1S
                    try {
                        sleep(1000);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        }.start();
        return super.onStartCommand(intent, flags, startId);
    }
```
运行
点击绑定服务：输出Service connected!
点击解除绑定则解除绑定
注意：点击如下打印机上面那个按钮，System.out.println()才在后台显示输出
![image](img/android/35.png)

(3) Service生命周期
public int onStartCommand(Intent intent, int flags, int startId)
public void onCreate()
public void onDestroy()
myservice.java如下：
```
public class MyService extends Service {
    public MyService() {
    }

    @Override
    public IBinder onBind(Intent intent) {
        // TODO: Return the communication channel to the service.
       // throw new UnsupportedOperationException("Not yet implemented");
        return new Binder();
    }
    @Override
    //外界执行startservice后会执行这个函数
    public int onStartCommand(Intent intent, int flags, int startId) {
        //创建一个线程，让他不断输出语句
//        new Thread(){
//            @Override
//            public void run() {
//                super.run();
//                while(true) {
//                    System.out.println("服务正在运行...");
//                    //休眠1S
//                    try {
//                        sleep(1000);
//                    } catch (InterruptedException e) {
//                        e.printStackTrace();
//                    }
//                }
//            }
//        }.start();
        return super.onStartCommand(intent, flags, startId);
    }

    @Override
    public void onCreate() {
        super.onCreate();
        System.out.println("service oncreate");
    }

    @Override
    public void onDestroy() {
        super.onDestroy();
        System.out.println("service ondestroy");
    }
}
```
运行：
![image](img/android/36.png)
点击启动服务 输出service oncreate
点击停止服务 输出service ondestroy
再点击绑定服务 输出service oncreate   Service connected!
点击解除绑定服务 输出service ondestroy
同时点击启动绑定服务后，单独点击解除绑定服务或者停止服务没有反应，必须点击解除绑定和停止两个服务才会退出
点击启动服务，点击手机左键退出程序，服务仍然运行
点击停止服务才退出
点击绑定服务，点击手机左键退出程序，抛出一个异常后服务退出（说明绑定在程序退出后解除绑定）

Myservice修改如下：
```
public int onStartCommand(Intent intent, int flags, int startId) {
        //创建一个线程，让他不断输出语句
//        new Thread(){
//            @Override
//            public void run() {
//                super.run();
//                while(true) {
//                    System.out.println("服务正在运行...");
//                    //休眠1S
//                    try {
//                        sleep(1000);
//                    } catch (InterruptedException e) {
//                        e.printStackTrace();
//                    }
//                }
//            }
//        }.start();
        System.out.println("service onStartCommand");
        return super.onStartCommand(intent, flags, startId);
    }

    @Override
    public void onCreate() {
        super.onCreate();
        System.out.println("service oncreate");
    }

    @Override
    public void onDestroy() {
        super.onDestroy();
        System.out.println("service ondestroy");
    }
```
运行：
启动服务：service oncreate，service onStartCommand。
一直点击启动服务，此时oncreate不在执行
重复执行启动服务一直输出：service onStartCommand

修改myservice：
控制服务的开始于停止
```
public class MyService extends Service {
    private boolean serviceRunning = false;//标识
    public MyService() {
    }
    @Override
    public IBinder onBind(Intent intent) {
        // TODO: Return the communication channel to the service.
       // throw new UnsupportedOperationException("Not yet implemented");
        return new Binder();
    }
    @Override
    //外界执行startservice后会执行这个函数
    public int onStartCommand(Intent intent, int flags, int startId) {
        System.out.println("service onStartCommand");
        return super.onStartCommand(intent, flags, startId);
    }

    @Override
    public void onCreate() {
        super.onCreate();
        System.out.println("service oncreate");
        serviceRunning=true;
        //创建一个线程，让他不断输出语句
        new Thread(){
            @Override
            public void run() {
                super.run();
                while(serviceRunning) {
                    System.out.println("服务正在运行...");
                    //休眠1S
                    try {
                        sleep(1000);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        }.start();
    }

    @Override
    public void onDestroy() {
        super.onDestroy();
        System.out.println("service ondestroy");
        serviceRunning=false;
    }
}
```
运行：
启动服务：
service oncreate
service onStartCommand
服务正在运行...
服务正在运行...
服务正在运行...
服务正在运行...

停止服务：
service ondestroy

绑定服务：
service oncreate
服务正在运行...
Service connected!
服务正在运行...
服务正在运行...
服务正在运行...
服务正在运行...

解除绑定服务：
service ondestroy

8.Android 中 Service 通信
------------------------
核心内容：绑定Service并与之通信
(1) 启动 Service 并传递数据
外界与一个服务实现数据传递
Main.xml
```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools" android:layout_width="match_parent"
   android:orientation="vertical"
    android:layout_height="match_parent" android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    android:paddingBottom="@dimen/activity_vertical_margin" tools:context=".MainActivity">

    <EditText
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:text="默认信息"
        android:id="@+id/etData"/>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="启动服务"
        android:id="@+id/btnStartService" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="停止服务"
        android:id="@+id/btnStopService" />

</LinearLayout>
```
Main.java
```
public class MainActivity extends Activity implements View.OnClickListener {

    private EditText editText;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        editText= (EditText) findViewById(R.id.etData);
        findViewById(R.id.btnStartService).setOnClickListener(this);
        findViewById(R.id.btnStopService).setOnClickListener(this);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            return true;
        }

        return super.onOptionsItemSelected(item);
    }

    @Override
    public void onClick(View v) {
        switch (v.getId()) {
            case R.id.btnStartService:
                Intent i=new Intent(this,MyService.class);
                i.putExtra("data",editText.getText().toString());//直接把data放到intent传递给service-----service中onstartcommand中第一个参数就是接收的intent
                startService(i);
                break;
            case R.id.btnStopService:
                stopService(new Intent(this,MyService.class));
                break;
        }
    }
}
```
Service.java
```
public class MyService extends Service {

    private boolean running=false;
    private String data="这是默认信息";

    public MyService() {
    }

    @Override
    public IBinder onBind(Intent intent) {
        // TODO: Return the communication channel to the service.
        throw new UnsupportedOperationException("Not yet implemented");
    }

    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        data=intent.getStringExtra("data");
        return super.onStartCommand(intent, flags, startId);
    }

    @Override
    public void onCreate() {
        running=true;
        super.onCreate();
        new Thread(){
            @Override
            public void run() {
                super.run();
                while (running){
                    System.out.println(data);/////////////
                    try {
                        sleep(1000);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        }.start();
    }

    @Override
    public void onDestroy() {
        super.onDestroy();
        running=false;
    }
}
```
运行：
点击启动服务输出：默认信息
改变输入框内信息再点击启动服务：后台输出信息发生变化，和输入框内一样
停止服务：输出停止

(2) 绑定 Service 进行通信（上）
本课时讲解如何与被绑定的 Service 进行通信
Main.xml
```
<EditText
    android:layout_width="fill_parent"
    android:layout_height="wrap_content"
    android:text="默认信息"
    android:id="@+id/etData"/>

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="启动服务"
    android:id="@+id/btnStartService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="停止服务"
    android:id="@+id/btnStopService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="绑定服务"
    android:id="@+id/btnBindservice" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="解除绑定服务"
    android:id="@+id/btnUnbindservice" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="同步数据"
    android:id="@+id/btnSyncData" />
```
Main.java
```
public class MainActivity extends Activity implements View.OnClickListener, ServiceConnection {

    private EditText editText;
    private MyService.Binder binder = null;//定义一个Binder对象
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        editText= (EditText) findViewById(R.id.etData);
        findViewById(R.id.btnStartService).setOnClickListener(this);
        findViewById(R.id.btnStopService).setOnClickListener(this);
        findViewById(R.id.btnBindservice).setOnClickListener(this);
        findViewById(R.id.btnUnbindservice).setOnClickListener(this);
        findViewById(R.id.btnSyncData).setOnClickListener(this);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            return true;
        }

        return super.onOptionsItemSelected(item);
    }

    @Override
    public void onClick(View v) {
        switch (v.getId()) {
            case R.id.btnStartService:
                Intent i=new Intent(this,MyService.class);
                i.putExtra("data",editText.getText().toString());//直接把data放到intent传递给service-----service中onstartcommand中第一个参数就是接收的intent
                startService(i);
                break;
            case R.id.btnStopService:
                stopService(new Intent(this, MyService.class));
                break;
            case R.id.btnBindservice:
                bindService(new Intent(this, MyService.class),this, Context.BIND_AUTO_CREATE);
                break;
            case R.id.btnUnbindservice:
                unbindService(this);
                break;
            case R.id.btnSyncData:
                if(binder != null){
                    binder.setData(editText.getText().toString());//从输入框内传入数据---这种方法比直接方法调用，比Intent那种方法快得多
                }
                break;
        }
    }

    @Override
    //这里参数IBinder service是myservice中传来
    //访问到的是myservice中 public IBinder onBind(Intent intent)的的返回值
    public void onServiceConnected(ComponentName name, IBinder service) {
        binder= (MyService.Binder) service;
    }

    @Override
    public void onServiceDisconnected(ComponentName name) {

    }
}

```
myservice.java
```
public class MyService extends Service {

    private boolean running=false;
    private String data="这是默认信息";

    public MyService() {
    }

    @Override
    public IBinder onBind(Intent intent) {
        return new Binder();//自己建的
    }

    //创建一个类继承来自系统的Binder
    public class Binder extends android.os.Binder{
        public void setData(String data){
            MyService.this.data=data;//修改data值
        }
    }

    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        data=intent.getStringExtra("data");
        return super.onStartCommand(intent, flags, startId);
    }

    @Override
    public void onCreate() {
        running=true;
        super.onCreate();
        new Thread(){
            @Override
            public void run() {
                super.run();
                while (running){
                    System.out.println(data);/////////////
                    try {
                        sleep(1000);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        }.start();
    }

    @Override
    public void onDestroy() {
        super.onDestroy();
        running=false;
    }
}
```
运行程序：
点击绑定服务：输出：这是默认信息
改变输入框内容，点击同步数据：后台输出内容与输入框内容一样

(3) 绑定 Service 进行通信（下）
本课时讲解如何侦听被绑定的 Service 的内部状态
如服务内部发生改变后发送到界面
Callback回调
Main.xml
```
<TextView
    android:layout_width="fill_parent"
    android:layout_height="wrap_content"
    android:id="@+id/tvOut"/>

<EditText
    android:layout_width="fill_parent"
    android:layout_height="wrap_content"
    android:text="默认信息"
    android:id="@+id/etData"/>

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="启动服务"
    android:id="@+id/btnStartService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="停止服务"
    android:id="@+id/btnStopService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="绑定服务"
    android:id="@+id/btnBindservice" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="解除绑定服务"
    android:id="@+id/btnUnbindservice" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="同步数据"
    android:id="@+id/btnSyncData" />
```
Main.java
```
public class MainActivity extends Activity implements View.OnClickListener, ServiceConnection {

    private TextView tvOut;
    private EditText editText;
    private MyService.Binder binder = null;//定义一个Binder对象
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        tvOut= (TextView) findViewById(R.id.tvOut);
        editText= (EditText) findViewById(R.id.etData);
        findViewById(R.id.btnStartService).setOnClickListener(this);
        findViewById(R.id.btnStopService).setOnClickListener(this);
        findViewById(R.id.btnBindservice).setOnClickListener(this);
        findViewById(R.id.btnUnbindservice).setOnClickListener(this);
        findViewById(R.id.btnSyncData).setOnClickListener(this);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            return true;
        }

        return super.onOptionsItemSelected(item);
    }

    @Override
    public void onClick(View v) {
        switch (v.getId()) {
            case R.id.btnStartService:
                Intent i=new Intent(this,MyService.class);
                i.putExtra("data",editText.getText().toString());//直接把data放到intent传递给service-----service中onstartcommand中第一个参数就是接收的intent
                startService(i);
                break;
            case R.id.btnStopService:
                stopService(new Intent(this, MyService.class));
                break;
            case R.id.btnBindservice:
                bindService(new Intent(this, MyService.class),this, Context.BIND_AUTO_CREATE);
                break;
            case R.id.btnUnbindservice:
                unbindService(this);
                break;
            case R.id.btnSyncData:
                if(binder != null){
                    binder.setData(editText.getText().toString());//从输入框内传入数据---这种方法比直接方法调用，比Intent那种方法快得多
                }
                break;
        }
    }

    @Override
    //这里参数IBinder service是myservice中传来
    //访问到的是myservice中 public IBinder onBind(Intent intent)的的返回值
    public void onServiceConnected(ComponentName name, IBinder service) {
        binder= (MyService.Binder) service;
        //访问回调函数
        binder.getService().setCallback(new MyService.Callback() {
            @Override
            public void onDataChange(String data) {
                //UI线程是不允许其他辅线程来修改UI线程的资源
//                tvOut.setText(data);//错误-------------因为程序是由myservice中新创建的线程来调用的，直接用一个新创建的线程来执行UI线程的资源是不能成功运行的
                //再下面新创建一个Handler
                Message msg = new Message();
                Bundle b=new Bundle();
                b.putString("data",data);
                //通过msg附加上一个数据
                msg.setData(b);
                handler.sendMessage(msg);
            }
        });
    }

    @Override
    public void onServiceDisconnected(ComponentName name) {

    }

    //新创建一个Handler
    //用android.os.Handler类而不是java库中Handler类
    private android.os.Handler handler = new android.os.Handler(){
        @Override
        public void handleMessage(Message msg) {
            super.handleMessage(msg);
            //获取字符串
           tvOut.setText(msg.getData().getString("data"));
        }
    };
}

```

myservice.java
```
public class MyService extends Service {

    private boolean running=false;
    private String data="这是默认信息";

    public MyService() {
    }

    @Override
    public IBinder onBind(Intent intent) {
        return new Binder();//自己建的
    }

    //创建一个类继承来自系统的Binder
    public class Binder extends android.os.Binder{
        public void setData(String data){
            MyService.this.data=data;//修改data值
        }

        //回调函数事件绑定
        public MyService getService(){
            return MyService.this;
        }


    }

    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        data=intent.getStringExtra("data");
        return super.onStartCommand(intent, flags, startId);
    }

    @Override
    public void onCreate() {
        running=true;
        super.onCreate();
        new Thread(){
            @Override
            public void run() {
                super.run();

                int i = 0;
                while (running){
                    i++;
                    String str=i+":"+data;
                    System.out.println(str);/////////////
                    if(callback != null){
                        callback.onDataChange(str);
                    }

                    try {
                        sleep(1000);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        }.start();
    }

    @Override
    public void onDestroy() {
        super.onDestroy();
        running=false;
    }

    private Callback callback = null;

    public void setCallback(Callback callback) {
        this.callback = callback;
    }

    public Callback getCallback() {
        return callback;
    }

    public static interface Callback{
        void onDataChange(String data);
    }
}
```

运行：点击绑定服务  开始不断累加显示数字----信息是从myservice中传来的
![image](img/android/37.png)

9.Android 中 AIDL 的理解与使用
----------------------------
(1) 跨应用启动 Service
Appservice.java
```
public void onCreate() {
    super.onCreate();
    System.out.println("service started");
}

@Override
public void onDestroy() {
    super.onDestroy();
    System.out.println("service ondestroyed");
```
main.java
```
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    startService(new Intent(this,Appservice.class));
}

@Override
protected void onDestroy() {
    super.onDestroy();
    stopService(new Intent(this, Appservice.class));
}
```
运行程序，后台输出service started，退出程序，后台输出service ondestroyed
在同一个程序中通过startService(new Intent(this,Appservice.class)); stopService(new Intent(this, Appservice.class));启动停止服务简单，那么如何通过其他程序来启动停止这个服务呢？
再创建一个名字为AnotherApp的module
备注：Android5.0以前可以使用隐式Intent（前面有讲到用他启动另外一个APP的activity）, Android5.0之后只能使用显式Intent
AnotherApp.main.xml
```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="启动服务"
    android:id="@+id/btnStartAppService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="停止服务"
    android:id="@+id/btnStopAppService" />
```
AnotherApp.main.java
```
private Intent serviceIntent;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.btnStartAppService).setOnClickListener(this);
        findViewById(R.id.btnStopAppService).setOnClickListener(this);

        serviceIntent=new Intent();
        //如下显示Intent
        //通过setComponent显示指明要启动的Intent
//                new ComponentName(被启动的Intent所在包名，被启动的类名)
        serviceIntent.setComponent(new ComponentName("com.example.zhang.startservicefromanotherapp","com.example.zhang.startservicefromanotherapp.Appservice"));
    }

    @Override
    public void onClick(View v) {
        switch (v.getId()){
            case R.id.btnStartAppService:
                startService(serviceIntent);
                break;
            case R.id.btnStopAppService:
                stopService(serviceIntent);
                break;
        }
    }
```
运行：
点击启动服务，在被启动项目下的后台（StartservicefromanotherAPP）（注意：不是AnotherApp）可以看到启动输出：service started

也可以在Appservice内部重写onStartCommand用于接收从其他的应用传过来的数据
```
public int onStartCommand(Intent intent, int flags, int startId){}
```

(2) 跨应用绑定 Service
绑定时需要用到一个bundler，一个程序无法访问另外一个程序中类的定义，那么是否不能通信呢？
Android提供了一种机制用于多个程序之间通信：AIDL（Android Interface Definition Language/ Android接口定义语言），下面进行操作
创建一个AIDL文件
App下java包下New->AIDL->AIDL file（IAppServiceInterface），会生成一个.aidl文件，里面会自动生成对应的一个类IAppServiceInterface
这时候点击build->rebuild project重构一下（以便检测到刚刚生成的类），如此在service的public IBinder onBind(Intent intent)函数中可以直接返回这个类
Myservice.java
```
public class Appservice extends Service {
    public Appservice() {
    }

    @Override
    public IBinder onBind(Intent intent){
        return new IAppServiceInterface.Stub(){
            public void basicTypes(int anInt, long aLong, boolean aBoolean, float aFloat, double aDouble, String aString) throws RemoteException {
            }
        };
    }

    @Override
    public void onCreate() {
        super.onCreate();
        System.out.println("service started");
    }

    @Override
    public void onDestroy() {
        super.onDestroy();
        System.out.println("service ondestroyed");
    }
```
如何通过AnotherApp绑定这个服务呢？
AnotherApp.main.xml
```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="启动外部服务"
    android:id="@+id/btnStartAppService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="停止外部服务"
    android:id="@+id/btnStopAppService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="绑定外部服务"
    android:id="@+id/btnBindAppService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="解除绑定外部服务"
    android:id="@+id/btnUnbindAppService" />
```
AnotherApp.main.java
```
public class MainActivity extends Activity implements View.OnClickListener, ServiceConnection {

    private Intent serviceIntent;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.btnStartAppService).setOnClickListener(this);
        findViewById(R.id.btnStopAppService).setOnClickListener(this);
        findViewById(R.id.btnBindAppService).setOnClickListener(this);
        findViewById(R.id.btnUnbindAppService).setOnClickListener(this);

        serviceIntent=new Intent();
        //如下显示Intent
        //通过setComponent显示指明要启动的Intent
//                new ComponentName(被启动的Intent所在包名，被启动的类名)
        serviceIntent.setComponent(new ComponentName("com.example.zhang.startservicefromanotherapp","com.example.zhang.startservicefromanotherapp.Appservice"));
    }

    @Override
    public void onClick(View v) {
        switch (v.getId()){
            case R.id.btnStartAppService:
                startService(serviceIntent);
                break;
            case R.id.btnStopAppService:
                stopService(serviceIntent);
                break;
            case R.id.btnBindAppService:
                bindService(serviceIntent, this, Context.BIND_AUTO_CREATE);
                break;
            case R.id.btnUnbindAppService:
                unbindService(this);//注意，这里区别于上面三个，用this
                break;
        }
    }

//bindService(serviceIntent, this, Context.BIND_AUTO_CREATE);中this需要下面两个函数
    public void onServiceConnected(ComponentName name, IBinder service) {
        System.out.println("Bind service");
        System.out.println(service);//看一下传入的IBinder是啥东西
// android.os.BinderProxy@c5151c7
    }

    @Override
    public void onServiceDisconnected(ComponentName name) {

    }
```
先安装上App，再运行AnotherApp
点击绑定服务，App后台输出启动服务，AnotherApp后台输出Bind service android.os.BinderProxy@c5151c7

(3) 跨应用绑定 Service 并通信
修改aidl,添加接口

同步如何使用呢？
需要在另外一个APP下创建一个与原APP包含.aidl文件的相同包名和对应包下放相同的.aidl文件
创建过程：右键->new->Folder-> AIDL Folder->finish
之后发现多出一个AIDL文件夹，右键->new->package(名字与原APP的.aidl文件包名同)
把.aidl文件复制到这个包下面就可以
现在两个应用有同样的.aidl文件，可以定义同样的定义

IAppServiceInterface.aidl
```
interface IAppServiceInterface {
    /**
     * Demonstrates some basic types that you can use as parameters
     * and return values in AIDL.
     */
    void basicTypes(int anInt, long aLong, boolean aBoolean, float aFloat,
            double aDouble, String aString);

    void setData(String data);
}
```
App.appservice.java
```
public class Appservice extends Service {

    //设置一个默认数据，通过另外一个App更改
    private String data="默认数据";
    private boolean running=false;

    public Appservice() {
    }

    @Override
    public IBinder onBind(Intent intent){
        return new IAppServiceInterface.Stub(){
            public void basicTypes(int anInt, long aLong, boolean aBoolean, float aFloat, double aDouble, String aString) throws RemoteException {
            }

            @Override
            public void setData(String data) throws RemoteException {
            Appservice.this.data=data;//对数据进行修改
            }
        };
    }

    @Override
    public void onCreate() {
        super.onCreate();
        System.out.println("service started");
        new Thread(){
            @Override
            public void run() {
                super.run();
                running=true;
                while (running){
                    System.out.println(data);
                    try {
                        Thread.sleep(1000);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        }.start();
    }

    @Override
    public void onDestroy() {
        super.onDestroy();
        System.out.println("service ondestroyed");
        running=false;
    }

    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        return super.onStartCommand(intent, flags, startId);
    }
}
```
App.main.java
```
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    startService(new Intent(this,Appservice.class));
}

@Override
protected void onDestroy() {
    super.onDestroy();
    stopService(new Intent(this, Appservice.class));
}
```
Anotherapp.main.xml
```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="启动外部服务"
    android:id="@+id/btnStartAppService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="停止外部服务"
    android:id="@+id/btnStopAppService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="绑定外部服务"
    android:id="@+id/btnBindAppService" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="解除绑定外部服务"
    android:id="@+id/btnUnbindAppService" />

<EditText
    android:layout_width="fill_parent"
    android:layout_height="wrap_content"
    android:text="这是另外一个应用的数据"
    android:id="@+id/etInput"/>

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="同步数据到绑定服务中"
    android:id="@+id/btnSync" />
```
Another.main.java
```
public class MainActivity extends Activity implements View.OnClickListener, ServiceConnection {

    private Intent serviceIntent;
    private EditText etInput;
    private IAppServiceInterface binder=null;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etInput= (EditText) findViewById(R.id.etInput);
        findViewById(R.id.btnStartAppService).setOnClickListener(this);
        findViewById(R.id.btnStopAppService).setOnClickListener(this);
        findViewById(R.id.btnBindAppService).setOnClickListener(this);
        findViewById(R.id.btnUnbindAppService).setOnClickListener(this);
        findViewById(R.id.btnSync).setOnClickListener(this);

        serviceIntent=new Intent();
        //如下显示Intent
        //通过setComponent显示指明要启动的Intent
//                new ComponentName(被启动的Intent所在包名，被启动的类名)
        serviceIntent.setComponent(new ComponentName("com.example.zhang.startservicefromanotherapp","com.example.zhang.startservicefromanotherapp.Appservice"));
    }

    @Override
    public void onClick(View v) {
        switch (v.getId()){
            case R.id.btnStartAppService:
                startService(serviceIntent);
                break;
            case R.id.btnStopAppService:
                stopService(serviceIntent);
                break;
            case R.id.btnBindAppService:
                bindService(serviceIntent, this, Context.BIND_AUTO_CREATE);
                break;
            case R.id.btnUnbindAppService:
                unbindService(this);//注意，这里区别于上面三个，用this
                binder=null;//解除绑定后要清空
                break;
            case R.id.btnSync:
                if(binder!=null){
                    //远程通信异常
                    try {
                        binder.setData(etInput.getText().toString());
                    } catch (RemoteException e) {
                        e.printStackTrace();
                    }
                }
                break;
        }
    }

//bindService(serviceIntent, this, Context.BIND_AUTO_CREATE);中this需要下面两个函数
    public void onServiceConnected(ComponentName name, IBinder service) {
        System.out.println("Bind service");
        System.out.println(service);//看一下传入的IBinder是啥东西

//        binder = (IAppServiceInterface) service;//错误 虽然两个应用中类的名字一样，但具体所在的内存地址不一样
        binder=IAppServiceInterface.Stub.asInterface(service);
    }

    @Override
    public void onServiceDisconnected(ComponentName name) {

    }
```
安装APP后再运行AnotherApp
绑定外部服务，APP后台会输出“默认信息”，点击同步后与App中输入框的相同

10.Android 广播接收器 BroadcastReceiver
------------------------------------
BroadcastReceiver 是Android 四大基本组件之一，用于接收广播信息，如：开屏、锁屏、短信等等，在实际工作中用途非常广泛
核心内容：动态注册和注销 BroadcastReceiver

(1) 使用 BroadcastReceiver
首先创建一个项目，再创建一个BroadcastReceiver：new->other-> Broadcast Receiver
生成一个.java,可以在onReceive（）方法里面写语句
Receiver的子标签在fest.xml自动添加
```
<receiver
    android:name=".MyReceiver"
    android:enabled="true"
    android:exported="true" >
</receiver>
```
Main.xml
```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="发送消息"
    android:id="@+id/btnSendMsg" />
```
Main.java
```
public class MainActivity extends Activity implements View.OnClickListener {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.btnSendMsg).setOnClickListener(this);
    }

    public void onClick(View v) {
        switch (v.getId()){
            case R.id.btnSendMsg:
                sendBroadcast(new Intent(this,MyReceiver.class));//发送广播消息
                break;
        }
    }
```
MyReceiver.java
```
public class MyReceiver extends BroadcastReceiver {
    public MyReceiver() {
    }
    @Override
    //这里创建了一个广播接收器，如果有其他程序朝接收器这里发送消息，就会接收到
    public void onReceive(Context context, Intent intent) {
        System.out.println("接收到了一条消息");

    }
}
```
运行点击发送按钮，后台输出：接收到了一条消息
当然，也可以附带上数据传输
Main.java
```
public void onClick(View v) {
    switch (v.getId()){
        case R.id.btnSendMsg:
            Intent i=new Intent(this,MyReceiver.class);
            i.putExtra("data","good morning!");
            sendBroadcast(i);//发送广播消息
            break;
    }
```
MyRciver.java
```
public void onReceive(Context context, Intent intent) {
    System.out.println("接收到了一条消息:"+intent.getStringExtra("data"));

}
```
运行点击发送按钮：
后台输出：接收到了一条消息:good morning!

(2) 动态注册和注销 BroadcastReceiver
不用始终处于监听状态，用注册和注销 BroadcastReceiver
去fest.xml删除Receiver注册，这时候接收不到消息
下面直接通过程序来实现注册：
添加两个按钮控制注册于注销
Main.xml
```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="发送消息"
    android:id="@+id/btnSendMsg" />
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="注册接收器"
    android:id="@+id/btnReg" />
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="注销接收器"
    android:id="@+id/btnUnreg" />
```
Main.java
```
protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.btnSendMsg).setOnClickListener(this);
        findViewById(R.id.btnReg).setOnClickListener(this);
        findViewById(R.id.btnUnreg).setOnClickListener(this);
    }

    private MyReceiver receiver=null;//防止多次注册
    public void onClick(View v) {
        switch (v.getId()) {
            case R.id.btnSendMsg:
//                Intent i = new Intent(this, MyReceiver.class);//动态注册不能再用这种格式，用下面的
                Intent i=new Intent(MyReceiver.ACTION);//直接传ACTION的方式发送---隐式Intent
                i.putExtra("data", "good morning!");
                sendBroadcast(i);//发送广播消息
                break;
            case R.id.btnReg:
                if(receiver==null){
                    receiver=new MyReceiver();
                    //registerReceiver(receiver,new IntentFilter(ACTION是一个字符串，有一个约定成俗的固定的格式，-可以在Myreceiver中定义));
                    registerReceiver(receiver,new IntentFilter(MyReceiver.ACTION));//zhuc
                }
                break;
            case R.id.btnUnreg:
                if(receiver != null){
                    unregisterReceiver(receiver);//注销
                    receiver=null;
                }
                break;
        }
    }
```
Myreciver.java
```
public static final String ACTION = "com.example.zhang.learnbroadcastreceiver.intent.action.MyReceiver";
public MyReceiver() {
}
@Override
//这里创建了一个广播接收器，如果有其他程序朝接收器这里发送消息，就会接收到
public void onReceive(Context context, Intent intent) {
    System.out.println("接收到了一条消息:"+intent.getStringExtra("data"));

}
```
运行点击注册之后点击发送消息才有反应，点击注销后发送消息没有反应
刚刚上面忘记了删除fest.xml中的自动注册，运行依然正确，应该是动态注册优先级高吧

(3) BroadcastReceiver 的优先级
先给MyReceiver添加注册信息
```
<receiver android:name=".MyReceiver">
    <intent-filter>
        <action android:name="com.example.zhang.learnbroadcastreceiver.intent.action.MyReceiver"/>
    </intent-filter>
</receiver>
```
再创建一个接收器Myreceiver1
```
public void onReceive(Context context, Intent intent) {
    System.out.println("MyReceiver1 接收到消息：");
}
```
Fest.xml
```
<receiver android:name=".MyReceiver" >
    <intent-filter>
        <action android:name="com.example.zhang.learnbroadcastreceiver.intent.action.MyReceiver" />
    </intent-filter>
</receiver>
<receiver
    android:name=".MyReceiver1"
    android:enabled="true"
    android:exported="true" >
    <intent-filter>
        <action android:name="com.example.zhang.learnbroadcastreceiver.intent.action.MyReceiver" />
    </intent-filter>
</receiver>
```
两个接收器用相同的action,理论上两个接收器都能接收到消息
运行：发现都接收到了消息，先注册的接收器先接收到消息
接收到了一条消息:good morning!
MyReceiver1 接收到消息：

也可以手动指定优先级<intent-filter android:priority="数字">数字越大优先级越高，越先接收到消息
如下MyReceiver1先接收到消息：
```
<receiver android:name=".MyReceiver" >
    <intent-filter android:priority="9">
        <action android:name="com.example.zhang.learnbroadcastreceiver.intent.action.MyReceiver" />
    </intent-filter>
</receiver>
<receiver
    android:name=".MyReceiver1"
    android:enabled="true"
    android:exported="true" >
    <intent-filter android:priority="10">
        <action android:name="com.example.zhang.learnbroadcastreceiver.intent.action.MyReceiver" />
    </intent-filter>
</receiver>
```
如何让一个优先级高的receiver防止后面的接收器接收到数据呢？
```
public void onReceive(Context context, Intent intent) {
    System.out.println("MyReceiver1 接收到消息：");

    abortBroadcast();//中断广播，优先级低于这个的将不在接收到广播消息
}
```
运行如下：
01-21 03:17:45.761  19775-19775/com.example.zhang.learnbroadcastreceiver I/System.out﹕ MyReceiver1 接收到消息：
01-21 03:17:45.919  19775-19775/com.example.zhang.learnbroadcastreceiver E/BroadcastReceiver﹕ BroadcastReceiver trying to return result during a non-ordered broadcast……………….
01-21 03:17:46.035  19775-19775/com.example.zhang.learnbroadcastreceiver I/System.out﹕ MyReceiver 接收到了消息

为啥优先级低的也接收到了消息？
因为BroadcastReceiver trying to return result during a non-ordered broadcast
尝试中断的是一个非顺序的broadcast，直接用sendBroadcast(i);发送的广播消息是不能被中断的，需要改为下面才能被中断：
```
  public void onClick(View v) {
        switch (v.getId()) {
            case R.id.btnSendMsg:
//                Intent i = new Intent(this, MyReceiver.class);//动态注册不能再用这种格式，用下面的
                Intent i=new Intent(MyReceiver.ACTION);//直接传ACTION的方式发送---隐式Intent
                i.putExtra("data", "good morning!");
//                sendBroadcast(i);//发送广播消息-------这个函数发送消息不能被中断
                sendOrderedBroadcast(i,null);//第一个参数为Intent,第二个为权限--这个函数发送消息能被中断
                break;
            case R.id.btnReg:
                if(receiver==null){
                    receiver=new MyReceiver();
                    //registerReceiver(receiver,new IntentFilter(ACTION是一个字符串，有一个约定成俗的固定的格式，-可以在Myreceiver中定义));
                    registerReceiver(receiver,new IntentFilter(MyReceiver.ACTION));//zhuc
                }
                break;
            case R.id.btnUnreg:
                if(receiver != null){
                    unregisterReceiver(receiver);//注销
                    receiver=null;
                }
                break;
        }
```
运行程序优先级低的被中断

11.Android 日志系统
----------------------
Android 日志是用来记录程序运行过程的，但是在实际开发中，由于日志信息太多导致不方便查看有效日志而影响了正常的开发调试工作，所以学会对日志进行分类查看非常重要。
核心内容：System.out;System.err;Android Log 类;日志分类过滤

(1) 使用日志 API
讲解在 Android 系统中如何使用日志 API 进行日志输出，内容包括 System.out、System.err、Log.v、Log.d、Log.i、Log.w、Log.e 的使用。
创建一个项目LearnLog
```
System.out.println("普通日志");// System.out.println（）属于普通日志
System.err.println("错误日志");
```
运行输出：
1349-1349/com.example.zhang.learnlog I/System.out﹕ 普通日志
1349-1349/com.example.zhang.learnlog W/System.err﹕ 错误日志
I----Info-------普通消息
W----Warning--------警告信息
Log level:消息类型
Verbose:最低-----全部显示
Info------显示info信息以及比他高的信息
![image](img/android/38.png)
上面是java提供的android还提供了非常详细的日志信息Log.里面有很多信息
//安卓提供从高到低日志信息如下
```
Log.e(TAG,"错误信息");//error
Log.w(TAG,"警告信息");//warn
Log.i(TAG,"普通信息");//info
Log.d(TAG,"调试信息");//debug
Log.v(TAG,"无用信息");//verbose 比如：一个程序员可以输出唠叨信息---这段程序好难写啊
```

(2) 日志分类
如何对日志进行分类呈现，便于开发调试。
![image](img/android/39.png)
No Filters----------------显示全部应用程序的日志信息
Show only selected application------------只是显示当前应用的日志信息

Edit Filters Configuration----------编辑路径：可以自定义标签
如只是输出MainActivity标签的信息：
![image](img/android/40.png)
则显示信息都是MainActivity标签的
Tag-标签     Message-----内容  pid------程序进程id

(3) 使用 DDMS 查看日志
DDMS 以及独立的 DDMS 查看日志
DDMS----------设备监听器
![image](img/android/41.png)
点击可以启动一个应用
![image](img/android/42.png)
选择一个设备，如下面一个模拟器
可以看到日志信息
![image](img/android/43.png)
可以点击上面绿色的加号
![image](img/android/44.png)
DDMS可以独立于开发环境启动
点击E:\Android\SDK\tools\ddms.bat就可以启动
DDMS可以用于调试
如下：
可以模拟拨打电话、发短信到模拟手机
其他还有好多功能自己尝试
![image](img/android/45.png)

11.Android 权限系统
----------------------
在 Android 中有非常完善的权限控制机制，开发者需要懂得如何使用，普通用户需要懂得如何分辨，结合起来才能够有效的阻止 Android 平台病毒的传播。
核心内容：定义权限;在代码中做权限检查;为基本组件添加权限检查
(1) 请求权限实例
创建项目LearnWebview
Main.xml
```
//WebView-----网页
<WebView
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/wv"></WebView>
```
Main.java
```
private WebView wv;
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    wv= (WebView) findViewById(R.id.wv);
    //用wv加载一个主页
    wv.loadUrl("http://www.bestzhangjin.com");

}
```
运行：
会提醒我们无法访问网页，并且有很多的错误，这是因为loadUrl("http://www.bestzhangjin.com") 加载一个网页需要一个权限
就是互联网的访问权限
需要在fest.xml中进行声明
```
<uses-permission android:name="android.permission.INTERNET"/>//声明访问互联网权限

<application
```
这时候重新运行可以访问到主页
![image](img/android/46.png)
用loadUrl("http://bestzhangjin.com")时没有www.会自动跳转到http://www.bestzhangjin.com 

在APPInfo中可以查看到权限

(2) 为代码添加权限检查
新建一个类Hello.java
```
public class Hello {

    public static final String PERMISSION_SAY_HELLO="com.example.zhang.learnwebview.permission.sayHello";
    //用下面的方法检测程序是否有执行权限
    public static void sayHello(Context context){//利用Context才能够访问到一下全局的属性
        int checkResult=context.checkCallingOrSelfPermission(PERMISSION_SAY_HELLO);//执行程序的代码是否拥有这个权限
        if(checkResult != PackageManager.PERMISSION_GRANTED){//PERMISSION_GRANTED---允许，PERMISSION_DENIED--拒绝
            throw new SecurityException("执行sayhello方法需要有com.example.zhang.learnwebview.permission.sayHello权限！");
        }
        System.out.println("你有权限，已经执行");
    }
}
```
fest.xml
```
<!---  新注册一个权限，权限的名字为com.example.zhang.learnwebview.permission.sayHello   -->
<permission android:name="com.example.zhang.learnwebview.permission.sayHello"/>
```
Main.java
```
Hello.sayHello(this);
```
运行出现异常：Unfortunately,。。。。。。。。stopped
后台输出提示执行sayhello方法需要有com.example.zhang.learnwebview.permission.sayHello权限！

下面填写权限：
Fest.xml
```
<!---  新注册一个权限，权限的名字为com.example.zhang.learnwebview.permission.sayHello   -->
<permission android:name="com.example.zhang.learnwebview.permission.sayHello"/>
<!--  获取权限 -->
<uses-permission android:name="com.example.zhang.learnwebview.permission.sayHello"/>
```
再次运行成功！输出：你有权限，已经执行

(3) 为基本组件添加权限检查
Android四大组件都可以使用相同的方式来配置权限
这里也activity为例
新建一个activity名字MyAty
MyAty.xml
```
<TextView android:text="这是一个被启动的activity" android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```
Fest.xml声明权限
注意：fest.xml中在顶部和被启动的activity中都要声明
```
<permission android:name="com.example.zhang.learnwebview.permission.MYATY"/>
```
```
<activity
    android:name=".MyAty"
    android:label="@string/title_activity_my_aty"
    android:permission="com.example.zhang.learnwebview.permission.MYATY">
</activity>
````
Main.xml
```
<Button
    android:layout_width="fill_parent"
    android:layout_height="wrap_content"
    android:text="启动MyAty"
    android:id="@+id/btnStartMyAty"/>
```
Main.java
```
findViewById(R.id.btnStartMyAty).setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        startActivity(new Intent(MainActivity.this,MyAty.class ));
    }
});
```
可以运行，因为是在一个应用之内
用另外一个应用启动这个activity则不行，需要加权限
新建一个module
OtherApp.main.xml加一个按钮
这里采用action方法启动另外一个应用的activity
所以先在被启动的应用的fest.xml的activity配置下加上action
```
<activity
    android:name=".MyAty"
    android:label="@string/title_activity_my_aty"
    android:permission="com.example.zhang.learnwebview.permission.MYATY">
    <intent-filter>
        <category android:name="android.intent.category.DEFAULT"/>
        <action android:name="com.example.zhang.learnwebview.intent.action.MyAty"/>
    </intent-filter>
</activity>
```
OtherApp.main.java
```
findViewById(R.id.btnStartMyAty).setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        //通过action启动其他应用的activity
        startActivity(new Intent("com.example.zhang.learnwebview.intent.action.MyAty"));
    }
});
```
运行按下按钮显示onfutunately--------退出
因为没有权限
在OtherApp.fest.xml前面加上使用声明
```
<uses-permission android:name="com.example.zhang.learnwebview.permission.MYATY"/>
```
之后运行正常


第三章 用户界面优化
================
1.Android Fragment
---------------------
Fragment 是 Android 中在同一个应用内部用于替换 Activity 界面跳转的机制，她高效灵活，是 Android 开发中不可缺少的。
核心内容：认识 Fragment；Fragment 生命周期；Fragment 的应用
Activity是比较重量级的基本组件，同一个程序内部界面切换不合适

(1) 使用 Fragment
创建一个with--Fragment项目
![image](img/android/47.png)
Main.xml—自动生成
```
<fragment xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools" android:id="@+id/fragment"
    android:name="com.example.zhang.fragment.MainActivityFragment"
    tools:layout="@layout/fragment_main" android:layout_width="match_parent"
    android:layout_height="match_parent" />
```
Fragment_main.xml
```
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="呈现另一个fragment"
    android:id="@+id/btnShowAnotherFragment" />
```
Fragment_another.xml
```
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="这是另外一个fragment"
    android:id="@+id/textView"/>

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="后退"
    android:id="@+id/btnBack" />
```
Main.java自动
```
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }


    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            return true;
        }

        return super.onOptionsItemSelected(item);
    }
}
```
MainActivityFragment.java
```
public class MainActivityFragment extends Fragment {

    public MainActivityFragment() {
    }

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        View rootView = inflater.inflate(R.layout.fragment_main, container, false);
        //添加事件监听器
        rootView.findViewById(R.id.btnShowAnotherFragment).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                getFragmentManager().beginTransaction()
                        .addToBackStack(null)//后退键------没有这行后退键将直接退出程序
                        .replace(R.id.fragment,new AnotherFragment()).commit();
            }
        });
        return rootView;
    }
}
```
AnotherFragment.java
```
public class AnotherFragment extends Fragment {
    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
        /////////////java文件解析对应的.xml
        View root=inflater.inflate(R.layout.fragment_another, container, false);
        root.findViewById(R.id.btnBack).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                getFragmentManager().popBackStack();//实现后退操作
            }
        });
        return root;
    }
}

```
运行仿真如下，我的是在一个界面内，极客学院的在不同的界面内
![image](img/android/48.png)

(2)Fragment 的生命周期
Fragment生命周期图如下:
![image](img/android/49.png)
一般知道三个即可：onCreate(),onCreateView(),onPause()
将AnotherFragment.java修改如下：
```
public class AnotherFragment extends Fragment{
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
        System.out.println("onCreateView");
        View rootView = inflater.inflate(R.layout.fragment_another, container, false);
        return rootView;
    }

    @Override
    public void onCreate(Bundle savedInstanceState) {
        System.out.println("onCreate");
        super.onCreate(savedInstanceState);
    }


    @Override
    public void onPause() {
        System.out.println("onPause");
        super.onPause();
    }

    @Override
    public void onDestroy() {
        System.out.println("onDestroy");
        super.onDestroy();
    }
```
运行点击按钮显示AnotherFragment，后台输出：
```
05-08 03:26:48.192    9321-9321/com.zhang.learnfragment I/System.out﹕ onCreate
05-08 03:26:48.192    9321-9321/com.zhang.learnfragment I/System.out﹕ onCreateView
```
退出时输出：
```
05-08 03:32:10.003  11763-11763/com.zhang.learnfragment I/System.out﹕ onPause
05-08 03:32:10.018  11763-11763/com.zhang.learnfragment I/System.out﹕ onDestroy
```

下面讨论第二个fragment把第一个fragment覆盖的情况。
将MainActivityFragment.java修改如下:
```
public class MainActivityFragment extends android.app.Fragment{
    public MainActivityFragment() {
    }
    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
		System.out.println("A onCreateView");
        View rootView = inflater.inflate(R.layout.fragment_main, container, false);
        rootView.findViewById(R.id.btnShowAnotherFragment).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                getFragmentManager().beginTransaction().replace(R.id.fragment
                /*主容器(activity_main.xml里的ID)*/, new AnotherFragment()/*新的fragment*/).commit();
            }
        });
        return rootView;
    }

    @Override
    public void onCreate(Bundle savedInstanceState) {
        System.out.println("A onCreate");
        super.onCreate(savedInstanceState);
    }

    @Override
    public void onPause() {
        System.out.println("A onPause");
        super.onPause();
    }

    @Override
    public void onDestroy() {
        System.out.println("A onDestroy");
        super.onDestroy();
    }
```
运行时：
```
05-08 03:38:06.686  14543-14543/com.zhang.learnfragment I/System.out﹕ A onCreate
05-08 03:38:06.686  14543-14543/com.zhang.learnfragment I/System.out﹕ A onCreateView
```
点击按钮显示下一个fragment,我这里两个fragment都在显示，所以出现了这个情况，A并没有onpause
```
05-08 03:39:08.782  14543-14543/com.zhang.learnfragment I/System.out﹕ onCreate
05-08 03:39:08.782  14543-14543/com.zhang.learnfragment I/System.out﹕ onCreateView
```
退出
```
05-08 03:40:34.260  14543-14543/com.zhang.learnfragment I/System.out﹕ A onPause
05-08 03:40:34.260  14543-14543/com.zhang.learnfragment I/System.out﹕ onPause
05-08 03:40:34.272  14543-14543/com.zhang.learnfragment I/System.out﹕ A onDestroy
05-08 03:40:34.272  14543-14543/com.zhang.learnfragment I/System.out﹕ onDestroy
```

(3)带侧边栏的 Activity
新建activity如下：
![image](img/android/50.png)






















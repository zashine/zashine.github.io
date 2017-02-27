---
layout: post
title:  "ButterKnife依赖注入用法"
date:   2017/2/27 22:07:15  
comments: true
categories: android
---

## **ButterKnife** ##

Github地址：[https://github.com/JakeWharton/butterknife](https://github.com/JakeWharton/butterknife)

最新版本ButterKnife8.5.1（截止目前2017/2/27 21:47:25）

![butterknife]({{site.url}}/assets/butterknife/butterknife.jpg "butterknife")

通过注解的方式，将Android View与成员变量和方法绑定起来，形成一种模版样式的代码。

- 在成员变量上使用 **`@BindView`** 替换 **`findViewById`**;
- 快速操作一组View（数组或list）
- 通过使用注解 **`@OnClick`** 消除匿名内部类的方法设置监听器
- 通过使用资源的注释字段消除资源查找

## 配置使用 ##

Android Studio中添加依赖：

	ctrl + alt + shift + s 进入项目project structure,点击modules下当前项目，再点击右侧dependencies——“+” library dependency——搜索butterknife，添加butterknife和butterknife compiler

在当前项目的buile.gradle里面可以看到依赖成功

![Large example image]({{site.url}}/assets/butterknife/butterknife_dependency.jpg "butterknife_compiler")


代码中使用`Butterknife.bind(Activity)`把当前`activity`的布局文件绑定注入

    public class MainActivity extends AppCompatActivity {

    @BindView(R.id.button0)
    Button button0;
    @BindView(R.id.button1)
    Button button1;
    @BindView(R.id.button2)
    Button button2;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
		// 绑定注入
        ButterKnife.bind(this);
    }

    @OnClick({R.id.button0, R.id.button1, R.id.button2})
    public void onClick(View view) {
        switch (view.getId()) {
            case R.id.button0:
                break;
            case R.id.button1:
                break;
            case R.id.button2:
                break;
        }
    }





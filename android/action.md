# dsds

## android在学习——activity关闭和dialog.dismiss冲突的解决(Activity has leaked window com.android.internal.policy.impl.PhoneWindow)



当我们在退出整个程序的时候偶尔会出现这种报错：Activity has leaked window com.android.internal.policy.impl.PhoneWindow
其意思大概就是：窗体已经关闭了但是dialog仍然在显示，Activity has leaked window（activity渗透出窗体），大概就是这个意思。

那么就要在activity finish()之前将dialog dismiss()掉。

我的做法就是重写本activity的onDestroy()方法，在此方法中将dialog清除：

```
    /**
     * 此方法必须重写，以决绝退出activity时 dialog未dismiss而报错的bug
     */
    @Override
    protected void onDestroy() {
        // TODO Auto-generated method stub
        try{
            myDialog.dismiss();
        }catch (Exception e) {
            System.out.println("myDialog取消，失败！");
            // TODO: handle exception
        }
        super.onDestroy();
    }
```

其实就是生命周期的问题

重复添加，或者已有的东西在finish之后再次finish



## android点击空白处软键盘消失 

只需要在页面Activity的代码中重写onTouchEvent事件，即在该页面添加以下代码：

   @Override
    public boolean onTouchEvent(android.view.MotionEvent event) {
        InputMethodManager imm = (InputMethodManager) getSystemService(INPUT_METHOD_SERVICE);
        return imm.hideSoftInputFromWindow(this.getCurrentFocus().getWindowToken(), 0);
    }
    

## android Waiting for Debugger

很多android开发初学者在写好一个小程序后，点击Debug 运行 结果模拟器总是会弹出Waiting for Debugger 然后程序又可以正常运行，于是以为程序出错了，其实这是加载调试环境而已，并不是程序出错，你运行 Run非Debug模式，就不会弹出Waiting for Debugger提示.

 

引用原官网文档说明：

“If debugging, the application will start in the "Waiting For Debugger" mode. Once the debugger is attached, Eclipse will open the Debug perspective.

To set or change the launch configuration used for your project, use the launch configuration manager. See Creating a Launch Configuration for information.”


## jump

scrollview.post(new Runnable() {

@Override
public void run() {
scrollview.scrollTo(70, 0);
}
});
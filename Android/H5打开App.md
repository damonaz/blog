## H5唤醒方式列表
URL Schemes
chrome intent
ios UniversalLink / android appLink

### URL Schemes 可以理解为一种特殊的URL用来定位一个应用以及应用内的某个功能，类比网页链接便很容易理解
[scheme:][//authority][path][?query] 比如：tuyasmart://home?test=1
```
<intent-filter>
    <action android:name="android.intent.action.VIEW" />
    <category android:name="android.intent.category.BROWSABLE" />
    <category android:name="android.intent.category.DEFAULT"/>
    <data
        android:host="myapp"
        android:scheme="app"
        android:path="/wakeapp"
        />
</intent-filter>
h5操作 链接格式例如 app://myapp/wakeapp?param=1
 
客户端取值
Uri uridata = this.getIntent().getData();
String id=uridata.getQueryParameter("param");
```

### chrome intent
安卓的原生谷歌浏览器从chrome25版本之后就不能通过URL Schemes唤醒安卓应用。要使用谷歌官方提供的intent:预发， 如果唤醒失败，则会跳转到谷歌的应用市场。

### Android App Links
安卓App Link的出现原因也是为了优化用户体验，在使用scheme唤醒时会弹出一个对话框提示用户是否打开，并且如果用户勾选了取消之后，可能之后就再也唤醒不了。

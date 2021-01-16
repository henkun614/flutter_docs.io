### 5.3 图片和ICON
Flutter使用Image加载图片，图片的来源可以是assets、文件、内存以及网络
#### 5.3.1 加载本地图片
![alt](assets/icons/icon_shipin.png)
```dart
1. 在assets目录下新建icons目录，用来存放本地图片
2. 在IconFont上下载一个图片放到icons目录下
3. 将图片目录配置到pubspec.yaml文件中，格式如下
assets:
     - assets/icons/icon_shipin.png
4. 使用AssetsImage加载图片
child: Image(
    image: AssetImage("assets/icons/icon_shipin.png"),
    width: 100,
    height: 100,
)
```
#### 5.3.2 使用NetworkImage加载网络图片
![alt](https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=127215917,4280589987&fm=26&gp=0.jpg)
```dart
Container(
    alignment: Alignment.centerLeft,
    child: Image(
        image: NetworkImage("https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=127215917,4280589987&fm=26&gp=0.jpg"),
        width: 200,
        height: 300,
    ),
),
```
#### 5.3.3 使用Image.network加载网络图片
```dart
 Container(
    alignment: Alignment.centerLeft,
    child: Image.network("https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=127215917,4280589987&fm=26&gp=0.jpg"),
    width: 200,
    height: 300,
),
```
#### 5.3.4 Image缩放模式
```dart
//fill 会拉伸填充满显示空间，图片本身长宽比会发生变化，图片会变形,
Container(
        margin: EdgeInsets.all(5),
        child: Image(
            image: NetworkImage(url),
            fit: BoxFit.fill,
            width: 200,
            height: 300,
        ),
),

//cover 会按图片的长宽比放大后居中填满显示空间，图片不会变形，超出显示空间部分会被剪裁
Container(
        margin: EdgeInsets.all(5),
        child: Image(
            image: NetworkImage(url),
            fit: BoxFit.cover,
            width: 200,
            height: 300,
        ),
        
),

//contain 默认的显示规则，长宽比不变，适当缩放以适应当前空间，图片不会变形
Container(
        margin: EdgeInsets.all(5),
        child: Image(
            image: NetworkImage(url),
            fit: BoxFit.contain,
            width: 200,
            height: 300,
        ),
),

//fitwidth 图片的宽度会缩放到显示空间的宽度，高度会按比例缩放，然后居中显示，图片不会变形，超出显示空间部分会被剪裁
Container(
        margin: EdgeInsets.all(5),
        child: Image(
            image: NetworkImage(url),
            fit: BoxFit.fitWidth,
            width: 200,
            height: 300,
        ),
),

//fitHeight 图片的高度会缩放到显示空间的高度，宽度会按比例缩放，然后居中显示，图片不会变形，超出显示空间部分会被剪裁
Container(
        margin: EdgeInsets.all(5),
        child: Image(
            image: NetworkImage(url),
            fit: BoxFit.fitHeight,
            width: 50,
            height: 300,
        ),
),

//none 图片没有适应策略，会在显示空间内显示图片，如果图片比显示空间大，则显示空间只会显示图片中间部分
Container(
        margin: EdgeInsets.all(5),
        child: Image(
            image: NetworkImage(url),
            fit: BoxFit.none,
            width: 200,
            height: 300,
        ),
),

//scaleDown 根据情况适当缩小
Container(
        margin: EdgeInsets.all(5),
        child: Image(
            image: NetworkImage(url),
            fit: BoxFit.scaleDown,
            width: 200,
            height: 300,
        ),
),
```
#### 5.3.5 ICON
上面介绍了通过Image加载本地或者网络图片的相关知识，开发的过程中有时候会需要使用一些小图标，比如底部导航的实现。Flutter内置的ICON部件（ICON部件内置了一组小图标）可以满足类似需求，当内置图标不能满足需求时可以考虑使用自定义ICON。  

**系统内置的ICON**  
![male](https://raw.githubusercontent.com/henkun614/my_pic/master/20210115140442.png)
<style>
img[alt="male"]{
  width:450px;
}
</style>
```dart
Row(
    children: [
        Icon(
            Icons.access_alarm,//图标
            color: Colors.blue,//图标的颜色
        ),
        Icon(
            Icons.ac_unit,
            color: Colors.blue,
        ),
        Icon(
            Icons.zoom_out,
            color: Colors.blue,
        )
    ],
),
```
**自定义ICON**
如果系统自带的ICON不能满足需求，可以考虑使用自定义ICON。步骤如下(以IconFont平台上的图片为例子):
1. 在Iconfont上找到要下载的图片，添加到购物车，然后在购物车中选择下载代码，将资源文件下载到本地(步骤完成之前不要删除，接下来会有用到)
2. 在项目的assets目录下新建fonts文件夹，将刚刚下载的代码文件中的iconfont.ttf文件放到fonts目录下
3. 配置pubspec.yaml文件的fonts节点
```yaml
fonts:
     - family: myIcon #这个一定要有，名字可以随便起一个
       fonts:
        - asset: assets/fonts/iconfont.ttf
```
4. 新建一个dart类，类名任意，主要用来配置IconData
```dart
class MyIcon {
  static const IconData micon =
      IconData(0xe620, fontFamily: 'myIcon', matchTextDirection: true);
}
// 0xe620 这个是之前下载的ttf文件的十六进制码，找到刚才下载的资源文件夹，里边有个demo_index.html，用浏览器打开之后就会看到当前图片对应的十六进制码。
```
5. 使用自定的ICON
上述过程完成之后就可以在界面上引用自定义的ICON类了
```dart
Icon(
    MyIcon.micon,
    color: Colors.blue,
)
```



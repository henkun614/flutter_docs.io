### 5.3 图片和ICON
Flutter使用Image加载图片，图片的来源可以是assets、文件、内存以及网络
#### 5.3.1 加载本地图片
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
#### 5.3.2 加载网络图片

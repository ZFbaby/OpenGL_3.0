# OpenGL_3.0

## 介绍

本工程完全采用OpenGL ES 3.0的API进行实现，目的是更好的使用OpenGL相关功能并移植到移动端项目。

以示例为主，可以作为调参工具，也可以作为学习参考。

## 图片显示

* 将需要显示的图片转成纹理
* 纹理序号将会在渲染线程中传给GPU进行缓存
* OpenGL程序绘制纹理并光栅化显示到窗口

```
// 图片指定存储路径
NSString *imagePath = [[NSBundle mainBundle] pathForResource:@"yourname" ofType:@"png"];
// 转换图片为OpenGL纹理ID
GLKTextureInfo *textureInfo = [GLKTextureLoader textureWithContentsOfFile:imagePath options:@{GLKTextureLoaderOriginBottomLeft : @true, GLKTextureLoaderGenerateMipmaps : @true} error:NULL];
// 存储纹理
self.mTextureId = textureInfo.name;
// 纹理尺寸
_imageSize = CGSizeMake(textureInfo.width, textureInfo.height);
```

<div align=center><img width="225" height="487" src="example_1.png"/></div>

## 动画

* 通过绘制两张不同的图像
* 在切换图像过程中，编写shader，添加一些行为（如：旋转、渐变、缩放、移动等）
* 按指定帧率渲染每一帧图像，得到流畅的动画

<div align=center><img width="225" height="487" src="example_2.png"/></div>

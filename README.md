#PixiJS技术调研文档

### 一.调研目的(需求)

1.PixiJS是否能够解决cocos creator渲染方面的短板问题，PixiJS在开发效率、开发成本方面是否更优。

2.若PixiJS各方面表现更优，是否能完全替代cocos creator作为新的开发引擎。

###二.PixiJS简介、基本原理

PixiJS是一款以WebGL和canvas等作为技术支撑使用javascript开发的HTML5创建引擎。

###三.PixiJS一般开发流程

- 开发流程：

  1.图片、龙骨、音频等资源准备与资源处理。

  2.代码编写，纯h5 web开发方式。

  3.代码合并、压缩、混淆。

  4.项目发布、上线。

- 基本代码结构：

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>test</title>
  </head>
  <body>
      <script>
          /*
          1.构建画布
          */
          let app = new PIXI.Application({
              width: 256,
              height: 256,
              antialias: true,
              transparent: false,
              resolution: 1
          }
          );
          document.body.appendChild(app.view);
          /*
          2.加载所有图片、龙骨和图集资源
          */
          PIXI.loader
              .add("cat", "images/cat.png")
              .load(setup);
          /*
          3.在资源加载完毕的回调函数中进行游戏元素创建和游戏逻辑编写
          */
          function setup(loader, res) {
              //在这里构建游戏元素编写游戏逻辑
              //...
              app.ticker.add(() => {
                  //这里每一帧会执行一次
                  //...
              })
          }
      </script>
  </body>
  </html>
  ```

### 四.cocos creator与PixiJS基础功能对比

######下列统计不考虑引入第三方技术的情况

| 技术/功能                          | cocos creator                       | PixiJS                   |
| ---------------------------------- | ----------------------------------- | ------------------------ |
| 灯光系统                           | 不支持                              | :smile:支持              |
| 自定义着色器、加载外部着色器文件   | 不支持                              | :smile:支持              |
| 碰撞检测、碰撞器分组、不规则碰撞器 | :smile:支持                         | 需自行实现               |
| 可视化UI编辑器                     | :smile:支持​                         | 不支持                   |
| 物理系统                           | :smile:支持​                         | 不支持                   |
| 补间动画系统                       | :smile:支持​                         | 不支持                   |
| 加载和播放龙骨                     | 支持spine和dragonBones              | 支持spine                |
| 音视频播放                         | :smile:均有完备的接口封装和兼容处理 | 音频需使用原生H5自行处理 |
| 瓦片图                             | 支持                                | 支持                     |
| 图集功能                           | 支持                                | 支持                     |

###五.cocos creator与PixiJS引擎特性对比

|                | cocos creator                                                | PixiJS                                                       |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 技术定位       | 跨平台游戏引擎框架                                           | HTML5创建引擎                                                |
| 是否开源免费   | 是                                                           | 是                                                           |
| 热度           | github star数量: <br />cocos2d-x: 12936, cocos2d-html5: 2511 | :smile:github star数量:<br />22294                           |
| 专门的技术社区 | :smile: 中文社区<https://forum.cocos.com/>  , 国内技术生态活跃 | 国外的h5游戏论坛有PixiJS专区(英文) <http://www.html5gamedevs.com/forum/15-pixijs/> |
| 产品可发布平台 | :smile:安卓、ios、web、微信小游戏、facebook小游戏            | 仅web形式                                                    |
| 开发模式       | 完全组件化                                                   | H5网页开发                                                   |
| 主要开发语言   | Javascript                                                   | Javascript                                                   |
| 开发效率       | :smile:高                                                    | 相对cocos creator较低                                        |
| 学习成本       | :smile:低                                                    | 中等                                                         |
| API特点        | 高度封装                                                     | 轻量封装、更灵活                                             |
| 渲染模式       | webGL和canvas                                                | webGL和canvas                                                |

### 六.PixiJS开发案例

- 官方demo地址(多个)：<https://pixijs.io/examples/#/basics/basic.js>

- 我的demo"小鸭子捡宝箱"地址(连接"APP-Test"访问)：<http://10.4.39.23:9090/>

  我的demo"小鸭子捡宝箱"源码：https://github.com/likek/PixJS-demo.git

  "小鸭子捡宝箱"中使用到的技术点：`碰撞检测`、`音频播放`、`shader技术(着色器)` 、`精灵`、`瓦片图`、`事件系统`、`文本`、`spine龙骨动画`、`灯光系统`等

### 七.总结

1.对于cocos creator无法实现的渲染方面相关的需求，可以引入PixiJS进行解决，例如灯光和滤镜。😘

2.PixiJS学习成本相对cocos creator较高，但总体适中。😘

3.PixiJS技术生态活跃度相对较低。

4.PixiJS游戏开发效率相对cocos creator较低，在UI层面不够友好，对团队成员代码能力要求更高。

5.从开发效率、社区活跃度和引擎功能等方面来看，目前工作中暂时__无法完全替代cocos creator__作为团队新的开发引擎。

6.因为没有足够的外部技术支持和技术社群支持，使用PixiJS进行开发__后期风险相对较高__。





---

作者:  李可可

最后编辑日期：2019/03/22
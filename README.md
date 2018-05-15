
canvas小游戏指南
### 1.布局
> 绘制背景及图片按照实际图片大小绘制,比如
- 现获取图片的宽高
```
 this.w = game.allImg["bg_day"].width;
 this.h = game.allImg["bg_day"].height;
```
- 绘制背景，每一帧都需要向左移背景，让他动起来，当向左移动的时候右侧会露底，在这里多增加几张图片，当移动的x距离等于一屏宽的时候，让x = 0
```
  game.draw.fillStyle = "#4ec0ca";
  game.draw.fillRect(0, 0, game.canvas.width, game.canvas.height)
  game.draw.drawImage(game.allImg["bg_day"], this.x, game.canvas.height - this.h)
  game.draw.drawImage(game.allImg["bg_day"], this.x + this.w, game.canvas.height - this.h)
  game.draw.drawImage(game.allImg["bg_day"], this.x + this.w * 2, game.canvas.height - this.h)
```
### 2.随机长度的管道
> 绘制随机长度管道，不仅感到高度要随机生成，绘制的时候 参数变为9个 drawImage(img,x1,y1,w1,h1,x2,y2,w2,h2)
- 第一个参数绘制的图片
- x1(图片裁剪的起始x坐标) y1(图片裁剪的起始y坐标) x2(图片绘制到画布的其实x坐标) y2(图片绘制到画布其实y坐标)
- w1,h1,w2,h2(图片宽高)
### 3.小鸟的飞行
> 小鸟与管道的碰撞检，当前一屏显示的管道都会存在数组中，因为管道是长度不等的，我们检测小鸟与每一条管道的碰撞

![](https://user-gold-cdn.xitu.io/2018/5/15/16361b41fc95607f?w=1076&h=673&f=png&s=24469)
发生碰撞的条件
- B.x2 > = P.x1
- B.x1 < = P.x2
- B.y1 < = p.y1
- B.y2 > = this.space + P.y1






![](https://user-gold-cdn.xitu.io/2018/5/15/16361c7f04234691?w=400&h=696&f=gif&s=4310252)
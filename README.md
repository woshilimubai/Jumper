# Jumper

> 使用Python 和 OpenCV 玩微信跳一跳
> 运行所需要的python模块
>
> - opencv-for-pyhton
> - numpy
> - win32api，win32con
> - random

## 这个程序很赞！

## 我遇到的问题
* 出现了一条很长的线，然后图像不会更新，等着错误次数超过10，即fault > 10 时，该程序会结束运行。
[跳一跳错误01.png](http://upload-images.jianshu.io/upload_images/6328913-29d98d380a939f42.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 解决方法:
> 更改了`dist < 50 or dist > 700`的处理方法，更改后的方法是，当出现上述问题是，让鼠标模拟点击一下手机的屏幕。
```python
# 更改后的代码
if(dist < 50 or dist > 700):
    fault = fault + 1          # will be reset
    fault_cnt = fault_cnt+1    # not not be reset
    cv2.waitKey(2000)
    if fault > 3:
        click_x = 150 + random.randint(-60, 60)  # 防作弊，变换点击位置
        click_y = 500 + random.randint(-20, 20)
        click(click_x, click_y, 0.015)
        fault = 0
                #exit()
    continue
```
## 参考链接
[简书教程](https://www.jianshu.com/p/c5138500afbf)
[测试视频](http://v.youku.com/v_show/id_XMzM0MjU1NjY5Ng)

# CVFX_H4
# Infinite Zooming



# Outline
- **校內景觀**
- **抽取特徵 & match結果 & 使用不同特徵提取器**
- **影像對齊&infinite zoom**
- **Image Stitch**
- **結論**

# 校內景觀
| 台達                               | 水木                               | 實齋                             |
|------------------------------------|------------------------------------|------------------------------------|
| ![](https://imgur.com/3oRlyHt.gif) | ![](https://imgur.com/JfWiefQ.gif) | ![](https://imgur.com/yqKM8Cl.gif) |

![](https://imgur.com/3oRlyHt.gif)
![](https://imgur.com/JfWiefQ.gif)







# 抽取特徵 & match結果 & 使用不同特徵提取器 



### 使用 brief & brief_knn 來 match（應用在TA的兩張影像）
|       | bf                                   | bf_knn                               |
|-------|--------------------------------------|--------------------------------------|
| orb   | ![](https://i.imgur.com/lBLZsp8.jpg) | ![](https://i.imgur.com/5a7885N.jpg) |
| AKAZE | ![](https://i.imgur.com/WsG8CYp.jpg) | ![](https://i.imgur.com/B2WYfF1.jpg) |
| SIFT  | ![](https://i.imgur.com/lPS15mZ.jpg) | ![](https://i.imgur.com/1mKCDry.jpg) |
| surf  | ![](https://i.imgur.com/EjZwaKm.jpg) | ![](https://i.imgur.com/P47aiYN.jpg) |
| brief | ![](https://i.imgur.com/LKroHQu.jpg) | ![](https://i.imgur.com/arTtKGR.jpg) |
| brisk | ![](https://i.imgur.com/sn2EBAp.jpg) | ![](https://i.imgur.com/dnBEklZ.jpg) |

### Matching with flann & flann_knn（應用在TA的兩張影像）

|       | flann                                | flann_knn                            |
|-------|--------------------------------------|--------------------------------------|
| orb   | ![](https://i.imgur.com/kMbBHLR.jpg) | ![](https://i.imgur.com/veY5AeN.jpg) |
| AKAZE | ![](https://i.imgur.com/g2t5Sk0.jpg) | ![](https://i.imgur.com/mpnPIAz.jpg) |
| SIFT  | ![](https://i.imgur.com/iiBmKWb.jpg) | ![](https://i.imgur.com/oGwuXmy.jpg) |
| surf  | ![](https://i.imgur.com/xd3Il8E.jpg) | ![](https://i.imgur.com/i7SlkoR.jpg) |
| brief | ![](https://i.imgur.com/RxJhYgs.jpg) |                                      |
| brisk | ![](https://i.imgur.com/h2V1Swl.jpg) |                                      |


# infinite zoom
飄來飄去
![](https://imgur.com/352139z.gif)

葉子の流
![](https://imgur.com/q1TjE6h.gif)




# Image Stitch 


**原始圖片如下**
| ![](https://i.imgur.com/60pROsk.jpg) | ![](https://i.imgur.com/kGBxn3Q.jpg) |
|--------------------------------------|--------------------------------------|

**抓取各自的特徵 並 完成拼接**
| ![](https://i.imgur.com/2FV7afL.jpg) |
|--------------------------------------|
| ![](https://i.imgur.com/kfCjlyv.jpg) |



# 結論


| 方法                                      | 評估                                                                                                                                                                                                                                                                              |
|-------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 抽取特徵 & match結果 & 使用不同特徵提取器 | 對於特徵提取的結果，我們對比了ORB,AKAZE,SIFT,SURF,brief,brisk六種特征提取器以及四種matching方法（brief,brief+knn,flann,flann+knn）可以看到，各自的效果都不差，但是 由於flann_knn+brief & flann_knn+brisk 這兩部分實踐在參數這上有問題，所以就沒有show出結果，總體來說效果還不錯。 |
| 影像對齊                           |                                                                                                                                                                                                                                                                                   |
| infinite zoom                             | 對於對校內場景做infinite zoom，我們認為不太容易，因為有行人和汽車的影響，所以向內                                                                                                                                                                                                 |
| image stitch                              | 效果很不錯，除了中間的拼接上有色差，如果去除色差，則看不出來有兩張圖拼接的痕跡。                                                                                                                                                                                                  |





































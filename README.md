# Infinite Zooming



# Outline


- **取景與校內**


- **抽取特徵 & match結果 & 使用不同特徵提取器**

- **infinite zoom**

- **Image Stitch**


- **Image alignment** 





- **結論**

# 取景與校內

| 台達                               | 水木                               | 實齋                             |
|------------------------------------|------------------------------------|------------------------------------|
| <img src="https://i.imgur.com/lJUl7lo.gif" width="255"> | <img src="https://i.imgur.com/IEMn00b.gif" width="255"> | <img src="https://imgur.com/yqKM8Cl.gif" width="255"> |


如果看不到gif，點擊這裡([台達](https://imgur.com/3oRlyHt.gif)，[水木](https://imgur.com/JfWiefQ.gif)，[實齋](https://imgur.com/yqKM8Cl.gif))




# 抽取特徵 & match結果 
抽取特徵 : orb, AKAZE, SIFT, surf, brief, brisk
特徵匹配 : BFMatcher, BFMatcher_knn, flann, flann_knn

### 使用 BFMatcher & BFMatcher_knn 來 match（應用在TA的兩張影像）
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
| brief | ![](https://i.imgur.com/RxJhYgs.jpg) |        not work                      |
| brisk | ![](https://i.imgur.com/h2V1Swl.jpg) |         not work                     |


# infinite zoom

* **飄來飄去**


![](https://imgur.com/352139z.gif)

* **葉子の流**


![](https://imgur.com/q1TjE6h.gif)



# Image Stitch 


**原始圖片如下**

| ![](https://i.imgur.com/kGBxn3Q.jpg) |  ![](https://i.imgur.com/60pROsk.jpg) |
|--------------------------------------|--------------------------------------|


**抓取各自的特徵 並 完成拼接**


| ![](https://i.imgur.com/2FV7afL.jpg) |
|--------------------------------------|
| ![](https://i.imgur.com/kfCjlyv.jpg) |


# Image aligtnment

**原始圖片如下**

| ![](https://i.imgur.com/8YFpdi6.jpg) | ![](https://i.imgur.com/MgdzpyQ.jpg) |
|--------------------------------------|--------------------------------------|


**抓取各自的特徵 並 完成對齊後的影像**

| ![](https://i.imgur.com/BAilFci.jpg) |
|---------------------------------------------|
| ![](https://i.imgur.com/eoJ4fLy.jpg) |



# 結論


| 方法                                      | 評估                                                                                                                                                                                                                                                                              |
|-------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 抽取特徵 & match結果 & 使用不同特徵提取器 | 對於特徵提取的結果，我們對比了ORB,AKAZE,SIFT,SURF,brief,brisk六種特徵提取器以及四種matching方法（brief,brief+knn,flann,flann+knn）可以看到，各自的效果都不差，但是 由於flann_knn+brief & flann_knn+brisk 這兩部分實踐在參數這上有問題，所以就沒有show出結果，總體來說效果還不錯。 |
| image alignment        | 效果不錯，即使把不同角度的影像倒轉後還能達到對齊的效果，且對齊的影像會根據所參考的影像特徵點的位置，將自身圖像進行裁切，所以它們沒有重叠的部分就會因爲對齊而丟失                                                                                                                                                                                                                                                                                                   |
| infinite zoom                             | 對於對校內場景做infinite zoom，我們認為不太容易，因為有行人和汽車的影響，所以向內                                                                                                                                                                                                 |
| image stitch                              | 效果很不錯，除了中間的拼接上有色差，如果去除色差，所以就看不出來有兩張圖拼接的痕跡，效果還不錯，但因為沒有時間，如果有時間使用Photoshop的話，會更加完美。                                                                    |

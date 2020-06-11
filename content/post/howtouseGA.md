---
title: "Hugo新增流量追蹤功能(Google_Analytics)"
date: 2020-06-11T16:41:16+08:00
draft: false
description : "
擁有了網站，想必如何追蹤自己的網站的訪客(流量)
也是不可或缺的，因此我們需要兩個步驟來達成。"
author: "ERu"
font: "黑體"
categories : [ "Hugo", "Google_Analytics","GA" ] 
---

擁有了網站，想必如何追蹤自己的網站的訪客(流量)
也是不可或缺的，因此我們需要兩個步驟來達成。

1. 申請GA的帳號
2. 將GA的功能加入網站內

## 申請Google Analytics (GA)的帳號

首先我們需要先到GA的官網點選"開始測量"
https://analytics.google.com/
![image](/images/GA/GA1S.png)

填入想要的帳戶名稱，並點選下一步
![image](/images/GA/GA2S.png)

因為我們希望能追蹤網站的訪客，所以在這步點選網站，並點選下一步
![image](/images/GA/GA3S.png)

填入想要的網站名稱、需要追蹤的網站網址，並點選下一步
![image](/images/GA/GA4S.png)

到這步就算完成了申請，但先不要關閉此網頁，這一步的"追蹤ID"及"全域網站代碼"
會需要在下一步加入至網站的原始碼內
![image](/images/GA/GA5S.png)

## 將GA的功能加入網站內

開啟Hugo網站根目錄的config.toml
並且加入以下的程式碼並儲存

    googleAnalytics = "UA-XXXXXX" //UA-XXXXXX 需更換為追蹤ID

開啟根目錄的\layouts中找到"partials"和"_internal"兩個目錄(若無請自行新增)  
接著進到網站套用的主題目錄中的  
\layouts\partials\head.html 或  
\layouts\partials\header.html  
複製到剛剛找到(建立)的partials裡
![image](/images/GA/GA11.png)

將head.html 或header.html 新增以下程式碼

    {{ template "_internal/google_analytics_async.html" . }}


再到剛剛找到(建立)的_internal裡，新增一個檔案名  
"google_analytics_async.html"，並將全域網站代碼複製到此檔案並儲存。

### 此時僅需發布您的網站即可於GA首頁查詢流量了
![image](/images/GA/GA12S.png)








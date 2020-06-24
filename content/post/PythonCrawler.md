---
title: "簡易網路爬蟲(Python)"
date: 2020-06-24T19:32:11+08:00
draft: false
description : "將搜尋到的網頁的資料收集起來並且製成表格需要3個工具"
author: "ERu"
font: "黑體"
tags : ["Python應用"]
categories : [ "Python", "Crawler","網路爬蟲" ] 
---

將搜尋到的網頁的資料收集起來並且製成表格需要3個工具

## 所需工具

1. requests       下載網頁原始碼
2. BeautifulSoup  擷取原始碼中所需的資料
3. pandas         將資料轉換為表格

以下範例會抓取我自己的blog為例

## 下載網頁原始碼

程式碼:

	#use requests
	import requests 
	
	# target page
	url = "https://eru085730.github.io/"

	# crawler page
	craw = requests.get(url)

	#set the val save the data
	w_content = craw.text


## 擷取原始碼中所需的資料

我希望能夠抓取每一篇文章的標題，因此從下方圖片  
可以發現標題是被放在"<h1 class="posr-title""裡面  
，所以我們可以這樣擷取

![image](/images/Crawler/C1.png)

程式碼:

	#use BeautifulSoup	
	from bs4 import BeautifulSoup

	#decode  html data
	soup = BeautifulSoup(w_content, 'lxml')

	#find target element
	t_element = soup.find_all('h1', class_="post-title")
	t_element
	
	#data put in an
	da = [e.text for e in t_element ]
	da
	an = []
	for bn in zip(da):
        	bn = str(bn)
        	bn= bn[4:len(bn)-5]
        	an.append(bn)

## 將資料轉換為表格

程式碼:

	#use pandas
	import pandas as pd

	sh = pd.DataFrame({
	   "Title" : an
	})

	sh.head()

## 成果

程式碼:

	import requests
	import pandas as pd
	from bs4 import BeautifulSoup
	
	# target page
	url = "https://eru085730.github.io/"
	
	# crawler page
	craw = requests.get(url)
	
	#set the val save the data
	w_content = craw.text
	
	#decode  html data
	soup = BeautifulSoup(w_content, 'lxml')
	
	#find target element
	t_element = soup.find_all('h1', class_="post-title")
	t_element
	
	#data
	da = [e.text for e in t_element ]
	da
	
	an = []
	for bn in zip(da):
        bn = str(bn)
        bn= bn[4:len(bn)-5]
        an.append(bn)
        
	sh = pd.DataFrame({
	    "Title" : an
	})
	
	sh.head()

![image](/images/Crawler/C2.png)

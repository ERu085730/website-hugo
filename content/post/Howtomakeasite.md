---
title: "Hugo & Github 如何快速(半自動)更新網站(windows10)"
date: 2020-06-09T14:26:32+08:00
draft: false
description : "Sample article showcasing basic Markdown syntax and formatting for HTML elements."
author: "ERu"
---

>當你寫好一篇又一篇的新文章卻發現網站沒有
將你的內容更新上去，因此你只好上網搜尋，
卻發現需要一步一步將之前所打過的指令重新
打過一次，但人是懶惰的，所以我們就需要將
上述的動作自動上傳因此我們需要使用以下工
具。

>## Batch file(批次檔)

批次檔可以將windows上的許多指令通通濃縮到
個檔案之中，只需要執行寫好的批次檔，便能夠
一次完成，甚至也能夠使用工作排程器，讓他在
電腦的特定狀況或時間下自動執行。

>## 如何自動更新網站

在此我們就不介紹Batch file的一些指令，直接
教大家如何操作

1. 首先創建一個.txt檔將其更改為.bat檔
2. 對其點右鍵編輯
3. 輸入以下的文字

	g:                   //需更改為安裝Hugo的磁碟 例如: C: 或  D:
	cd \Hugo\first_site  //cd \後為Hugo安裝後所在網頁的路徑

	hugo

	cd public
	git init
	git remote add origin https://github.com/ERu085730/ERu085730.github.io.git
	git add .
	git commit -m "Initial commit"
	git push -u origin master

	cd ../
	git init
	git remote add origin https://github.com/ERu085730/website-hugo.git
	git add .
	git commit -m "Initial commit"
	git push -u origin master


4. 將其儲存
5. 撰寫文章 or更新內容
6. 開啟此.bat檔

>### 若完成以上步驟，之後使用僅需 操作5、6兩步驟即可快速上傳新增的內容
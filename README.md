# 這是一個可以畫出歷年股價與均線的小作業
```python
# In[]輸入股票代號
stockname = input("請輸入台灣股票名稱或代號")

if stockname.isdigit() == True:
    stockID = stockname+".TW"
else:
    condition = stockdata["StockName"] == stockname
    stockID = str(stockdata[condition].iloc[0]["StockID"])+".TW"
    
# In[]輸入時間
date1 = psr.parse(input("請輸入查詢起始日期"))
date2 = psr.parse(input("請輸入查詢截止日期"))
startdate = date1.date()
enddate = date2.date()



# In[]畫圖
close_price = ggdata["Close"]
close_price.plot(label="收盤價")
close_price.rolling(window = 20).mean().plot(label="20MA")
close_price.rolling(window = 60).mean().plot(label="60MA")


plt.title("{} {}~{} 收盤價".format(stockID, startdate,enddate))
plt.xlabel("日期")
plt.ylabel("股價")
plt.legend(loc='best')
plt.show()
```
[如下圖](https://upload.cc/i1/2020/12/24/hop2ty.png)

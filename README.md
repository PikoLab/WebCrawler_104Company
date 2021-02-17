# 【第一部分：104人力銀行網站爬蟲】¶
關鍵字設定：針對有興趣的關鍵字「數據分析」進行搜索；並限定搜索範圍為「台北地區」、「最近一個月內更新」、「全職工作」。

蒐集資料欄位包括：公司名稱、職稱、產業、薪資待遇、工作技能要求。

使用套件說明
利用requests套件與網頁伺服器連線

利用selenium套件連續爬取多個頁面

利用bs4(BeautifulSoup)套件解析HTML格式，並爬取所需欄位

利用json套件，爬取所需欄位

# 【第二部分：資料清洗】
網路爬蟲完成後，得到需要的欄位，其中「工作技能」各家公司標註的技能不同，種類相當繁雜，為了增加資料的可讀性，進行資料清洗

1.利用pd.get_dummies進行資料標籤編號，將每一個工作技能，以獨立欄位標示。0無要求，1(或>1)為有要求。

2.欄位整併：將工作技能同義字欄位合併，例如：['ANSI SQL', 'MS SQL', 'MySQL', 'PL/SQL', 'PostgreSQL']，均視為SQL

3.刪除欄位：刪除多餘的同義字欄位，與基本技能例如打字能力、MS Office等

4.調整工作技能欄位排序：將各項技能進行加總，加總數量越多(工作技能出現越多次)，工作技能排序越前，例如EXCEL/VBA> SQL> Python> Google Analytics> R....

5.最後依據「公司名稱」進行排序，將同一家公司開出的職缺放在一起，方便閱讀。

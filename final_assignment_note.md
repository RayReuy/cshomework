# Linux3
## 正規表達法 Regular Expression
正規表達法是透過一些特殊符號來比對字串的方法，並可對符合比對條件的字串進行搜尋、萃取、替代、轉換等等
## 正規表達法 (國際模式比對字符)
>1. [:alnum:]__代表英文大小寫字元及數字，亦即0-9，A-Z，a-z
>2. [:alpha:]__代表任何英文大小寫字元，亦即A-Z，a-z
>3. [:lower:]__代表小寫字元，亦即a-z
>4. [:upper:]__代表大寫字元，亦即A-Z
>5. [:digit:]__代表數字而已，亦即0-9
>6. [:punct:]__代表標點符號，亦即 : ' ? ! ; : # $ @ ...
>7. [:blank:]__代表空白鍵與[Tab]按鍵兩者
>8. [:cntrl:]__代表鍵盤上面的控制按鍵，亦即包括CR，LF，Tab，Del..等等
>9. [:graph:]__除了空白字元(空白鍵與[Tab]按鍵)外的其他所有按鍵
>10. [:print:]__代表任何可以被列印出來的字元
>11. [:space:]__任何會產生空白的字元，包括空白鍵，[Tab]，CR等等
>12. [:xdigit:]__代表16進制的數字類型，因此包括:0-9，A-F，a-f的數字與字元
## 正規表達法 (特殊字符)
>1. ^ _ 搜尋規則前的「開頭」.意思代表「非」
>2. $ _ 搜尋規則後的「結尾」
>3. . _ 任意一個字元
>4. * _ 任意字元或任意字串，單一字元或群組出現任意次數
>5. .* _ 一起使用代表任意字串
>6. + _ 單一字元或群組出現至少一次
>7. ? _ 單一字元或群組出現至少0次或1次
>8. {n,m} _ 比對前一個字元至少n次，至多m次，m、n皆為正整數
>9. [] _ 比對範圍內的字元或字串
>10. [^] _ 比對不再指定範圍內的字元
>11. \ _ 特別序列的起始字元
## 正規表達法講解
> 1. +【加號】__跟星號類似，差別在於至少要與前一個字比對一次或以上。
> EX：sky+blue → skyblue(y出現1次)、skyyyblue(y出現多次)
> 2. |【直線】__或者。
> EX：想找到Facebook、Instagram、Wordpress、Google相關的文章，可以使用Facebook | Instagram | Wordpress | Google
> 3. ^【插入符號】和 $【錢字符號】__ ^插入符號是比對前開頭，$錢字符號則是比對結尾。
> EX：^eat → eat、eatenEX：eat$ → creat、peat、leat
> 4. \【反斜線】__將任何特殊字元，恢復成一般字元。
> EX：transbiz\.com → transbiz.com
> 5. ()【括號】__把想找的相關字詞放入括號內，可依照括號裡的字元排序找到可能的結果。
> EX：(sym) → sympathy、symbol、assym等
> 6. []【中括號】__任意比對字串內的每個項目。
> EX：product[DEFG] → productD、productE、productF、productG
# grep 語法
## 可從資料或檔案中，使用關鍵字或正規表達法(Regex)找出想要的內容
grep [option] filename
# grep 參數
●　-i → 忽略大小寫
●　-n → 顯示匹配行及行號
●　-r → 遞歸顯示目錄
●　-c → 只輸出匹配行的計數
●　-v → 只列出不符合的內容
●　--color　=　never|always|auto → 顏色標示
●　-A → 多顯示匹配行的後幾行
●　-B → 多顯示匹配行的前幾行
●　-C → 多顯示匹配行的前後幾行
# Linux4
## grep / awk 講解與實作
## awk 
常用在對文字和資料進行分析處理 | 檔案逐行的讀入 | 以空格為預設分隔符號
## awk Script
awk 'BEGIN{ print "start" } pattern{ commands } END{ print "end" }' filename
工作原理: ○ 第一步執行BEGIN 語句 | ○ 第二步從檔案或標準輸入讀取一行，然後再執行pattern語句，逐行掃描檔案到檔案全部被讀取 | ○第三步執行END語句awk 'BEGIN{ print "start" } pattern{ commands } END{ print "end" }' filename
## awk 語法
awk  [options]  ‘scripts’  var=value  filename
## awk print record & field
awk '{print $1, $2, $4}' fruit.txt
## awk 參數
>1. $0  當前record(列、橫行)
>2. $1~$n  當前record的第N個欄位
>3. FS  輸入field直欄分隔符（-F相同作用）預設空格
>4. RS  輸入record(列、橫行)分割符，預設換行符
>5. NF  欄位個數 | NR  record數，就是行號，預設從1開始
>6. OFS  輸出欄位分隔符，預設空格
>7. ORS  輸出resord分割符，預設換行符
## awk 算術運算子
awk '$2 + $3 >= 160 {print $0}' filename
## awk 關係運算子
awk '{if ($3 == 120) print $0}’ filename
## awk 邏輯運算子
awk '($2 > 6) && ($3 >= 150) {print $0}’ filename
## awk 正則運算子
awk '{if ($3 ~ /0/) print $0}’ filename
## awk 賦值運算子
Example : awk '{for (j=1; j <= NF; j++) { print $j }}' filename
# Git1
## sed 文字分析工具
●「stream editor 」的縮寫，顧名思義是進行串流(stream) 的編輯 | ●字串取代、複製、刪除的功能 | ●自動化的修改文字檔
## Sed指令
sed [option] “[n1,n2] [command] / [pattern] / [replacement] / [flag]” file.txt
## Sed語法-常用選項
sed [-nefi] “[n1,n2] [command] / [pattern] / [replacement] / [flag]” file.txt
## Sed語法-常用指令
sed [-nefi] “[n1,n2] [command] / [pattern] / [replacement] / [flag]” file.txt
## Sed語法-常用旗幟
sed [-nefi] “[n1,n2] [command] / [pattern] / [replacement] / [flag]” file.txt
## Sed應用-- s搜尋並取代
sed -e ‘s/a/A/1’ apple.txt | sed ‘s/a/A/g’ apple.txt
## Sed應用 -- -n沉默模式+p 只印出受影響的行
sed -n ‘s/a/A/p’ apple.txt | sed -n ‘s/a/A/p’ apple.txt > apple_output.txt
## Sed應用-- -f 讀取檔案手稿
sed -f apple_command.txt apple.txt
## Sed應用-- a新增, c取代, d刪除
sed '1a apple apple apple' apple.txt | sed -i '2,3c hahaha' apple.txt | sed 1,5d apple.txt
## Sed應用-- s搜尋並取代+正規表達法
sed 's/.e/E/g' apple.txt
## Sed應用-- s搜尋並取代(多個)&存檔
sed 's/pen/pencil/; s/have/had/' apple.txt | sed 's/pen/pencil/; s/have/had/' apple.txt > apple_output.txt
# Grep, Awk, Sed 比較
## ● grep：文字搜尋工具
○ 可用正規表達法，找出匹配的內容
## ● sed ：是一種線上編輯器
○ 它一次處理一行內容，可搭配正規表達法○主要用來自動編輯一個或多個檔案，簡化對檔案的反覆操作○用於行間的內容操作,如增刪改,查詢替換
## ● awk：文字分析工具
○ 逐行的讀入，可搭配正規表達法○主要用在對文字和資料進行分析處理，以空格為預設分隔符號○同時也是程式語言○用於處理有欄位規則的行內內容,並支援格式化輸出
## Git 連結帳號至 Github
> 1. $ git config --global user.name “Your Name”
> 2. $ git config --global user.email “your@gmail.com”21
# Thanks for your watching!




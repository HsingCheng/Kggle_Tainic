# 1.緒論
在Kaggle上鐵達尼號是一個經典的且適合初學者的比賽。建立一個機器學習模型來預測乘客是否生還。

# 2.資料介紹

詳細變數意義，可以參考 [kaggle](https://www.kaggle.com/c/titanic/data)的敘述

|Variable|Definition|Key|
|survival|Survival|	0 = No, 1 = Yes|
|pclass|Ticket class|	1 = 1st, 2 = 2nd, 3 = 3rd|
|sex|Sex	||
|Age|	Age in years|	|
|sibsp|	# of siblings / spouses aboard the Titanic	||
|parch|	# of parents / children aboard the Titanic	||
|ticket|	Ticket number	||
|fare|	Passenger fare	||
|cabin|	Cabin number	||
|embarked|	Port of Embarkation|C = Cherbourg, Q = Queenstown, S = Southampton|

### 2.1資料準備
|data|n (資料筆數)|p (變數數量)|
|training data|891 筆|4個類別變數，7個數值變數|
|testing data|418 million 筆|4個類別變數，7個數值變數|

# 3.資料分析

我認為PassengerId、Name、Cabin和ticket這四個變數對於預測乘客存活沒有太大關連因此沒有選用。

### 3.1遺失值
變數age以及fare有null值，因此我分別都利用mean來取代null值。

### 3.2變數轉換
sex欄位原本為female及male轉換成數字0，1。

### 3.3onehot encoding
embarked欄位為類別資料因此利用onehot encoding方式做dummy variable。

# 4.Model
我選用Keras並建立MLP模型。
|層數|輸入的神經元|輸出的神經元|激活函數|
|隱藏層1|9 個|40 個|relu|
|隱藏層2|40 個|30 個|relu|
|輸出層1|30 個|1 個|sigmoid|

|data|size|n (資料筆數)|p (變數數量)| 時間長度 |在 R 中佔的 ram |
|----|----|-----------|------------|------|---------------|
|training data|3 GB|74 million 筆|8個類別變數，5個數值變數| week 3 ~ week 9| 3.6 GB |
|testing data|239 MB|7 million 筆|8個類別變數，5個數值變數|week 10 ~ week 11| 0.2 GB |

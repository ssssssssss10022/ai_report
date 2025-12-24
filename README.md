# Colab訓練YOLO v5實現口罩偵測

本文介紹在Googlecolab上訓練yolov5進行目標偵測的基本流程。 yolo系列模型是目前最先進的目標偵測模型之一。 YOLO V5效能與YOLO V4不相伯仲，但其個頭比V4小得多，模型訓練速度也要快上不少。

本文前置條件：為了能夠存取Colab，需要電腦能夠科學上網。

Colab是Google提供的線上jupyter筆記本，其為勞苦大眾提供了6個小時連續白嫖Tesla GPU的機會（一次使用不超過6個小時，到點兒了會自動斷開連接）。另外Colab提供了多種深度學習框架支援（TensorFlow，PyTorch等），這對於學習者來講是非常不錯的運算資源。

Colab網址：(https://colab.research.google.com/notebooks/welcome.ipynb)  

## 1.設定計算環境

進入Colab後第一步是新建一個筆記本，如下圖所示。

![image](https://github.com/kevin945290/AI_report/blob/main/1.png)

修改檔名，並點選"+程式碼"新增程式碼區塊
![image](https://github.com/kevin945290/AI_report/blob/main/2.png)

現在，我們就可以在程式碼框中輸入一些程式碼。這裡注意，如果我們直接輸入程式碼，系統就會當作Python程式碼執行。例如我們輸入：  
a = 1  
print(a)  
運行之後輸出框中會列印出"1"。
![image](https://github.com/kevin945290/AI_report/blob/main/3.png)

如果想去執行系統指令，只需要在指令前加感嘆號!。例如我們輸入：  
!ls  
![image](https://github.com/kevin945290/AI_report/blob/main/4.png)

## 前期配置
修改筆記本環境
![image](https://github.com/kevin945290/AI_report/blob/main/5.png)

硬件類型從CPU改成GPU
![image](https://github.com/kevin945290/AI_report/blob/main/6.png)

連接Google drive:首先在儲存格中輸入並執行以下命令，會出現2次校驗
![image](https://github.com/kevin945290/AI_report/blob/main/7.png)

會發現上面的程式碼的授權網站無法進入,因為版本過舊
![image](https://github.com/kevin945290/AI_report/blob/main/8.png)

掛載Google Drive程式碼：
![image](https://github.com/kevin945290/AI_report/blob/main/9.png)

會發現上面的程式碼的授權網站也無法進入
![image](https://github.com/kevin945290/AI_report/blob/main/A.png)

所以改用其他方式，一開始沒掛載雲端，如圖:
![image](https://github.com/kevin945290/AI_report/blob/main/B.png)

所以我們用了最新版本的掛載雲端方式，載入成功之後在左邊的檔案中多了一個dirve資料夾，如下圖:
![image](https://github.com/kevin945290/AI_report/blob/main/C.png)

掛載完後，我們可以用命令"!ls"查看
![image](https://github.com/kevin945290/AI_report/blob/main/D.png)

## 更改工作目錄
在Colab中cd指令是無效的，切換工作目錄使用chdir函數，執行完後，目前工作目錄會進入drive資料夾下。我們再使用!ls指令會發現系統輸出的是drive資料夾下的目錄
![image](https://github.com/kevin945290/AI_report/blob/main/E.png)

用" os.chdir('../') "，可回到上級目錄，執行完後，目前工作目錄會回到上級目錄。之後我們再使用!ls指令來觀察
![image](https://github.com/kevin945290/AI_report/blob/main/F.png)

## 運行自己的程式碼
### 1. 將.py檔案和其它必要的檔案上傳到Google Drive
![image](https://github.com/kevin945290/AI_report/blob/main/G.png)

### 2. 將工作目錄切換到.py檔案所在目錄
![image](https://github.com/kevin945290/AI_report/blob/main/H.png)

### 3. 運行程式碼
![image](https://github.com/kevin945290/AI_report/blob/main/I.png)

### 4. 注意事項  
Linux系統下檔案路徑使用'/'而不是'\'  

## 總結
1.可以把Google Colab看成是一台有GPU或TPU的Ubuntu虛擬機，只不過我們只能用命令列的方式操作它。你可以選擇執行系統指令，也可以直接寫執行python程式碼。  
2. 掛載完Google Drive，會在虛擬機器裡產生一個drive資料夾，直接將Google Drive當成是一塊硬碟即可。存取drive資料夾裡的文件，就是在存取你的Google Drive裡的文件。  
3. Colab最多連續使用12小時，超過時間系統會強制掐斷正在運作的程式並收回佔用的虛擬機器。 （好像再次連接到虛擬機器後，虛擬機器是被清空的狀態，需要重新配置和安裝庫等等）





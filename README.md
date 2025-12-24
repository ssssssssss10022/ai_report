# Colab訓練YOLO v5實現口罩偵測

本文介紹在Googlecolab上訓練yolov5進行目標偵測的基本流程。 yolo系列模型是目前最先進的目標偵測模型之一。 YOLO V5效能與YOLO V4不相伯仲，但其個頭比V4小得多，模型訓練速度也要快上不少。

本文前置條件：為了能夠存取Colab，需要電腦能夠科學上網。

Colab是Google提供的線上jupyter筆記本，其為勞苦大眾提供了6個小時連續白嫖Tesla GPU的機會（一次使用不超過6個小時，到點兒了會自動斷開連接）。另外Colab提供了多種深度學習框架支援（TensorFlow，PyTorch等），這對於學習者來講是非常不錯的運算資源。

Colab網址：(https://colab.research.google.com/notebooks/welcome.ipynb)  

## 1.設定計算環境

進入Colab後第一步是新建一個筆記本，如下圖所示。

![image](1.png)

選擇程式碼執行程序→ 更改運行時類型

![image](2.png)

在開啟的對話方塊中選擇硬體加速器為GPU

![image](3.png)

這樣就可以使用Google提供的GPU了。 

## 2.連接谷歌硬碟

Colab不會保存數據，這時候最好連接自己的Google硬碟。

在筆記本中輸入下面的程式碼並運行。

![image](4.png)

選擇要登入帳戶

![image](5.png)

允許Google Drive for desktop存取個人資訊，點選繼續

![image](6.png)

選取要讓Google Drive for desktop存取的範圍，點選全選後再點選繼續

![image](7.png)

谷歌硬碟連線成功後如下圖所示。

![image](8.png)

## 3.下載yolov5 

資料集可以自己製作，也可以使用別人製作的。自己製作資料集的話可以使用labelimg，注意選擇輸出為yolo格式。這裡簡單起見使用網路上公開的資料集。網站（https://public.roboflow.com/）提供了許多用於目標檢測的公開資料集，例如常見的微軟COCO資料集，牛津Pets資料集等。這裡找個小型的口罩資料集，這個資料集規模很小，只有149張照片。 （呃，相對於COCO十幾萬張照片來說真的可以忽略不計了）

![image](9.png)

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





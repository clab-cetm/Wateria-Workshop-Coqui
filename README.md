# 《WATERIA自助飲水站》Coqui 工作坊

---

![](images/coqui-01.jpg)

[Coqui](https://publiclab.org/notes/warren/03-01-2019/build-a-sound-generating-coqui-conductivity-sensor) 由 Publiclab community 發想製作，是一個量測液體導電性的微型裝置。這個工作坊來自於「[Lab Kill Lab](https://lkl.clab.org.tw/concept)」計畫中的「[WATERIA自助飲水站](https://lkl.clab.org.tw/workstations)」。關於本計畫的構思與策畫請參考 Lab Kill Lab 官網: [https://lkl.clab.org.tw](https://lkl.clab.org.tw)


## 關於這份文件

這份文件是配合 2020/12/14 在 C-LAB 所舉辦的《WATERIA自助飲水站 -- Coqui 工作坊》所製作的文件。在這份文件將會簡單介紹 Coqui，以及介紹如何製作出本次工作坊版本的 Coqui。在文件的後半段也將會介紹一些改裝的點子。


## Coqui 是什麼?

Coqui 是由 Publiclab community 所設計的 "液體導電性感測器" (Conductivity Sensor)。相較於一般的環境感測器裝置，Coqui 並不會顯示任何環境感測數據，而是以產生聲音的高低來傳達水質導電性的程度。水體中的電導率可以反映出水污染的程度。

另外，Coqui 所輸出的聲音是可以被錄製、分析、儲存，並可用於樂器演奏的。在這個工作坊中將示範如何製作一個 Coqui 導電性感測器。

[Coquí](https://en.wikipedia.org/wiki/Coqu%C3%AD) 的命名來自多明尼加樹蛙 (Eleutherodactylus Coqui)。是原產於波多黎各的一種相當小的樹蛙。多明尼加樹蛙求偶的叫聲就像牠的學名 “Coquí” 一樣，有二個明顯的高音 “co-kee”，在 0.5 公尺的範圍內可達將近 100 分貝。


## 開始製作 Coqui


### 準備材料

#### 基本材料

* 555 計時器 IC (Timer IC) x1
* 20KΩ 1/4W ±5% 碳膜電阻 (Carbon Film Resistor) x1
* 0.1uF 陶瓷電容 (Capacitors) x1
* 壓電式蜂鳴器 (工作電壓 1~30V) x1
* 9V 碳鋅電池 x1
* 9V 電池盒 (或電池扣) 含導線 x1
* 170 孔迷你麵包板 x1
* 10cm 公對公杜邦線 x4
* 20cm 公對公杜邦線 x2


#### 改裝用材料 (有需要才增加)

* 光敏電阻 x1
* 10~100K 以內的可變電阻 x1
* 撥動開關 x2
* 塑膠外殼
* 3.5mm 音源輸入孔焊接插座 x1
* 10cm 公對公杜邦線 x3


ps: 在實體工作坊中會帶大家以 "基本材料" 製作出最基本的 Coqui。關於進階的改裝步驟會記錄在這份線上文件的後半段，可根據上述的 "改裝用材料" 列表採買所需零組件。

![](images/coqui-02.jpg)


### 動手做


**Step1: 安裝 555 Timer IC 在麵包板上**

Coqui 透過 555 IC 發出震盪頻率，驅使蜂鳴器發出不同的音頻。安裝 555 的時候唯一要注意的就是 "安裝的方向"。在 555 的示意圖中有標示一個半圓形的缺口，並且有一個用來標記 "一號腳位" 的定位圓點。以下圖為例，原點所在的腳位是編號一號的 GND (接地)。IC 的規則大多是從一號開始逆時鐘依序編號。你可以注意到 1~8 的順序是從圓形點標示的一號開始逆時鐘依序編號的。

![](images/ne555.jpg)

真實的 IC 圖片如下。為了以下示範方便，請統一將 IC 半圓缺口處(圓點處)朝向左邊，然後找一個麵包板大約中間的位置安置它。

![](images/coqui-03.jpg)

步驟一完成之後應該會像這樣。

![](images/coqui-04.jpg)


**Step2: 連接 555 IC 的 pin4 和 pin8**

請使用手邊的杜邦線，將 555 IC 的第 4 腳位 (下圖 IC 下排最右)，連接到 555 IC 的第 8 腳位 (下圖 IC 上排最左)。

![](images/coqui-05.jpg)


**Step3: 連接 555 IC 的 pin2 和 pin6**

使用手邊的杜邦線，將 555 IC 的第 2 腳位 (下圖 IC 下排左二)，連接到 555 IC 的第 6 腳位 (下圖 IC 上排右二)。

![](images/coqui-06.jpg)


**Step4: 放置 0.1uF 陶瓷電容**

陶瓷電容的兩根腳沒有正負之分（無極性），安裝時正反兩面都可以使用。

安裝時如下圖，將其中一根腳，安置於 555 IC 的編號第 1 腳位下 (下圖 IC 下排最左) 的直排任一孔。另一根腳只要不在 555 IC 腳位的直排範圍內即可，例如下圖選擇往左間隔一個直排後安置。

![](images/coqui-07.jpg)


**Step5: 連接電容和 555 IC pin2**

如下圖，使用一條杜邦線將剛才安置電容的另一隻腳連接回 555 IC 編號第 2 腳位下 (下圖 IC 下排左二) 的直排任一孔。

![](images/coqui-08.jpg)


**Step6: 安裝 20KΩ 電阻**

20KΩ 電阻的色碼是 "紅、黑、橘"，你應該可以在 20KΩ 電阻上看到這三個顏色的色環。電阻也是沒有極性分別的，所以安裝的方向不拘。

安裝時請將電阻依照下圖的方式跨接麵包板的上半部和下半部。如果你希望讓電阻更平貼麵包板，可以將針腳剪短。

![](images/coqui-09.jpg)


**Step7: 連接電阻到 555 IC pin3**

使用手邊的杜邦線，20KΩ 電阻的一端連接到 555 IC 的第 3 腳位 (下圖 IC 下排左三)。

![](images/coqui-10.jpg)


**Step8: 接上蜂鳴器**

請注意，蜂鳴器有正負之分，黑色的線是負，接地 (GND)，紅色的必須供正電。

安裝時將蜂鳴器黑色的線接在 555 IC 的第 1 腳位下 (下圖 IC 下排最左) 的直排任一孔。蜂鳴器紅色的線則接在 555 IC 的第 3 腳位下 (下圖 IC 下排最左三) 的直排任一孔。　

![](images/coqui-11.jpg)


**Step9: 接上電池**

將 9V 電池扣上帶有導線的電池扣（或是使用帶有導線的 9V 電池盒）。電池也有極性，黑色是負極，紅色是正極。

將 9V 電池的黑色線接在 555 IC 的第 1 腳位下 (下圖 IC 下排最左) 的直排任一孔。9V 電池的紅色線則接在 555 IC 的第 4 腳位下 (下圖 IC 下排最右) 的直排任一孔。

![](images/coqui-12.jpg)


**Step10: 接上探測棒**

我們使用杜邦線當作水質導電性探測棒，請使用材料包中兩條較長的杜邦線。

如下圖，一條接在 20KΩ 電阻的一端同一直排孔。另一條接在 0.1uF 陶瓷電容的一端同一直排孔。


![](images/coqui-13.jpg)


完成！現在你可以開始測試 Coqui 囉~


## 使用 Coqui

在你把 Coqui 的探測棒放入液體之前，你可以試著將兩條探測導線末端的金屬接頭觸碰在一起。你應該會聽到 Coqui 從蜂鳴器發出了高頻聲音，這個音頻將會是這個 Coqui 電路能發出的最高頻聲音。在後續的段落中，我們會介紹如何調整它。 

你應該會發現當你把探測棒丟入液體的時候，探棒之間的距離甚至是深度都可能會影響音頻。因此假如你想比較不同液體的導電度，比較好的方式就是想辦法固定這些參數。

例如找一個泡綿將探棒插入：

![](images/coqui-14.jpg)

你也可以參考 Public Lab 公布在網站上的做法，裁切寶特瓶的上半部來製作承水器具。

![](https://img.youtube.com/vi/eFiavvMAseQ/maxresdefault.jpg)

來源參考：[Build a Coquí: A Simple Water Conductivity Sensor (version 1), publiclab.org](https://publiclab.org/notes/ashkaya/09-17-2016/build-a-coqui-a-simple-water-conductivity-sensor#Step+by+Step+Instructions+for+Making+the+Coqui)


## Coqui 改裝

以下是 C-LAB 示範的改裝步驟，你可以針對有興趣的部分單獨做改裝。


### 變身照度感測器

事實上 Coqui 的電路設計不只能用在量測水質的導電性，還可以應用於「任何能改變電阻值」的感測行為。

例如，只要將探測液體的探棒導線，替換成光敏電阻，就可以將 Coqui 變身為照度感測器。

![](images/coqui-20.jpg)

光敏電阻也沒有極性之分，所以連接的方向不拘。如下圖，移除用來探測液體的杜邦線。將材料包中的光敏電阻安裝於麵包板上。

將光敏電阻的一端接在 20KΩ 電阻的一端同一直排孔。另一端則接在 0.1uF 陶瓷電容的一端同一直排孔。

![](images/coqui-21.jpg)

現在，用手遮住光敏電阻，或是用手機的閃燈照射它，看看 Coqui 會發出什麼聲音吧~


### 加入電源開關 (適用於使用電池扣的狀況)

有時候為了減少裝置的體積，你可能會使用電池扣，而不是使用電池座。如果你的電池是透過電池扣供電給 Coqui 的。你可能會想要加入一個開關來控制是否要將電力輸出給 Coqui。

只需要使用像下圖這樣的 3pins 撥動開關就可以簡單做到。

![](images/coqui-15.jpg)

首先，移除電池的正極線（紅色）

![](images/coqui-16.jpg)

撥動開關有三根腳，將最左邊的腳接在 555 IC 的第 4 腳位下（下圖 IC 下排最右）的直排任一孔。

![](images/coqui-17.jpg)

接完之後，從上面俯瞰的樣子應該會像這樣。

![](images/coqui-18.jpg)

最後，再把剛剛移除的 9V 電池扣紅線接到撥動開關的 "中間那隻腳位" 的直排任一孔上。最後的樣子會像這樣：

![](images/coqui-19.jpg)

然後，試著切換撥動開關的位置，看看是否可以控制電池的供電與斷電。


### 替 Coqui 找個窩

你可以尋找適合的塑膠盒，讓你的 Coqui 有個窩。記得開孔讓 Coqui 的聲音可以傳出來。

![](images/coqui-22.jpg)

以及提供探測導線引出的孔。

![](images/coqui-23.jpg)


### 提供音源輸出孔

如果你想將 Coqui 的聲音錄製下來，或是將聲音輸出到桌上型喇叭，你可能會需要一個音源輸出介面。你需要購買一個「3.5mm 音源輸入孔焊接插座」，並且將導線的 Left/GND 接出。

下圖的白線是 Left，黑線是 GND。

![](images/coqui-24.jpg)

你可以在外殼上鑽個洞，安置音源輸出孔。

![](images/coqui-25.jpg)

接線的方式很簡單。記得剛剛的蜂鳴器有正負兩條紅黑線嗎？把蜂鳴器接線的位置用音源輸入插座的兩條導線替換即可。

音源插座黑色的線接在 555 IC 的第 1 腳位下 (下圖 IC 下排最左) 的直排任一孔。音源插座白色的線則接在 555 IC 的第 3 腳位下 (下圖 IC 下排最左三) 的直排任一孔。

![](images/coqui-26.jpg)

如果你想要同時讓蜂鳴器和音源輸出孔共存，你可能會想要多個撥動開關來切換 Coqui 的聲音由蜂鳴器輸出，還是由音源孔輸出？接線的方式如下圖：

![](images/coqui-27.jpg)

完成了！現在你可以使用音源線連接到電腦，配合軟體錄製 Coqui 的聲音，或是直接輸出到其他裝置。

![](images/coqui-28.jpg)


### 調整最高音頻

在 Coqui 的電路中，能決定音頻的是安置於電路上的電阻和電容。目前我們所使用的是一個 20KΩ 的碳膜電阻，以及一個 0.1uF 的陶瓷電容。

在電子材料行可以方便地買到可變電阻，所以透過改變電阻值來改變音頻是個比較簡單的方式。

![](images/coqui-29.jpg)

如下圖，先將原本固定電阻值的碳膜電阻移除。然後將可變電阻安置於麵包板上。

可變電阻通常會有三根腳，接線的時候只需要選兩根腳接線即可，但一定要有中間那根腳。所以左、中、右三根，你可以選 "左/中"，或是 "右/中"。

下面的示範中，我選的是 "左/中"。

![](images/coqui-30.jpg)

你唯一需要更改的，是將原本至於 20KΩ 電阻端的探測導線（下圖左黃線），改成連接到可變電阻的中間腳位同一直排孔。

然後你可以試著將探棒放入液體中或是直接互相接觸測試，同時以小螺絲起子調整可變電阻上的電阻值。你應該可以聽到隨著電阻值改變時，音頻也會跟著改變。

![](images/coqui-31.jpg)

Coqui Rock!

![](images/coqui-32.jpg)


## 應用 Coqui 的其它發想

Coqui 將水質的導電度（汙染狀況）轉化為音頻聲響。是否還能有其他轉換呢？

在 Public Lab 的官網中有人提出了這樣的點子 -- 使用開源的音訊編輯軟體 [Audacity](https://zh.wikipedia.org/zh-tw/Audacity) 輸出頻圖做分析。

![](https://publiclab.org/system/images/photos/000/025/196/original/low.png)

圖片來源參考：[Analizing the signal of the Coqui using Audacity, publiclab.org](https://publiclab.org/notes/imvec/06-11-2018/analizing-the-signal-of-the-coqui-using-audacity)

是否可以為買一種水質狀況產生一個專屬的圖騰或是樣板？交給各位去延伸發想了。


## 技術補充

### 電池與音量的考量

事實上 Coqui 可以使用 3V 的電池運作。可以使用兩個 AA 1.5V 的電池，讓 Coqui 發出聲音。但聲音會比 9V 的還小聲。

並且如果你有將聲音輸出到喇叭或其他裝置的需求，3V 電源的功率可能不足以推動喇叭。


### Coqui 是如何發出聲音的

首先，你必須了解日常中所謂的 Do Re Mi 音階，事實上代表著不同的「振動頻率」。例如以中央 C 之上的 A 作為 440Hz 時，中央 C 的頻率約 261.6Hz（C4）。

然後，你需要知道我們所使用的蜂鳴器，是一種稱為「無源壓電式」的蜂鳴器，要讓這種蜂鳴器發出聲音，必須持續地對蜂鳴器輸入高電壓和低電壓的切換（pulse），而根據電壓正負切換的頻率就會讓壓電片產生不同頻率的震動，進而發出對應的音階。


### 如何簡單決定最高音頻

這邊所指的高音頻是指當兩根探棒短路接觸碰在一起時所發出的聲音。理論上那就是當前 Coqui 電路配置下的最高音頻。

在 Coqui 改裝的段落中，我們提到了可以透過調整可變電阻來決定最高音頻。但要怎麼做到盡可能地精確呢？如果我想要發出較準確的 Do Re Mi 的音階，我該怎麼做呢？

事實上 555 Timer IC 的規格書都會附上不同的接法以及該電路產生頻率的計算公式。但其實最簡單的方式就是直接量測訊號。這裡使用一台手持示波器，量測 Coqui 電路上蜂鳴器所連接的正負位置（紅黑線），你可以看到我們的基本配置版本將會輸出 880Hz 的音頻，大約是 A5 的音符。

![](images/coqui-33.jpg)

所以只需要使用合適的可變電阻，配合示波器的協助，就能夠以較方便的方式設定最高音頻。

![](images/coqui-34.jpg)


~ END ~　呱！呱！
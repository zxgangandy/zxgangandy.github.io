---
title: 我們與 OSCP 的距離
author: crystal
date: 2021-09-02
tags: [Security]
layout: zh-cn/layouts/post.njk
image: /img/posts/crystal/oscp/cover.jpg
---
<!-- summary --> 
<!-- 八月的某一個凌晨，終於完成報告然後跟考官道別結束考試，半年的奮戰也告一段落。期待已久的 OSCP 到手啦！半年前 OSCP 對我而言也是 castle in the cloud，今天來分享這張證照是什麼，以及我自己的準備過程與心得。 -->
<!-- summary -->
資安領域中，多數人都聽過一張標榜最有公信力的證照，就是不少公司跟求職者趨之若鶩的 OSCP。
常聽很多人說，OSCP 證照是『小魔王』，考前像在地獄爬一圈，考完前途一片光明，多少人考了四五次都沒過，簡直不要太殘忍。這張證照到底是何方神聖能被形容成這樣呢？

## 關於 OSCP

OSCP （Offensive Security Certified Professional）是 Offensive Security 這家公司發行的一系列證照之一，也是他的入門款第一張（對你沒聽錯，這個大魔王其實是難度比較低的基礎款喔）。Offensive Security 每隔一陣子就會更新課程內容跟證照類型，所以有一些證照現在已經不能考或是改名了，現階段發行的證照可以去官網查詢：
#[OSCP 證照們](/img/posts/crystal/oscp/oscp-certs.png)

從下面這個編號命名規則跟學習流程圖也可以看出 OSCP 的編號 PEN-200 是最基礎也最 general 的。後續有更深入的 OSEP(PEN-300) 以及專精網頁攻擊的 OSWP(WEB-300) 跟專攻 exploit 開發的 OSED(EXP-301) OSEE(EXP-401) 等等。

#[PWK journey](/img/posts/crystal/oscp/certs-journey.png)

忘了之前是在哪個網站看到的，有一張截止今年二月各種資安證照的示意圖，感覺應該是依照難度跟領域劃分的，放這裡僅供想考證照的人參考。可以看到 OSCP 在最右邊中上的地方：

#[各種資安證照](/img/posts/crystal/oscp/certs-all.png)

回到 OSCP，這張證照的考試內容算是比較廣泛的，就是模擬你進到內網裡面有一堆機器，你要如何快速找出一些淺顯的弱點（例如版本過舊的軟體、看起來很可疑的網站、權限沒鎖好的服務等等）並收集資訊，然後利用這些弱點進到機器獲得低權限，再試圖提權拿到最高權限。

説 OSCP 是入門的原因也是因為，課程中大多數設計好的『漏洞』通常都是有公開 exploit （可能需要一點手動修改）或是一些需要手動執行但是概念簡單的問題（例如 SQL injection），但並不會需要你自己從頭挖掘或撰寫一份 exploit（當然你要把手動執行的部分自動化也是不錯的練習），簡言之，一切都是『已知的』，只是你有沒有觀察到而已。我的感想是，這個考試只是過濾掉一些 script kiddie 並訓練你基本技巧的熟練度跟分辨 rabbit hole，不會讓你變成漏洞挖掘大師 XDD

### 考試方式

OSCP 不是一般筆試，而是給你 24 小時打下 5 台機器的上機考，然後還會有 24 小時可以寫一份完整的滲透測試報告，所以總計是一個 24+24 小時的考試。因為現在是上機部分全程監考，所以你要在預定考試的前 15 分鐘先進去一個 portal 跟考官核對身份、確認環境（要拿起電腦讓他看到整個房間跟桌子下）、開螢幕分享跟攝影機，這時間如果因為設備或是其他問題 delay 就是吃到你自己的考試時間，所以建議考前自己測試一下。開始考試後考官全程會盯著你跟你的螢幕們看，要暫停或是中離都要跟他說一聲，回來也要。不用擔心，他們會輪班監考，不會陪你通宵。

考 24 小時聽起來很可怕，不過考試的設計也不是要你 24 小時都在電腦前面敲敲打打，他是有考慮到睡覺吃飯休息運動等日常生活的，之前在 reddit 上看到有人說，考試設計是你應該在 12 小時內就可以完成的，所以不用到廢寢忘食啦！（雖然會想考這張的應該打 CTF 也常常不小心玩到通霄 XDD）

如果你有到寫報告的階段，會再有 24 小時可以寫一份專業的滲透測試報告，寫完壓縮上傳到一個網站，送出就不能再修改，格式內容檔名都不行。這部分官方有提供一個模板，社群也有很多改良版本，讓你可以把考試機器的過程填格子填好，前後罐頭文字都不用動，就算是沒寫過報告的也可以滿簡單的完成。要別注意的是，前面上機考的時間一結束你就再也進不去了考試環境了，所以缺截圖少步驟也沒辦法補上，請培養隨時截圖並做筆記記錄步驟跟結果的習慣。我自己是一邊打一邊寫，打完一台就把整個過程完整寫進報告裡，所以上機考完差不多就可以交報告了。

每台機器都有配分，分別是 25 25 20 20 10，總共滿分 100 分，這個配分指的是你可以從這台機器拿到的最高分數，也就是說一台 25 分的機器你要拿到最高權限的 flag 並且報告都沒被扣分才能拿到 25 分，如果你只拿到低權限的 flag 或是報告沒寫好，就只有部分分數甚至沒分（報告是看得很重的）。最後必須至少 70 分才會通過考試，所以上機可以的話多拿一點分數比較保險，如果連 70 分都沒有也就可以不用寫報告了。另外，聽說 lab 跟課程的 exercise 如果有做完然後寫完整的 writeup 有機會加五分，不過我覺得 CP 值頗低所以沒做。

### 課程與設備

OSCP 的考試是跟課程綁在一起的，也就是你報名的是 PEN-200 這個課程然後會附帶考試機會一次，後續要是沒考過可以再買補考，不過第一次是不能只買考試的。（現在官網還有買 365 天加考試機會兩次的方案，真的會有人買嗎）

那課程內容有哪些呢？當你報名之後會收到教材包，裡面有壓縮後 4GB 的影片們與 851 頁的 PDF 講義，影片跟講義的章節跟內容都是對應的，可以想像成是動畫有聲書（？）然後還有登入 VPN 跟論壇的一組帳號密碼。

首先，開始前你需要準備幾樣東西。

第一是一台 kali，教材包裡面官方會寄給你一台舊一點的版本，不過我是用我自己的 kali，雖然有聽過別人討論不同版本有些工具會出問題（kali 是 rolling release 會一直更新），不過我自己是沒遇到什麼 google 無法解決的問題啦，考試也很順利。 

第二是做筆記的軟體。我用的是 kali 內建的 cherrytree，不過我覺得用自己熟悉的就行。讀講義跟練 lab 的時候，要有條理地整理自己嘗試的方法、步驟、指令、甚至截圖，不管是不是要寫 writeup，留個紀錄都好。說不定考試的時候剛好遇到一個似曾相識的狀況，這時候有筆記跟步驟就會讓你安心許多，而且平時就培養做好筆記的習慣，考試也不容易東漏西漏最後還要回去一直補洞。

考試的話，排好時辰之後你會收到一封信告訴你需要準備哪些東西跟一個 FAQ 網址。設備不外乎就是：
* 鏡頭：我用 mac 的內嵌鏡頭但也可以外接，畫質要讓考官可以清楚看見你的身份證明文件
* 還算通順的網路：官方給你的 VPN 包會附說明跟你說 ping time 多少比較好，我平常在家練 lab 大概是下載上傳 16Mbps/3Mbps，除了 RDP 跟 tunneling 之後有一點卡之外大致上都還行，不過考試的時候除了 VPN 還要分享鏡頭跟螢幕，全程視訊真的是會 lag，所以我是到學校用超高速網路 XDD 我覺得保守一點一般 100Mbps/60Mbps 應該就很順暢了。
* 身份證明文件：政府發行的證件，但必須是英文的，所以台灣人應該只能用護照了吧（？）注意這個要跟你註冊的名字一樣！！

### 課程內容

講義的部分內容依據章節順序大概是：

1. 介紹 PWK(PEN-200)：包含課程、環境、報告、考試規範等等
2. 基礎
    1. Kali 教學：怎麼安裝跟使用 kali linux，還有 command line 教學
    2. 工具介紹：netcat, powershell, wireshark 等等常用工具
    3. 寫簡單的 bash script
3. 資料收集：
    1. Passive recon: google hacking, email password dump...
    2. Active recon （各種服務的資訊收集）
        1. port scanning
        2. DNS, SMB, NFS, SMTP, SNMP 等等的枚舉技巧
    3. Vulnerability scanning
4. 網頁攻擊：
    1. 手動勘查、工具使用
    2. XSS, Directory traversal, File inclusion, SQL injection...
5. Buffer Overflow (Windows + Linux)：最簡單的那種，連 NX 都沒開，return address + shellcode 結束這一回合
6. Client-Side Attacks: HTA, Microsoft Word...（惡意軟體實作入門 XDD）
7. 尋找、修改、編譯、使用 public exploit
8. file transfer 的技巧
9. 避開防毒軟體
10. 提權（Privilege Escalation）
11. 爆密碼
12. port forwarding 跟 tunneling 的小技巧
13. Active Directory (AD)
14. Metasploit 跟 Powershell Empire 教學
15. 完整滲透測試的一次 walkthrough

基本上，如果不是完全沒有一點資訊背景，我覺得可以跳過第二段基礎的部分。然後如果是純粹為了短時間內通過考試，可以先跳過 passive recon、client-side attack、防毒、port forwarding、AD、Metasploit（禁用）這些章節，扣掉零零總總大概剩 3/5 的內容。雖然扣除的部分都還蠻有趣而且現實中也實用，不過因為考試中不會/不能出現，所以趕時間的朋友可以重點練下面幾個技巧：

* Active recon
* 網頁攻擊
* public exploit
* file transfer
* 提權（Privilege Escalation）

我自己因為在報名 OSCP 之前玩了好一陣子的 Hack The Box (HTB)，所以對課程主題都有一點熟悉度了，講義影片這邊只花了兩三天快速看過加補足一些沒看過的技巧。依據 reddit 上的討論，如果是完全沒接觸過的話，建議把講義從頭讀一遍（或是看完影片）並整理自己的筆記，exercise 也可以選著做一些；有點基礎的話，還是可以搭配講義跳著看來補充整理一下屬於自己的筆記，雖然內容可能很冗長，但是官方課程內容的優點就是真的講得很仔細，雖然不深但算是很全面的介紹，當作是複習一下也不錯，偶而還是會戳到一些沒那麼清楚或是不懂的點。講義的每個小章節都會有一些 exercise 讓你動手練習（lab 裡面會有你專屬的 client machine 可以用），這部分如果有全部做完然後寫 writeup 就可以額外加分，不過我也沒從頭讀完，所以就沒做這塊。

我自己覺得最重要最有幫助的其實是最後一章帶你做一次滲透測試的部分（在 lab 裡面也可以跟著做一次）。這段會給你一台入口機器，然後教你如何枚舉如何選擇 attack vector 層層推進，會深入好幾層內網最後拿下 AD，基本上講義內所有類型的技巧都會用到。

雖然個別的技巧都會用，但是我一直覺得自己缺少一個明確的方法論跟做滲透的 SOP 來最有效率的串出攻擊鍊，一看到機會就見獵心喜的衝進去，試了半天才發現死路一條。

> 我覺得這門課另一個很重要的目的是建立一套穩定的中心思想，讓你在真的滲透的時候能有計畫跟邏輯的進行攻擊，而不是亂槍打鳥。

附帶一提，lab 裡面有兩台機器有官方的 writeup，也是非常重要的資源，建議一定看過想過一遍，會省很多走歪路的時間。再提一點，既然這門課希望建立你的方法論，考試機器就勢必會開很多誘餌服務來誤導你，做好時間控管並且學會判斷哪些才是真的 meaty 很關鍵。

### Lab

Lab 環境就是模擬一整個企業的網路，大概長得像下面這張圖，外層是你用 VPN 連過去就可以直接 access 的 public network，還有必需透過 tunneling 才可以連到的內部網路 IT DEV ADMIN 部門。這個網路是跟其他學生共用的，所以每一台打之前建議先 reset ，不然有時候被別人弄壞了或是改了設定就會白費時間，或是偶爾解一解看到其他人留下來的痕跡然後被暴雷 XDD

下面的 private segment 是每個人會有三台專屬的機器，分別是一台 linux 一台 win10 跟一台 windows server，主要是在講義 exercise 的時候讓你實作練習用的。這三台機器要自己 reset 才會 spin 起來，並在 VPN 斷掉後也會關掉。我自己是只有用到 win10 來做 windows 的 BOF，因為考試的時候一定會有一題 25 分的 BOF，然後官方也會給你一台 debugging machine，所以還是考前練習一下怎麼用那個軟體比較保險 XDDD

#[Lab 環境](/img/posts/crystal/oscp/lab-env.png)

截至 2021/08/19 （我的最後一天）為止，不算講義中帶你做的模擬測試的話，總共有 70 台機器，據官方所說其中還有約 5~8 台前考試機。

你的 VPN 帳號密碼也會用來登入一個學生專用的論壇，裡面有分門別類的討論區，大致上劃分成機器區、教材區、其他問題區。你可以在裡面跟其他同學還有校友交流，不過如果對題目暴雷太多會被管理員刪除字句，所以很多提示都會講得很隱晦。除了考試機器，任何相關問題都能問，不管是技術相關或是關於考試需要的硬體設備等疑難雜症幾乎都會有人回應。

## 怎麼準備

大家最想知道的當然是：我到底該怎麼準備？先讓我講講自己的經驗再介紹一些資源給大家。

我決定要考 OSCP 的時候被各種評論嚇得不輕，所以規劃了半年來準備，整體來說從二月努力到八月底考試。二月開始，我大概每週花 16 小時練 Hack The Box (HTB) 上面的題目，然後因為想要做完 lab 直接考，所以我在六月底左右報名 60 天的 lab，最後八月底考完畢業。

### 2~6月 HTB

HTB 是一個很酷的練習平台，上面除了有非常大量的 machines 之外還有 CTF jeopardy style 的題目、專攻某些技術的 tracks、一系列 AD 機器的 fortress 等等，總之有非常多資源可以讓你打到爽。

#[Hack The Box](/img/posts/crystal/oscp/htb.png)

跟 OSCP 最像的 machine（或是 box）也有各種 OS 跟難易度（雖然時間越近的難易度已經大幅躍升了），免費用戶可以玩一小批會 rotate 的 box，付費的話就可以玩所有的 retired machine，總共好幾百台。每週都會推出新的 box 可以玩，而且都會有官方論壇可以交流討論給提示，是個很有幫助的社群 XDDD 

而且最重要的是，初學者可以用這些 box 搭配別人的 writeup 還有 walkthrough 學到很多技巧跟經驗，例如廣為推崇的 [ippsec 影片](https://www.youtube.com/channel/UCa6eh7gCkpPo5XXUDfygQQA) 還有我自己常看的 [0xdf hacks stuff](https://0xdf.gitlab.io)，因為他們不是只告訴你對的路在哪，而是會解釋自己是怎麼想的、走了哪些歪路、為什麼有些方法行不通等等，我覺得對建立自己的思路很有幫助。

對於該如何學習這件事，相信每個人都有自己適合的方法，我的話是盡量嘗試但沒想法了就去論壇找 hints 或是找 writeup，理由很簡單，雖然自己撞也許過一陣子撞得出解法，但對初學者來說這樣效率低而且思考沒有系統化。

> 這個方法並不是一卡住就找解答，這樣是不會成長的，而是把自己的招式跟能想到的方向都嘗試過後，就該是拜師求學的時候了，畢竟 you can't know what you don't know，人都是從模仿開始的。這時就可以參考我上面提過的網站，看看別人是怎麼想怎麼觀察的然後修正自己的方法，最後自己練習做一遍，把技巧變成自己的知識。

為了準備考試而練習 HTB 的話，建議買 VIP 會員，一個月才 10 英鎊而已可以打幾百台機器真的很划算，補考一次都要 $249 了。練習順序的話可以參考 [TJnull's list](https://docs.google.com/spreadsheets/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/edit#gid=1839402159)，裡面整理了跟 OSCP 比較像的 box，而且一直有在更新，可以幫你規劃練習。

#[TJnull's list](/img/posts/crystal/oscp/tjnull.png)

不過也許是因為 OSCP 的 box 比較不需要太多創意（？）所以在 HTB 上評分都不高，我自己是除了清單上的也把 easy 跟 medium 評價有 4 以上的都做了一遍，順序是由舊到新、由簡單到困難。

我在這個時期累積了很多技巧跟經驗，甚至有點過度轟炸的狀態，因為每個 box 用到的技巧都不同也不太會重複，所以就是不斷的『哇哇哇原來可以這樣啊』，比較少有『嗯嗯一看就是這樣啦』的感覺。後期慢慢就培養出自己的直覺了，可以比較快速地知道哪裡有問題以及該如何找到方法，做的筆記也在考試準備上很有幫助。

附帶一提，跟 HTB 相似的 Proving Grounds (PG) 聽說也不錯，雖然機器沒有 HTB 多但是因為後來被 Offensive Security 買下來了所以據說裡面的 box 是最接近 OSCP 考試的，上面的 TJnull's list 也有整理進去。

### 7~8月 OSCP Lab

差不多把 HTB 上的 easy + medium 的 linux + windows box 練了八成之後，就覺得好像有點基礎可以來試試 OSCP lab 了。

講義的部分沒有花太多時間，因為 HTB 教的技巧更多更深，不過漏網之魚還是花了一兩天補起來，方法論的部分也認真思考了一遍。 

剛開始練 lab 的時候有點迷惘，因為不管是 CTF 還是 HTB、PG 這種練習平台，都是一個 IP 一個 IP 各自獨立的所以標的很明確，但 lab 就是一整個大網路，裡面有一堆機器，你怎麼知道從哪邊開始好？有些機器還有相依性，不解完一台進不去另一台，又該如何判斷？

這時候就是用到 OSCP 方法論的時候了！

> 你必須透過大範圍的掃描跟 DNS 的資訊判別有哪些機器以及他們各自的特性，由粗而細檢視這個網路、挑選攻擊對象，最後逐一擊破。拿到最高權限還不夠，你必須好好搜刮裡面的資訊，才能更好的狙擊下一個目標。

雖然你也可以偷看繳交 flag 的頁面來知道有哪些 IP 然後照順序打完，但我相信除去了建立全局觀並規劃攻擊順序的練習，你的收穫一定會少得多。

這也是大家對於 OSCP lab 評價兩極的原因。課程中希望模擬真實世界的網路，大量用戶彼此間有互動跟資訊交流也有權限上的不同，有些機器戒備森嚴有些卻容易得莫名其妙，以『培養出有基礎能力的滲透測試人員』來說這點做得不錯。但是考試卻完全不同，是五台各自獨立的機器，目標是『在時間內打下這五個目標』。所以以學習的角度而言 OSCP lab 相當特別，但單純只是為了考到證照的話，其他的練習平台反而更符合需求。

這方面我自己的心得是，如果時間足夠不妨同時進行。

做 OSCP lab 做多了會陷入一個僵化的思維，就是掃服務，每個戳戳看，找到 exploit 或入口，打，跑提權的腳本，打，結束。exploit 的方式跟地方還有提權的技巧不外乎就那幾個。雖然 HTB 流程上也是差不多，但是每個階段都需要仔細觀察，變化跟技巧豐富度差很多，有可能你會找到某個權限或是位置稍微不同的執行檔，decompile 後會找到某個可以蓋過去的函式庫；有可能你要多開幾個連線，重複登入看看背後執行的程式有什麼不同。總之不會是找 exploit，打，拿 shell 這麼固定的方式。

> 我覺得不管是我的經歷（先從 HTB 大量快速累積技巧，再用 OSCP 鞏固做滲透的方法論），或是先用 OSCP 建立基礎再用 HTB 訓練 thinking outside the box 並充實自己的工具箱，都是不錯的方式。

### 8月底 OSCP Pre-exam

讀書的時候，都有考過模擬考吧？考 OSCP 前，訓練時間管理跟壓力控管的一個方式，就是給自己一次完整的模擬考！

在考前一兩週可以安排一次 24 小時的考試，模擬實際考試的環境跟時間，要求自己做完五台機器。我自己用的是 [John J Hacking - The OSCP Preparation Guide 2020](https://johnjhacking.com/blog/the-oscp-preperation-guide-2020/) 裡面建議的：

* Buffer Overflow Machine: VulnHub Brainpan (25 Points)
* Jeeves (25 Points)
* Chatterbox (20 Points)
* Cronos (20 Points)
* Sense (10 Points)

另外 TJnull 也有推薦在 VulnHub 上的另一組機器：

#[Dry run](/img/posts/crystal/oscp/dry-run.png)

請完全模擬考試，做完整的筆記跟截圖紀錄，不要使用手機也絕對不能去找提示，可以的話連報告也寫一份。

> 就算沒有 70 分也沒關係，模擬考的目的是讓你知道自己準備的程度跟缺少的練習，順利完成是增進考試信心，沒完成也只是教會你更多考試能用的武器。

### 資源

這裡整理一些我覺得有幫助的資源、部落格、或是文章：

Boxes:
* [Hack The Box](https://www.hackthebox.eu/)
* [Proving Grounds](https://www.offensive-security.com/labs/)
* [VulnHub](https://www.vulnhub.com/)
* [TJnull's list](https://docs.google.com/spreadsheets/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/edit#gid=1839402159)
* [ippsec 影片](https://www.youtube.com/channel/UCa6eh7gCkpPo5XXUDfygQQA)
* [0xdf hacks stuff](https://0xdf.gitlab.io)

更多 OSCP Prep：
* [John J Hacking - The OSCP Preparation Guide 2020](https://johnjhacking.com/blog/the-oscp-preperation-guide-2020/)
* [Rana Khalil](https://rana-khalil.gitbook.io/hack-the-box-oscp-preparation/)

好用的：
* [HackTricks](https://book.hacktricks.xyz/)
* [Payloads All the Things](https://github.com/swisskyrepo/PayloadsAllTheThings)
* [Sushant747 Total OSCP Guide](https://sushant747.gitbooks.io/total-oscp-guide/content/)
* [revshells](https://www.revshells.com/)
* [GTFOBins](https://gtfobins.github.io/)

### 其他建議

* 提前一個月預約考試。剩兩三週的時候比較好的時間大概都沒了，如果你不想要晚上八點到早上六點之間開始的話要早點預約，反正時間可以改三次而且早點約比較有死線的感覺（？）
* 睡好，吃飽，常常起來走動休息。真的，你需要新鮮的腦袋來釐清思路，答案就在那裡，只是頂著一個又累又緊繃的漿糊腦是看不出來的。你不需要 24 小時，你只需要思緒清楚的 12 小時。附上一句別人心得裡面我很喜歡的一句話：

> You'll run out of ideas before you run out of time 

* 考試只能用到一次 Metasploit，所以請留到非不得已，你能在 Metasploit 找到的 exploit 也一定可以在其他地方找到公開 exploit。平常練習 lab 也請不要依賴 Metasploit。
* OffSec 標榜 Try Harder，我個人的詮釋是再多研究多嘗試一些，想想還有什麼事能做但還沒做，或是有什麼遺漏的地方，把你會的都發揮出來。但當你撞到一面牆，重複 google 同一個關鍵字、跑同一個 exploit 20 次是沒用的，適時的求救能幫你用更短的時間學到一樣的東西。
* OffSec 有下面這張 Pass rate vs machines compromised 的統計圖，不過除了很直觀的『打越多越安心』之外根本沒什麼資訊。我想說的是，打機器只是訓練你的熟練度跟方法論的完善程度，如果你完全不用依靠論壇就可以順順一天打好幾台，就算你最後只完成了 20 台也一樣可以考過。不用太拘泥這個數字。

#[Pass rate vs machines compromised](/img/posts/crystal/oscp/pass-rate.png)

### 心得

剛決定考 OSCP 時其實覺得有些慌張，畢竟什麼都不會要怎麼考？但隨著解開的 box 越來越多，累積的筆記跟技巧越來越豐富，心裡的踏實感也會逐漸累積，大概就是學習曲線上從『我知道我不知道』走向『我知道我知道』的成就感。

技術上，OSCP 難度的確不高，考驗的是觀察力跟串連資訊找到漏洞的能力，只要發現對的破口幾乎就一擊斃命。考試剛開始時緊張到手抖，根本不能好好思考，後面出去散個步回來放鬆一點後雜亂的資訊就都自己連線歸位了。快要考試的人們，你們是一定可以做到的，要相信自己累積的實力早就超過考試所需了，只是壓力讓你眼睛業障重，過了 15 個小時只有 25 分也無所謂，剩下的時間絕對夠你把其他機器都打完，別慌。

給想要嘗試 OSCP 的人們，不論你是什麼背景與經驗，都可以去玩玩看 HTB 之類的平台來感受一下。一開始會卡住或是茫然是完全正常的，我的前幾個 box 也是在『我該幹嘛？』『然後呢？？』中度過的。這是你學習的第一步，多堅持一下你會比想像中進步更快！

這半年內，我在 HTB 訓練的各種技巧跟 OSCP 的滲透思維都給了我很多成長跟養分，推薦給想學習更多的 hacker wannabes！我也要繼續朝下一張前進了！

有問題可以在下面留言，我會在不違規的情況下盡量回答 XDDD

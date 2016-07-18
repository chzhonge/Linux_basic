# 第一章、Linux是什麼

# Linux之前，Unix的歷史
1969年以前 MIT -> Multics（讀卡機時代）</br>
> 相容分時系統(Compatible Time-Sharing System, CTSS)』， 它可以讓大型主機透過提供數個終端機(terminal)以連線進入主機，來利用主機的資源進行運算工作。 僅提供輸入輸出。


1969年 Ken Thompson (貝爾試驗室一員) ->Unics </br>
+ 覺得Multics沒搞頭，將其簡化。
+ 為了移植「太空旅遊」。
+ **所有的程式或系統裝置都是檔案。**
+ **不管建構編輯器還是附屬檔案，所寫的程式只有一個目的，且要有效的完成目標。**

1973年 Thompson與Ritchie (貝爾試驗室) ->Unix
+ 覺得Unics好用，但是機器不同需重新編譯組合語言，<br>改用高階語言來改善這種狀況，使用**B語言**（效能不好），Ritchie 將B語言改寫成為**C語言**，Unix誕生。

1977年 Bill Joy（柏克萊大學 ）-> Berkeley Software Distribution (BSD)
+ Sun(昇陽)創辦者。
+ FreeBSD即是BSD改版而來。

1979年 AT&T -> 收回Unix版權

1984年之一 Andrew Tanenbaum（譚寧邦）教授 ->Minix
+ 為了學生Unix核心課程自己開發。
+ 教育用途，無維護時間。


1984年之二 Richard Mathew Stallman(史托曼) -> GNU計畫與FSF基金會的成立
+ 認為「分享」是產生更優秀的程式碼的最佳方式！
+ 專利軟體為封閉環境無法共享，轉移至較開放的Unix</br>
，也將自己轉換完成的程式碼公開出來。
+ GNU計畫， 這個計畫的目的是：建立一個自由、開放的Unix作業系統(Free Unix)。
+ 程式編輯器:Emacs，並公布原始碼。
+ 撰寫C語言的編譯器：**GNU C Compiler(gcc)**。
+ 販售 Emacs 募資 成功召募工程師與志工撰寫軟體。</br>並建立自由軟體基金會(FSF, Free Software Foundation)。
+ 完成**(GNU C library)** 以及**BASH shell**。

1988年 MIT與其他協力廠商 -> 圖形介面XFree86計畫  
+ 成立了非營利性質的XFree86組織。

1991年 Linus Torvalds -> Linux base Kernel
+ 芬蘭大學生Linus Torvalds的一則簡訊
+ Linux 即將出現。
+ 將Linux修改符合軟體運作規範以支援各項軟體。
>POSIX是可攜式作業系統介面(Portable Operating System Interface)的縮寫，重點在規範核心與應用程式之間的介面， 這是由美國電器與電子工程師學會(IEEE)所發佈的一項標準喔！
+ 先求有且能跑， 再求進一步改良。
+ Linux便逐漸發展成具有模組的功能架構。

Linux的核心版本
> 3.10.0-123.el7.x86_64</br>
主版本.次版本.釋出版本-修改版本
+ **失效**
+ 主、次版本為**奇數**：發展中版本(development)</br>
> 2.5.xx，這種核心版本主要用在測試與發展新功能，所以通常這種版本僅有核心開發工程師會使用。 如果有新增的核心程式碼，會加到這種版本當中，等到眾多工程師測試沒問題後，才加入下一版的穩定核心中；
+ 主、次版本為**奇數**：發展中版本(development)
> 如2.6.xx，等到核心功能發展成熟後會加到這類的版本中，主要用在一般家用電腦以及企業版本中。 重點在於提供使用者一個相對穩定的Linux作業環境平台。

主線版本、長期維護版本(longterm version)
+ 看[這](https://www.kernel.org/releases.html)
+ **指令 查詢 Kernel 版本 ：uname -r**

Linux distributions
+ 『Kernel + Softwares + Tools + 可完整安裝程序』，稱為Linux distribution， 一般中文翻譯成可完整安裝套件，或者Linux發佈商套件等。
+ 需依據Linux Standard Base (LSB)和目錄架構的File system Hierarchy Standard (FHS)等......規範來開發。
# 關於GNU計畫、自由軟體與開放原始碼
GNU計畫與FSF基金會創辦人Stallman先生
+ 發展的良好的軟體讓大家來使用。
+ 改良程式碼回傳分享，自己也進步。

自由(Free)的真諦：
+ 取得軟體與原始碼：你可以根據自己的需求來執行這個自由軟體；
+ 複製：你可以自由的複製該軟體；
修改：你可以將取得的原始碼進行程式修改工作，使之適合你的工作；
+ 再發行：你可以將你修改過的程式，再度的自由發行，而不會與原先的撰寫者衝突；
+ 回饋：你應該將你修改過的程式碼回饋於社群！
+ 修改授權：你不能將一個GPL授權的自由軟體，在你修改後而將他取消GPL授權～
+ 單純販賣：你不能單純的販賣自由軟體。

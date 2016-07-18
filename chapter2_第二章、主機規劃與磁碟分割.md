# 第二章、主機規劃與磁碟分割

# 各硬體裝置在Linux中的檔名
|裝置|裝置在Linux內的檔名|
|---|---|
|SCSI/SATA/USB硬碟機|/dev/sd[a-p]|
|USB快閃碟|/dev/sd[a-p] (與SATA相同)|
|VirtI/O界面|**/dev/vd[a-p] (用於虛擬機器內)**|
|軟碟機|/dev/fd[0-7]|
|印表機|/dev/lp[0-2] (25針印表機)</br>/dev/usb/lp[0-15] (USB 介面)|
|滑鼠|/dev/input/mouse[0-15] (通用)</br>/dev/psaux (PS/2界面)</br>/dev/mouse (當前滑鼠)</br>|
|CDROM/DVDROM|/dev/scd[0-1] (通用)</br>/dev/sr[0-1] (通用，CentOS 較常見)</br>/dev/cdrom (當前 CDROM)</br>|
|磁帶機|/dev/ht0 (IDE 界面)</br>/dev/st0 (SATA/SCSI界面)</br>/dev/tape (當前磁帶)|
|IDE硬碟機|/dev/hd[a-d] (舊式系統才有)|
> 如果你的機器使用的是跟網際網路供應商 (ISP) 申請使用的雲端機器，這時可能會得到的是虛擬機器。

# 磁碟分割
+ MSDOS(MBR)
 + 主要開機記錄區(Master Boot Record, MBR)：</br>安裝開機管理程式的地方，有446 bytes。
 + 分割表(partition table)：</br>記錄整顆硬碟分割的狀態，有64 bytes。
 + 主要和延伸分割合計最多為**四塊**
 > 3P+1E E可在分割為多個邏輯分割
 </br>邏輯分割一定是從5開始，因為前4包留給主要和額外。
 +  2.2TB 限制。



+ GPT 磁碟分割表(partition table)
 + LBA(預設為 512bytes)
 + 使用前34個 LBA 紀錄分割資訊，將最後 33 個 LBA 作為備份區。
 + LBA 0 儲存了第一階段的開機管理程式。
 + LBA 1 (GPT 表頭紀錄)
   + 儲存分割表本身位置與大小。
   + 備份的LBA後33區塊位置，提供磁區修復。
   + 分割表的檢驗機制碼 (CRC32)，來檢查標頭有無錯誤。
  + LBA2-33 (實際紀錄分割資訊處)
  + GPT 在每筆紀錄中分別提供了 64bits 來記載開始/結束的磁區號碼。
  + GPT 分割表對於單一分割槽來說<GPT 分割表對於單一分割槽來說他的最大容量限制就會在『 2<sup>64</sup> x 512bytes = 2<sup>63</sup> x 1Kbytes = 2<sup>33</sup>xTB = 8 ZB 』，要注意 1ZB = 2<sup>30</sup>TB

# BIOS 搭配 MBR/GPT 的開機流程
1. BIOS：開機主動執行的韌體，會認識第一個可開機的裝置；
2. MBR：第一個可開機裝置的第一個磁區內的主要開機記錄區塊，內含開機管理程式；
3. 開機管理程式(boot loader)：一支可讀取核心檔案來執行的軟體；
  1. 安裝在MBR
  2. 安裝在每個分割槽的開機磁區(boot sector)
4. 核心檔案：開始作業系統的功能...
> 根據BIOS所支援的開機程式，檢視可開機的裝置。

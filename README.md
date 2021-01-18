# Aria2 一鍵安裝管理指令碼 增強版

[![LICENSE](https://img.shields.io/github/license/P3TERX/aria2.sh?style=flat-square)](https://github.com/P3TERX/aria2.sh/blob/master/LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/P3TERX/aria2.sh.svg?style=flat-square&label=Stars&logo=github)](https://github.com/P3TERX/aria2.sh/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/P3TERX/aria2.sh.svg?style=flat-square&label=Forks&logo=github)](https://github.com/P3TERX/aria2.sh/fork)

Aria2 是目前最強大的全能型下載工具，它支援 BT、磁力、HTTP、FTP 等下載協議，常用做離線下載的服務端。Aria2 一鍵安裝管理指令碼是 Toyo (逗比) 大佬最為知名的指令碼作品之一，2018年11月14日逗比大佬因未知原因突然失聯。由於博主非常喜歡 Aria2 所以自2018年12月7日起開始接手這個專案並進行了大量的功能與細節優化，一直持續維護至今。增強版指令碼整合了 [Aria2 完美配置](https://github.com/P3TERX/aria2.conf)，在安裝 Aria2 的過程中會下載這套配置方案，這套方案包含了配置檔案、附加功能指令碼等檔案，用於實現 Aria2 功能的增強和擴充套件，提升 Aria2 的下載速度與使用體驗，解決 Aria2 在使用中遇到的 BT 下載無速度、檔案殘留佔用磁碟空間、任務丟失、重複下載等問題。

## 功能特性

- 使用 [Aria2 完美配置](https://github.com/P3TERX/aria2.conf)方案
    * BT 下載率高、速度快
    * 重啟后不丟失任務進度、不重複下載
    * 刪除正在下載的任務自動刪除未完成的檔案
    * 下載錯誤自動刪除未完成的檔案
    * 下載完成自動刪除控制檔案(`.aria2`後綴名檔案)
    * 下載完成自動刪除種子檔案(`.torrent`後綴名檔案)
    * 下載完成自動刪除空目錄
    * BT 下載完成自動清除垃圾檔案(檔案型別過濾功能)
    * BT 下載完成自動清除小檔案(檔案大小過濾功能)
    * 有一定的防版權投訴、防迅雷吸血效果
    * 更好的 PT 下載支援

- 使用 [Aria2 Pro Core](https://github.com/P3TERX/Aria2-Pro-Core) 專案最新靜態編譯二進制檔案
    - 多平臺：`amd64`, `i386`, `arm64`, `armhf`
    - 全功能：`Async DNS`, `BitTorrent`, `Firefox3 Cookie`, `GZip`, `HTTPS`, `Message Digest`, `Metalink`, `XML-RPC`, `SFTP`
    - 單伺服器執行緒數最大值無上限（已破解執行緒數限制）
    - 防掉執行緒優化
    - 最新依賴庫，下載更安全、穩定、快速
    - 持續更新最新版本

- 支援與 [RCLONE](https://rclone.org/) 聯動，更多擴充套件功能與玩法：
    - [OneDrive、Google Drive 等網盤離線下載](https://p3terx.com/archives/offline-download-of-onedrive-gdrive.html)
    - [百度網盤轉存到 OneDrive 、Google Drive 等其他網盤](https://p3terx.com/archives/baidunetdisk-transfer-to-onedrive-and-google-drive.html)

- 支援新一代網際網路協議 IPv6
- 定時自動更新 BT tracker 列表（無需重啟）

## 專案地址

https://github.com/P3TERX/aria2.sh

支援專案請隨手點個`star`，可以讓更多的人發現、使用並受益。你的支援是我持續開發維護的動力。

## 系統要求

CentOS 6+ / Debian 6+ / Ubuntu 14.04+

## 架構支援

x86_64 / i386 / ARM64 / ARM32v7 / ARM32v6

## 使用說明

* 爲了確保能正常使用，請先安裝基礎元件`wget`、`curl`、`ca-certificates`，以 Debian 為例子：
```
apt install wget curl ca-certificates
```

* 下載指令碼
```
wget -N git.io/aria2.sh && chmod +x aria2.sh
```

* 執行指令碼
```
./aria2.sh
```

* 選擇你要執行的選項
```
 Aria2 一鍵安裝管理指令碼 增強版 [v2.7.4] by P3TERX.COM
 
  0. 升級指令碼
 ———————————————————————
  1. 安裝 Aria2
  2. 更新 Aria2
  3. 解除安裝 Aria2
 ———————————————————————
  4. 啟動 Aria2
  5. 停止 Aria2
  6. 重啟 Aria2
 ———————————————————————
  7. 修改 配置
  8. 檢視 配置
  9. 檢視 日誌
 10. 清空 日誌
 ———————————————————————
 11. 手動更新 BT-Tracker
 12. 自動更新 BT-Tracker
 ———————————————————————

 Aria2 狀態: 已安裝 | 已啟動

 自動更新 BT-Tracker: 已開啟

 請輸入數字 [0-12]:
```

## 其他操作

啟動：`/etc/init.d/aria2 start` | `service aria2 start`

停止：`/etc/init.d/aria2 stop` | `service aria2 stop`

重啟：`/etc/init.d/aria2 restart` | `service aria2 restart`

檢視狀態：`/etc/init.d/aria2 status` | `service aria2 status`

配置檔案路徑：`/root/.aria2c/aria2.conf` （配置檔案有中文註釋，若語言設定有問題會導致中文亂碼）

預設下載目錄：`/root/downloads`

RPC 金鑰：隨機產生，可使用選項`7. 修改 配置檔案`自定義

## 遇到問題如何處理

遇到問題先看 [FAQ](https://p3terx.com/archives/aria2_perfect_config-faq.html) 再提問，你還可以加入 [Aria2 TG 群](https://t.me/Aria2c)和小夥伴們一起討論。要注意提問的方式和提供有用的資訊，提問前建議去學習《[提問的智慧](https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way/blob/master/README-zh_CN.md)》，這能更好的幫助你去解決問題和節約時間。諸如 「為什麼不能使用？」、「那你能幫幫我嗎？」 之類的問題應該沒有人會知道。

## 更新日誌

更新推送：[Aria2 Channel](https://t.me/Aria2_Channel)

### 2020-12-26 v2.7.4 Final

> **NOTICE:** 由於指令碼程式碼歷史包袱太重，這將是最後一次維護更新。未來可能會寫一個全新的指令碼來替代。

- 更換 Aria2 二進制檔案下載鏈接
- 修復若干 bug

<details>
<summary>歷史記錄</summary>

### 2020-08-15 v2.7.0

- 新增 AriaNg 鏈接功能

### 2020-08-09 v2.6.2

- 修改 資源下載鏈接
- 優化 IP檢測介面

### 2020-07-12 v2.6.0

- 適配新版 [Aria2 完美配置](https://github.com/P3TERX/aria2.conf)
- 移除 Aria2 版本選擇功能

### 2020-06-27 v2.5.3

- 同步 Aria2 完美配置檔名改動
- 安裝過程優化
- 修復 bug

### 2020-05-21 v2.5.0

- 解決 CLI 下`aria2c`無法直接下載的問題
- 修改配置目錄為`/root/.aria2c`
- 修改下載目錄為`/root/downloads`

### 2020-05-20 v2.4.5

- 新增自動更新 BT Tracker 狀態顯示
- 改進指令碼升級策略
- 優化文案細節
- 修復部分歷史遺留 bug

### 2020-05-17 v2.3.0

- 優化 中國大陸「區域網」環境下的安裝體驗

### 2020-05-09 v2.2.5

- 新增 IPv6 地址檢測功能
- 優化防火墻設定，自動開放必要的埠。
- 修復部分歷史遺留 bug

### 2020-04-14 v2.2.1

- 優化 BT Tracker 列表更新策略，以無重啟方式進行（**自動更新 BT Tracker** 功能需重新進行設定）
- 優化程式碼細節，修復部分歷史遺留 bug

### 2020-02-18 v2.2.0

- 更換靜態編譯二進制檔案下載來源（[P3TERX/aria2-builder](https://github.com/P3TERX/aria2-builder)）
- 適配 ARM64、ARM32v7、ARM32v6 架構。
- 優化文案細節。

### 2020-02-17 v2.1.0

- 適配新版 [Aria2 完美配置](https://github.com/P3TERX/aria2.conf)
- 分離 trackers 更新功能
- 優化功能，完善細節，修復若干 bug

### 2019-11-23 v2.0.8

- 修改 Trackers 來源([XIU2/TrackersListCollection](https://github.com/XIU2/TrackersListCollection))

### 2019-10-12 v2.0.7

- 修復 Aria2 版本更新時因未獲取 CPU 架構導致版本下載錯誤且無法啟動的 bug

### 2019-09-30 v2.0.6

- 獲取 DHT（IPv6）檔案

### 2019-06-08 v2.0.5

- 增加 清空日誌 功能
- 調整 部分文案

### 2018-12-25 v2.0.4

- 優化調整

### 2018-12-24 v2.0.3

- 增加 重置/更新 Aria2 完美配置 選項
- 優化 修改配置檔案下載路徑時同步修改附加功能指令碼中的下載路徑

### 2018-12-8 v2.0.2

- 修復 附加功能指令碼沒有執行許可權的 bug

### 2018-12-7 v2.0.1

- 修復 設定下載資料夾提示不存在的 bug
- 解鎖 更新 BT-Tracker伺服器 選項

### 2018-12-7 v2.0.0α

- 整合 [Aria2 完美配置](https://github.com/P3TERX/aria2_perfect_config)

### 2018-10-18 v1.1.10

- 取自[一個逗比寫的逗比指令碼](https://github.com/P3TERX/doubi_backup)
- 感謝 Toyo 大佬

</details>

## Lisence
[MIT](https://github.com/P3TERX/aria2.sh/blob/master/LICENSE) © Toyo x P3TERX

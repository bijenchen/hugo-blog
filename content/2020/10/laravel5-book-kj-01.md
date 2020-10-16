---
title: "初探&建環境"
date: 2020-10-04T15:24:32+08:00
draft: false
tags: ["latavel 5","reflection"]
pre : "<b>[讀書筆記]Laravel 5 for beginner 新手道場 </b>"
---
> 發布日期：2020-10-16
> 最後更新日期：2020-10-16

## 閱讀書籍： Laravel 5 for beginner 新手道場
#### 作者： 洪可郡（KeJyun）

* [博客來連結](https://www.books.com.tw/products/0010773916)
* [gitbook](http://kejyun.github.io/Laravel-5-Learning-Notes-Books/)

<!-- 內文 -->
## Laravel 初探

* 開發網站使用框架的理由
    + 當我們遇到以下情境，使用框架會帶來不少好處：
        - 整個網站的功能複雜，需要一個系統化、層級明確、分工清楚的程式架構，以便規劃與維護
            + *note: 就像小團隊可以不用明確組織架構也能順利運作，但到一定規模以後每個部門就會有明確層級跟分工，一但出現新任務才會知道要找誰來做。也像是東西要分門別類收好，要用的時候才容易找。*
        - 有時程壓力，需要迅速完工
            + *note: 大多數專案都會用到的功能，框架通常會很貼心地幫我們做好，讓我們可以直接使用，省時省工。而在自己的程式架構中，把功能切得越獨立，也越容易單獨提取、重複使用，一樣省時省工。*
        - 需要跟他人合作打造專案
            + *note: 彼此都懂使用的框架在寫什麼、在幹嘛，可以省去很多解釋與溝通的時間。就像大家都知道什麼作用的工具放在哪裡，不用說明就能自行找到並且拿來用。*
    + *note: 框架有分前端和後端，但「需要框架的情境」、「框架帶來的好處」不分前後端都適用*

* 選框架的方法
    + 維護性
        - 如果打算開發商業產品，至少要選「有 LTS(Long-term support) 版本可用」的框架
            + *note: 才不會變成沒人維護的孤兒專案，找到 bug 至少還有人會去改。*
        - 框架更新是成本，如果是商業產品，請務必謹慎評估後再更新。如果有好好寫單元測試(Unit test)的話，至少可以在更新時確保更新前後程式都能滿足相同的商業邏輯，不會出錯。
    + 擴充性
        - 該框架是否容易引入套件、套件選擇多
            + *note: 專案需求千奇百怪，但框架通常是以大家的最大公約數在設計。如果框架本身對套件的包容性高，就能接納其他高手提供的套件，使用該框架的人也會越來越多。當使用的人變多，框架的 bug 就越容易被發現與修復，增加框架的穩定度。使用上會更加安心～*
        - 加碼說明： php 的套件管理工具「 composer 」
            + *note: 套件管理工具會聰明的判斷使用哪個版本號的套件，避免更新之後新舊版本互斥、程式掛掉。*
    + 因為 Laravel 滿足上述所有條件，使用者多、安裝方便、擴充性也很夠，觀察使用者社群趨勢也還維持成長狀態，所以選擇 Laravel 作為開發專案的框架。

## 設定 Laravel 開發環境

* Laravel 很貼心地幫大家降低環境阻礙，提供 Homestead 虛擬環境給開發者。所以第一步就是建立 Homestead 虛擬環境，原則上依照 [laravel 官網](https://laravel.com/) 的 documentation 步驟走就行了。(我選的是 laravel 7.x 的版本，因為 8.x 的版本寫法貌似有做調整，為免節外生枝，先用與書上寫法一致的版本)
    + 大原則：(細節可能會因為官網更新而有差異，請以官網為主～)
        - Homestead 需要在虛擬機跑，依照 documentation 上 Getting Started 裡的 [homestead](https://laravel.com/docs/7.x/homestead) 段落，事先準備好對應版本的虛擬機器(VirtualBox, VMWare ......選一個裝起來，不想煩腦的話就跟書上一樣裝 VirtualBox )和虛擬環境配置軟體 Vagrant 。
            * ![安裝版本指示位置](https://lh3.googleusercontent.com/pw/ACtC-3clSGHn054o1wz-roM43i0yHoLVFdt_x76xMGsGuJBupmeSxAhQaOKu_BJY1bMbSDoEPo8nibssX-QaauewOq1SonURkycKdOddSBQ9a5LN5Tx1Jhh59z71d0sm8kStSZ6nO6NK3wz9vY_hJvg5gGLY=w2032-h912-no?authuser=0)
        - 準備好虛擬機器與虛擬環境配置軟體以後，在虛擬機器中下載 Vagrant 裡的 Homestead 環境映像檔
            * 添加環境映像檔 : `vagrant box add laravel/homestead`
            * ![add_homestead](https://lh3.googleusercontent.com/pw/ACtC-3creipZ0abeI_a6wqD98D9iuuThkwCe14KSrgneF93qFBneJgxx00JLl1WPDWm8L6WgbeFmXiFez3lT1F64bJMCjm5HSsSoUHXB2C7iLA4-otpB5iQ-oPdTkFgAogGE8vn5tDRJjC_Vzx_0kaYzrMWR=w2038-h1284-no?authuser=0)
        - 取得 Homestead 設定檔
            * ![homestead_version](https://lh3.googleusercontent.com/pw/ACtC-3ec4VuvdJGr012X78UrIj80oR2r9mRoDIyxlgONlcJJSi60icON3VFRnPcVMbnRlFDnqAAUbFomf5tkRAT0zXDb1rMa0FgdbMojoiOwwzX7IyrOqMiIs3V0XZrOu-0is265L0wWzcoRPcIXkHlG5jHI=w2072-h1136-no?authuser=0)
        - 初始化 Homestead 以後，就可以啟動裝有 Homestead 環境的虛擬機器了
            * 初始化 Homestead : `bash init.sh`
            * 啟動虛擬機器 : `vagrant up`
                + 啟動以後，可以確認虛擬機器的狀態變化。不開發時記得關閉(`vagrant halt`)以免佔用資源。
                + ![vagrant_halt](https://lh3.googleusercontent.com/pw/ACtC-3frsPCsZfQ3TvJzi0sZojg73H67NKYRoLZUWH6DXip2Iq8iiGITvPGnwrWMeSX3YyKcV33JR8C_t4pqXfI99y3y91EoZHuxDeQBxi6kL8sy61EgjxGimIRj2djzPvj_Cdn5_93fPYhInzn_bG3Ca-gU=w1062-h336-no?authuser=0)
* 在 Homestead 環境中安裝 laravel
    + 記得選用自己想要的版本～
    + ![install_laravel](https://lh3.googleusercontent.com/pw/ACtC-3f5SzoCN31bqUGyH3__Qvc0p7kQT8Ai572RqsxUzQ_dWNtg33434WpgBsgCz0VdwL6BzKszLN0QqDzxtnP_hjxS2v6j9mhmJVvYEKJ4kpQL8knEBjz0NYgkb9RxPLcxf-LpiF8qwG_C9dYEc3JemQap=w1978-h586-no?authuser=0)
    + 安裝成功的話，就可以在專案資料夾裡看到完整的 laravel 框架結構囉！
    + ![directory_structure](https://lh3.googleusercontent.com/pw/ACtC-3fmw3za1SGg7XouIxg7zyvl8FheNOKs1uxPu3NDpAKcg46NCVZRIZe_26ERv6qPE3xSEUnGQpMXsiml3RAu0LnBoknJWa0Zb7IznD4A49xcSqeth0HJex5qXawP4FMSdomv204NkrJA7UCpDiSb3tCx=w1498-h1078-no?authuser=0 "directory_structure")
* *note: 版本選對，安裝就會順順利利～請忠實跟隨與時俱進的官網文件。*

* `vagrant ssh` 進入 Homestead 虛擬主機之後 `ls` 看一下， Homestead.yaml 檔共享目錄裡紀錄的虛擬主機目錄真的有存在。所以應該是執行 `bash init.sh` 的時候，按照當時下載的 Homestead 檔案建立 Homestead 虛擬環境(這邊是初始化， Homestead.yaml 異動後要更新環境的話，需使用 `vagrant provision`)。

## 參考資料
- [laravel 官網](https://laravel.com/)
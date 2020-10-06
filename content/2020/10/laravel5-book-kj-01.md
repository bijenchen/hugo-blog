---
title: "初探&建環境"
date: 2020-10-04T15:24:32+08:00
draft: true
tags: ["latavel 5","reflection"]
pre : "<b>[讀書筆記]Laravel 5 for beginner 新手道場 </b>"
---
> 發布日期：2020-10-??
> 最後更新日期：2020-10-07

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

* Laravel 很貼心地幫大家降低環境阻礙，提供 Homestead 虛擬環境給開發者。所以第一步就是建立 Homestead 虛擬環境。
* *note: 由於 Homestead 要在 vitural box 上運作，書上特別強調必須依照 Homestead 的版本要求選擇對應的 vitural box 。但是我要在哪裡知道目前的 Homestead 需要哪個版本的 Virtual Box ?*

  *google 「Laravel Homestead」找到了 Laravel Homestead 的[說明文件](https://laravel.tw/docs/5.1/homestead)，文件上說要用 5.x 版本的 vitural box ，所以雖然 vitural box 目前已經推到 6.x 的版本，也不要選最新版避免節外生枝。*
* *note: vargant 提供的安裝選項有新增為四項，一樣選用 virtualbox*
    - 1) hyperv
    - 2) parallels
    - 3) virtualbox
    - 4) vmware_desktop

    這邊等了快半小時，看來我的網速不夠飛速 XD

* Homestead 設定檔進展很多，現在到 v11.1.2 了！@@
    + 差異
        - sites 的網域設定裡的預設值「 .local 」變成「 .test 」了，但這邊反正可以取自己喜歡像是 [yourname].laravel-site 之類的，所以無傷大雅。
        - 新版本的 Homestead.yaml 多了一些可以設定的項目，但預設都是關起來的
           ```
           features:
                - mariadb: false
                - ohmyzsh: false
                - webdriver: false

            #services:
            #    - enabled:
            #        - "postgresql@12-main"
            #    - disabled:
            #        - "postgresql@11-main"

            # ports:
            #     - send: 50000
            #       to: 5000
            #     - send: 7777
            #       to: 777
            #       protocol: udp
           ```

* `vagrant ssh` 進入 Homestead 虛擬主機之後 `ls` 看一下， Homestead.yaml 檔共享目錄裡紀錄的虛擬主機目錄真的有存在。所以應該是執行 `bash init.sh` 的時候，按照當時下載的 Homestead 檔案建立 Homestead 虛擬環境(這邊是初始化， Homestead.yaml 異動後要更新環境的話，需使用 `vagrant provision`)。

* 指令好長，不想再打第二次，以後只想用複製的，先存起來
    + `composer create-project --prefer-dist laravel/laravel shop_laravel`

* 卡關惹Q___Q 先休息冷靜一下(2020-10-07 過午夜了Q_____Q)
    - 在 code/ 執行 `composer create-project --prefer-dist laravel/laravel shop_laravel` 時，遇到 [InvalidArgumentException]
        ```
        vagrant@homestead:~/code$ composer create-project --prefer-dist laravel/laravel shop_laravel
        ```
        ```
        [InvalidArgumentException]
            Composer could not find a composer
            .json file in /home/vagrant/code/s
            hop_laravel
            To initialize a project, please cr
            eate a composer.json file as descr
            ibed in the https://getcomposer.or
            g/ "Getting Started" section
        ```
    - 把 shop_laravel/ 放在 /home/vagrant/ 層級下
        + 也就是前一步往外一層執行 `composer create-project xxxxxxx`
            - 得到「 Application key set successfully. 」
        + public/ 路徑長這樣： /home/vagrant/shop_laravel/public
        + /etc/hosts
            - `192.168.10.10   shop-laravel.local`
        + *Homestead.yaml* sites:
            - map: shop-laravel.local
            - to: /home/vagrant/shop_laravel/public
        + 此時進入 http://shop-laravel.local/ 會顯示「 No input file specified. 」

## 先存著之後細讀，首次啟動 homestead 跑的相關設定
```
Bringing machine 'homestead' up with 'virtualbox' provider...
==> homestead: Box 'laravel/homestead' could not be found. Attempting to find and install...
    homestead: Box Provider: virtualbox
    homestead: Box Version: ~> 10.0.0
==> homestead: Loading metadata for box 'laravel/homestead'
    homestead: URL: https://vagrantcloud.com/laravel/homestead
==> homestead: Adding box 'laravel/homestead' (v10.0.0) for provider: virtualbox
    homestead: Downloading: https://vagrantcloud.com/laravel/boxes/homestead/versions/10.0.0/providers/virtualbox.box
Download redirected to host: vagrantcloud-files-production.s3.amazonaws.com
    homestead: Calculating and comparing box checksum...
==> homestead: Successfully added box 'laravel/homestead' (v10.0.0) for 'virtualbox'!
==> homestead: Importing base box 'laravel/homestead'...
==> homestead: Matching MAC address for NAT networking...
==> homestead: Checking if box 'laravel/homestead' version '10.0.0' is up to date...
==> homestead: Setting the name of the VM: homestead
Vagrant is currently configured to create VirtualBox synced folders with
the `SharedFoldersEnableSymlinksCreate` option enabled. If the Vagrant
guest is not trusted, you may want to disable this option. For more
information on this option, please refer to the VirtualBox manual:

  https://www.virtualbox.org/manual/ch04.html#sharedfolders

This option can be disabled globally with an environment variable:

  VAGRANT_DISABLE_VBOXSYMLINKCREATE=1

or on a per folder basis within the Vagrantfile:

  config.vm.synced_folder '/host/path', '/guest/path', SharedFoldersEnableSymlinksCreate: false
==> homestead: Clearing any previously set network interfaces...
==> homestead: Preparing network interfaces based on configuration...
    homestead: Adapter 1: nat
    homestead: Adapter 2: hostonly
==> homestead: Forwarding ports...
    homestead: 80 (guest) => 8000 (host) (adapter 1)
    homestead: 443 (guest) => 44300 (host) (adapter 1)
    homestead: 3306 (guest) => 33060 (host) (adapter 1)
    homestead: 4040 (guest) => 4040 (host) (adapter 1)
    homestead: 5432 (guest) => 54320 (host) (adapter 1)
    homestead: 8025 (guest) => 8025 (host) (adapter 1)
    homestead: 9600 (guest) => 9600 (host) (adapter 1)
    homestead: 27017 (guest) => 27017 (host) (adapter 1)
    homestead: 22 (guest) => 2222 (host) (adapter 1)
==> homestead: Running 'pre-boot' VM customizations...
==> homestead: Booting VM...
==> homestead: Waiting for machine to boot. This may take a few minutes...
    homestead: SSH address: 127.0.0.1:2222
    homestead: SSH username: vagrant
    homestead: SSH auth method: private key
    homestead: Warning: Connection reset. Retrying...
    homestead: Warning: Remote connection disconnect. Retrying...
    homestead:
    homestead: Vagrant insecure key detected. Vagrant will automatically replace
    homestead: this with a newly generated keypair for better security.
    homestead:
    homestead: Inserting generated public key within guest...
    homestead: Removing insecure key from the guest if it's present...
    homestead: Key inserted! Disconnecting and reconnecting using new SSH key...
==> homestead: Machine booted and ready!
==> homestead: Checking for guest additions in VM...
    homestead: The guest additions on this VM do not match the installed version of
    homestead: VirtualBox! In most cases this is fine, but in rare cases it can
    homestead: prevent things such as shared folders from working properly. If you see
    homestead: shared folder errors, please make sure the guest additions within the
    homestead: virtual machine match the version of VirtualBox you have installed on
    homestead: your host and reload your VM.
    homestead:
    homestead: Guest Additions Version: 6.1.8
    homestead: VirtualBox Version: 5.2
==> homestead: Setting hostname...
==> homestead: Configuring and enabling network interfaces...
==> homestead: Mounting shared folders...
    homestead: /vagrant => /Users/bijen/Code/Homestead
    homestead: /home/vagrant/code => /Users/bijen/Code
    homestead: /home/vagrant/laravel_project => /Users/bijen/laravel_project
==> homestead: Detected mount owner ID within mount options. (uid: 1000 guestpath: /home/vagrant/code)
==> homestead: Detected mount group ID within mount options. (gid: 1000 guestpath: /home/vagrant/code)
==> homestead: Detected mount owner ID within mount options. (uid: 1000 guestpath: /home/vagrant/laravel_project)
==> homestead: Detected mount group ID within mount options. (gid: 1000 guestpath: /home/vagrant/laravel_project)
==> homestead: Running provisioner: file...
    homestead: /Users/bijen/Code/Homestead/aliases => /tmp/bash_aliases
==> homestead: Running provisioner: shell...
    homestead: Running: inline script
==> homestead: Running provisioner: shell...
    homestead: Running: inline script
    homestead:
    homestead: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDJt0x32prG1C6p/hrKDhLLm+UVl77aoZEuSfALANQWCsptM3kt51no+JIu8J8C9WoTeurwATZLP1tXeAPH4YIUn/xPEOi+iXqzIrJNNK6qk1vN1Ih0WxA2rDO2aPwjL0s8gIRp9VDKhIaL+nzCwWQTqAzvnNGU04qnlKXPiAT8Wpn5b0XnA07cMsswUFNMsT6dbAew/lj7kA+BWyC3eQhI+WeTgWsPWnXsVQu97O/al8DJL+TGhS3ZWRFGsUfoiKY2SM48GULWGLzdlrhvJCDs3aIEIhGC1EcDMxy2KFUCxjhh3/WqtOtlFbwv3deLcgw7R3TqPZO4ImRfaNmllKqZ i-am-bijen
==> homestead: Running provisioner: shell...
    homestead: Running: inline script
==> homestead: Running provisioner: shell...
    homestead: Running: inline script
==> homestead: Running provisioner: shell...
    homestead: Running: inline script
==> homestead: Running provisioner: shell...
    homestead: Running: inline script
    homestead: Ignoring feature: mariadb because it is set to false
==> homestead: Running provisioner: shell...
    homestead: Running: inline script
    homestead: Ignoring feature: ohmyzsh because it is set to false
==> homestead: Running provisioner: shell...
    homestead: Running: inline script
    homestead: Ignoring feature: webdriver because it is set to false
==> homestead: Running provisioner: shell...
    homestead: Running: /var/folders/zg/z6qg4xpx70d_0091ntyg0plm0000gp/T/vagrant-shell20201004-43309-17ev9xw.sh
==> homestead: Running provisioner: shell...
    homestead: Running: /var/folders/zg/z6qg4xpx70d_0091ntyg0plm0000gp/T/vagrant-shell20201004-43309-abia02.sh
==> homestead: Running provisioner: Creating Certificate: homestead.test (shell)...
    homestead: Running: script: Creating Certificate: homestead.test
    homestead: Updating certificates in /etc/ssl/certs...
    homestead: rehash: warning: skipping duplicate certificate in ca.homestead.homestead.pem
    homestead: 1 added, 0 removed; done.
    homestead: Running hooks in /etc/ca-certificates/update.d...
    homestead: done.
==> homestead: Running provisioner: Creating Site: homestead.test (shell)...
    homestead: Running: script: Creating Site: homestead.test
==> homestead: Running provisioner: shell...
    homestead: Running: inline script
==> homestead: Running provisioner: shell...
    homestead: Running: /var/folders/zg/z6qg4xpx70d_0091ntyg0plm0000gp/T/vagrant-shell20201004-43309-si82a2.sh
==> homestead: Running provisioner: Checking for old Schedule (shell)...
    homestead: Running: script: Checking for old Schedule
==> homestead: Running provisioner: Creating Certificate: bijen.laravel-site (shell)...
    homestead: Running: script: Creating Certificate: bijen.laravel-site
==> homestead: Running provisioner: Creating Site: bijen.laravel-site (shell)...
    homestead: Running: script: Creating Site: bijen.laravel-site
==> homestead: Running provisioner: shell...
    homestead: Running: inline script
==> homestead: Running provisioner: shell...
    homestead: Running: /var/folders/zg/z6qg4xpx70d_0091ntyg0plm0000gp/T/vagrant-shell20201004-43309-1e955wi.sh
==> homestead: Running provisioner: Checking for old Schedule (shell)...
    homestead: Running: script: Checking for old Schedule
==> homestead: Running provisioner: Clear Variables (shell)...
    homestead: Running: script: Clear Variables
==> homestead: Running provisioner: Restarting Cron (shell)...
    homestead: Running: script: Restarting Cron
==> homestead: Running provisioner: Restart Webserver (shell)...
    homestead: Running: script: Restart Webserver
==> homestead: Running provisioner: Creating MySQL Database: homestead (shell)...
    homestead: Running: script: Creating MySQL Database: homestead
    homestead: We didn't find a PID for mariadb, skipping $DB creation
==> homestead: Running provisioner: Creating Postgres Database: homestead (shell)...
    homestead: Running: script: Creating Postgres Database: homestead
==> homestead: Running provisioner: Update Composer (shell)...
    homestead: Running: script: Update Composer
    homestead: Updating to version 1.10.13 (stable channel).
    homestead:
    homestead: Use composer self-update --rollback to return to version 1.10.9
==> homestead: Running provisioner: shell...
    homestead: Running: /var/folders/zg/z6qg4xpx70d_0091ntyg0plm0000gp/T/vagrant-shell20201004-43309-px4t6p.sh
==> homestead: Running provisioner: Update motd (shell)...
    homestead: Running: script: Update motd
==> homestead: Running provisioner: shell...
    homestead: Running: /var/folders/zg/z6qg4xpx70d_0091ntyg0plm0000gp/T/vagrant-shell20201004-43309-vbzsh2.sh
```


bijen.laravel-site

## 還沒解的疑問

* 使用 Homestead 究竟省掉多少事？實際上它處理掉哪些事情？
  + 其一：不用自己設定 nginx
* vargant 在做什麼？
* 為何要選家目錄放置 Homestead 和專案？用其他層會造成什麼問題嗎？
* 為何要開兩個資料夾？ Code & laravel_project ？看起來 laravel_project 資料夾會放使用 laravel 框架做出來的網站的程式碼，那 Code 呢？
* Homestead.yaml 裡的設定，為何大家的 ip 會一樣？是因為 192.168.10.10 代表 virtualbox 的 ip 嗎？
    - 好像是 Homestead 的預設主機 ip ，[這裡](http://kejyun.github.io/Laravel-5-Learning-Notes-Books/environment/Environment-Homestead-README.html)說的。可是 KJ gitbook 上說「Homestead 預設的主機 ip 都為 192.168.10.11」，所以是依照不同版本的 Homestead.yaml 喜歡指定哪個 ip 變動，其實 ip 只要不跟人撞，就可以自己寫開心？
    - ip 分成四段的數字個字代表什麼意義？每一段都有專門對應的意義嗎？裡面有什麼約定俗成的默契嗎？
* 為什麼[這裡](http://kejyun.github.io/Laravel-5-Learning-Notes-Books/environment/Environment-Homestead-README.html)在執行完 `vagrant up` 後就可以看到 http://kejyun.app 的內容？我在執行完之後先看設定好的 domain ，只看到 *No input file specified.*
    - 難道說有途徑可以「在 `vagrant up` 之前就裝好 laravel 」?所以原來 laravel 不是裝在 homestead 裡面?!!但是看書裡的描述應該是裝在 homestead 才對？我誤會了哪一邊？@@


## 參考資料
- [Laravel Homestead](https://laravel.tw/docs/5.1/homestead)
- [Homestead 發布版本](https://packagist.org/packages/laravel/homestead)
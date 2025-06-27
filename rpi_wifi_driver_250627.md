# Raspberry Pi 4B/5に無線LANドライバーをインストール

### [Device] Archer T2U Nano AC600 (TP-LINK AC600 REALTEK RTL8811AU)

### **aircrack-ng/rtl8812au リポジトリを使用**

[RTL8812AU/21AU and RTL8814AU Wireless drivers](https://github.com/aircrack-ng/rtl8812au)

1. ビルドで依存するパッケージのインストール
   
   ```
   sudo apt install bc mokutil build-essential libelf-dev linux-headers-`uname -r` 
   ```

2. Githubレポジトリをクローンする
   
   ```
   git clone -b v5.6.4.2 https://github.com/aircrack-ng/rtl8812au.git
   cd rtl*
   ```

3. makeでドライバーをビルドしてインストール
   
   ```
   sudo make
   sudo make install
   ```
   
   mekeするのに約10分かかる

4. NetworkManagerを再起動
   
   ```
   sudo service NetworkManager restart
   ```

### 

### [Device] TP-Link Archer T3U Nano (TP-LINK Wi-Fi) / EP-AC1686 (REALTEK RTL88x2BU)

### morrownr/88x2bu リポジトリを使用

[Linux Driver for USB WiFi Adapters that are based on the RTL8812BU and RTL8822BU Chipsets](https://github.com/morrownr/88x2bu-20210702)

1. システムを最新の状態にする
   for Debian based distributions such as Ubuntu, Kali, Armbian and Raspberry Pi OS
   
   ```
   sudo apt update && sudo apt upgrade
   ```

2. 必要なツールとヘッダーファイルをインストールする
   for Raspberry Pi OS (arm/arm64)
   
   ```
   sudo apt install -y raspberrypi-kernel-headers build-essential bc dkms git
   ```

3. ドライバーを保存するディレクトリを作る
   
   ```
   mkdir -p ~/src
   cd ~/src
   ```

4. RTL88x2BUドライバーのソースコードをダウンロードする
   
   ```
   git clone https://github.com/morrownr/88x2bu-20210702.git
   cd ~/src/88x2bu-20210702
   ```

5. ドライバーをコンパイルしてインストールする
   
   ```
   sudo apt install gcc-12
   sudo ./install-driver.sh
   ```
   
   時間がかかる(約5分)
   
   以下の問いに答えると自動的に再起動する
   ```
   Do you want to edit the driver options file now? (recommended) [Y/n] n
   Do you want to apply the new options by rebooting now? (recommended) [Y/n] y
   ```

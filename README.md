1 USBでブートするためのおまじない
  電源押して、PCのタイトルが出たらF12を押す
  次にUSBを選択してエンター
  次に起動の選択画面になるので「e」を押す
  次に下ののような文字列が並ぶので、「-- 」より右の文字列を追加して、保存
  USBの起動が始まればOK
```
setparams 'Try Ubuntu without Installing'

        set gfxpayload-keep
        linux         /casper/vmlinuz file/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- ivrs_ioapic[32]=00:14.0 ivrs_ioapic[33]=00:00.1 clocksource=hpet libata.force=1:nohrst iommu=pt
        initrd        /casper/initrd
```
https://github.com/gllrmzndm/Installing_Linux_on_ThinkPad_E585/blob/master/Installing_Ubuntu_on_E585.md

2. 文字変換をCTRL + SPACE にする。
   最初に設定用のプログラムを追加
   ```
   sudo apt install mozc-utils-gui
   ```
   次に、右上の電源ボタンを押して設定画面を選択。そこからキーボード項目を選択して、入力ソースを「日本語」のみにする。
   下記は削除前  
![image](https://github.com/kaooshim/ubuntusetup/assets/63496960/72da2672-8c4b-4eb7-9770-941abd398f45)


次に日本語の３点リーダーを押して、キー設定の「編集」を選択肢、２つのアクションをCTRL+SPACEに変更する  
設定したらログアウトする
![image](https://github.com/kaooshim/ubuntusetup/assets/63496960/4c623ad5-ef52-42b7-bff3-df02f9d958b9)

![image](https://github.com/kaooshim/ubuntusetup/assets/63496960/4ddae190-5e5e-4b15-abe3-9316341e6b9e)
![image](https://github.com/kaooshim/ubuntusetup/assets/63496960/a5225e56-f9a9-491a-b389-7928a6843085)

3. フォルダを英字名にする
   ```
   LANG=C xdg-user-dirs-gtk-update
   ```
         " Don't ask me this again " にチェックを入れて、[ Update Names ] をクリック

4. Dockのショートカットを変更する（Intellijのショートカットとぶつかる想定）
   Super(win) + 1 の機能を　Super + Alt + 1 にする（２−９も）
   .bashrc に記入する
   ```
   gsettings set org.gnome.shell.extensions.dash-to-dock app-hotkey-1 "['<Super><Alt>1']"
   gsettings set org.gnome.shell.extensions.dash-to-dock app-hotkey-2 "['<Super><Alt>2']"
   gsettings set org.gnome.shell.extensions.dash-to-dock app-hotkey-3 "['<Super><Alt>3']"
   gsettings set org.gnome.shell.extensions.dash-to-dock app-hotkey-4 "['<Super><Alt>4']"
   gsettings set org.gnome.shell.extensions.dash-to-dock app-hotkey-5 "['<Super><Alt>5']"
   gsettings set org.gnome.shell.extensions.dash-to-dock app-hotkey-6 "['<Super><Alt>6']"
   gsettings set org.gnome.shell.extensions.dash-to-dock app-hotkey-7 "['<Super><Alt>7']"
   gsettings set org.gnome.shell.extensions.dash-to-dock app-hotkey-8 "['<Super><Alt>8']"
   gsettings set org.gnome.shell.extensions.dash-to-dock app-hotkey-9 "['<Super><Alt>9']"
   gsettings set org.gnome.shell.extensions.dash-to-dock app-hotkey-10 "['<Super><Alt>0']"
   
   gsettings set org.gnome.shell.keybindings switch-to-application-1 "['<Super><Alt>1']"
   gsettings set org.gnome.shell.keybindings switch-to-application-2 "['<Super><Alt>2']"11
   gsettings set org.gnome.shell.keybindings switch-to-application-3 "['<Super><Alt>3']"
   gsettings set org.gnome.shell.keybindings switch-to-application-4 "['<Super><Alt>4']"
   gsettings set org.gnome.shell.keybindings switch-to-application-5 "['<Super><Alt>5']"
   gsettings set org.gnome.shell.keybindings switch-to-application-6 "['<Super><Alt>6']"
   gsettings set org.gnome.shell.keybindings switch-to-application-7 "['<Super><Alt>7']"
   gsettings set org.gnome.shell.keybindings switch-to-application-8 "['<Super><Alt>8']"
   gsettings set org.gnome.shell.keybindings switch-to-application-9 "['<Super><Alt>9']"
   gsettings set org.gnome.shell.keybindings switch-to-application-0 "['<Super><Alt>0']"
   ```

5. IntellijのキーマップをMac風にする
   TweakToolをインストールして起動
   ```
   sudo apt update
   sudo apt-add-repository universe
   sudo apt install gnome-tweaks
   gnome-tweaks
   ```
   キーボードとマウスのメニューを開いて「追加のレイアウトオプション」を選択「Meta is mapped to Win」にする
   ![image](https://github.com/kaooshim/ubuntusetup/assets/63496960/4010c225-6c29-4401-bce1-e79d1a0e22f0)
   ![image](https://github.com/kaooshim/ubuntusetup/assets/63496960/26d76ef2-85dc-458d-839e-dcd163a599b2)


6. WinキーとAltきーを入れ替える
   ```
   sudo cp evdev evdev_org
   sudo vi evdev
     LALT を LWIN の数値（入れたときは133）
     LWIN を LALT の数値（入れたときは64）
   ```
   ログインし直す。
  　https://h-iijima.hatenadiary.org/entry/20110307/1299489812

7. Intellij入れる
    https://www.jetbrains.com/help/idea/installation-guide.html#toolbox
    desktopアイコンをランチャーに入れる。ファイルの場所は/home/leno/.local/share/applications。ファイル名は自由だけど拡張子は .desktop

   ---
   #!/usr/bin/env xdg-open  
   [Desktop Entry]  
　　Version=2023.03  
　　Terminal=false  
　　Type=Application  
　　Name=Intellij  
　　Exec="/opt/idea-IU-232.9559.62/bin/idea.sh" %f  
　　Icon=/opt/idea-IU-232.9559.62/bin/idea.png  
　　StartupWMClass=jetbrains-idea

   ---
   ソフトウェア検索で作ったアイコンを検索してアプケーションに登録する
   ![image](https://github.com/kaooshim/ubuntusetup/assets/63496960/39e32305-41b8-4e93-b3d0-41b26c621220)

8. IntellijのキーマップをMac似変更
   




   
 

   


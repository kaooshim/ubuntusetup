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
   Super(win) + 1 の機能を　Super + Shift + 1 にする（２−９も）
   .bashrc に記入する  

   


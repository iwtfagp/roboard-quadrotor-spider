Arduino DIY---ATmega8(一)---安裝bootloader
http://robotrabbit.blogspot.tw/2012/08/arduino-diy-atmega8bootloader.html
Arduino DIY---ATmega8(二)---Max232
http://robotrabbit.blogspot.tw/2012/08/arduino-diy-atmega8-max232.html


![http://4.bp.blogspot.com/-fj7iAFbJuRo/UPektLUe4BI/AAAAAAAAAlA/Yqq5HeA8njU/s1600/2013-01-10+13.54.17.jpg](http://4.bp.blogspot.com/-fj7iAFbJuRo/UPektLUe4BI/AAAAAAAAAlA/Yqq5HeA8njU/s1600/2013-01-10+13.54.17.jpg)
利用Arduino讀取遙控器的資料，接著將資料拿來控制飛天蜘蛛的腳。

這些程式碼都會放在google code上面，提供給大家下載使用

Arduino部分
RC\_control：用來接收遙控器的資料
setservo：設定伺服馬達位置用
servokey\_control：主要的程式碼，可以利用接收器所得到的資料去控制伺服馬達和飛行
![http://2.bp.blogspot.com/-rAdzGJq9go0/UPeku7RqfFI/AAAAAAAAAlU/NEB8scEkyWc/s1600/2013-01-10+14.08.37.jpg](http://2.bp.blogspot.com/-rAdzGJq9go0/UPeku7RqfFI/AAAAAAAAAlU/NEB8scEkyWc/s1600/2013-01-10+14.08.37.jpg)
![http://4.bp.blogspot.com/-pGnUOQ1-ZX4/UPekuVLFEwI/AAAAAAAAAlM/xGM5B9U7TJs/s1600/2013-01-10+13.58.17.jpg](http://4.bp.blogspot.com/-pGnUOQ1-ZX4/UPekuVLFEwI/AAAAAAAAAlM/xGM5B9U7TJs/s1600/2013-01-10+13.58.17.jpg)

左手邊的那個就是接收器，是一個小盒子，左手邊的是遙控器，是使用2.4G的傳輸模式，在使用之前當然要先做過一些基本的調整和對頻。



---


提到2.4G就順便說說相關的資料好了，可能很多人對於這些尚且不是很了解。

遙控器希望藉由我手上推動搖桿後所得到的一些電子訊號傳遞出去，再由一個小盒子接收訊號，並且轉換成我們想要的PWM資料，希望達到這樣的效果，我們就得使用「電磁波」 (Electromagnetic Wave) ，電磁波這種東西像是紅外線、紫外線和可見光等等都是所謂的電磁波，而電磁波譜中約在3KHz～300GHz等區域的電磁波被稱之為「無線電」，其波長從1mm到100Km，而一般的可見光波長則是400nm~700nm，由此可見無線電的波長相當的長，而且範圍相當的廣。

那麼為何要使用無線電呢？可以用其他光來傳訊息嗎？當然可以，紅外線也是一種傳遞訊息的方式，但是大家都知道，紅外線是有可能會被擋住的，假如隔了道牆壁，紅外線傳輸就會出現問題，可是無線電卻不一樣，他有著不容易被其他物質遮蔽的特性，因此有些天文學的觀測技術就是利用無線電訊號來觀測星體運作，也就是所謂的「電波望遠鏡」。

無線電運用範圍很廣，主要應用在於通訊方面，由於無線電很好用，大家希望能夠利用這樣的工具來遙控資料或是傳遞資料，像是我想要遙控我的飛機一樣，但是如果你用到的訊號和我一模一樣，我的飛機要聽誰的？因此發展出許多中的調變技術，一般收音機最常見的就是AM調幅（Amplitude Modulation）和FM調頻（Frequency Mpdulation），這也是以前的遙控所用的方式，你必須在你的飛機接收機上面裝一個和遙控器一樣頻率的振盪器，才可以進行遙控，不幸的是，如果你的震盪器又和別人一樣呢???這時候不就又發生一樣的悲劇了嗎？

2.4GHz的遙控器具有自動跳頻的功能，也就是說只要你之前在家先對過頻率之後，就不用擔心和別人頻道相同，他利用展頻的方式將訊號分布在不同的頻率上傳輸，因此不會因為一個頻率受到干擾而訊號整個錯亂，因此不用像以往的AM和FM為了避免雜訊而提高功率，2.4GHz其實是相當省電的。

![http://3.bp.blogspot.com/-VNC1kzmgh9Q/UPek0TbvB1I/AAAAAAAAAms/euRo0_Qygds/s1600/2013-01-13+21.20.16.jpg](http://3.bp.blogspot.com/-VNC1kzmgh9Q/UPek0TbvB1I/AAAAAAAAAms/euRo0_Qygds/s1600/2013-01-13+21.20.16.jpg)

大致上就像是這樣接起來就可以用了~~~哪條線接哪個channel要仔細看過說明書才知道。~~

![http://1.bp.blogspot.com/-WdJpoXDWvVM/UPekxo9V4sI/AAAAAAAAAmA/sPkN_oqZLmM/s1600/2013-01-10+19.36.29.jpg](http://1.bp.blogspot.com/-WdJpoXDWvVM/UPekxo9V4sI/AAAAAAAAAmA/sPkN_oqZLmM/s1600/2013-01-10+19.36.29.jpg)
和腳進行連接，並且用飛機本身的電源去去提供給Arduino。
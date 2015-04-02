![http://3.bp.blogspot.com/-ltTiVbq7S4s/UO5afWffvAI/AAAAAAAAAaA/aoMNZYjv3wo/s1600/2013-01-10+13.58.17.jpg](http://3.bp.blogspot.com/-ltTiVbq7S4s/UO5afWffvAI/AAAAAAAAAaA/aoMNZYjv3wo/s1600/2013-01-10+13.58.17.jpg)

![http://3.bp.blogspot.com/-bX4hQw5p0_o/UO5bGXH8aZI/AAAAAAAAAaY/1yH0qJFguRI/s1600/2013-01-10+14.08.47.jpg](http://3.bp.blogspot.com/-bX4hQw5p0_o/UO5bGXH8aZI/AAAAAAAAAaY/1yH0qJFguRI/s1600/2013-01-10+14.08.47.jpg)

> 為了讓蜘蛛也可以利用遙控器來控制，因此我打算利用自己DIY的Arduino來讀取RC接收器的數值，RC接收器屆時讀取到的數值應該是PWM的訊號(這點還沒有很確認，不過對於接下來的使用不影響。)


自製的Arduino的接腳圖如下

![http://2.bp.blogspot.com/-2kVU4gDtppY/UO5adk88q1I/AAAAAAAAAZU/GkUozjyGsQU/s1600/2013-01-10+13.55.03.jpg](http://2.bp.blogspot.com/-2kVU4gDtppY/UO5adk88q1I/AAAAAAAAAZU/GkUozjyGsQU/s1600/2013-01-10+13.55.03.jpg)


> 左邊的是電源模組，提供5V的電壓，右邊則是RS232模組，用來連接電腦的，上方的一條藍線+五條黃色線是RC接收機的訊號線，藍線部分則沒有接任何東西，因為我只有五個頻道。

那五條黃色線分別對應到UNO數位腳的9 10 11 12 13，在下列的程式碼利用

pulseIn(pin, HIGH)

這行來進行讀取PWM訊號HIGH的時間長度。

void setup() {
> pinMode(9, INPUT);

> pinMode(10, INPUT);

> pinMode(11, INPUT);

> pinMode(12, INPUT);

> pinMode(13, INPUT);

> Serial.begin(9600);

}

void loop() {
> int value1 = pulseIn(9, HIGH);

> int value2 = pulseIn(10, HIGH);

> int value3 = pulseIn(11, HIGH);

> int value4 = pulseIn(12, HIGH);

> int value5 = pulseIn(13, HIGH);

> value1 = value1/10 - 149;

> value2 = value2/10 - 149;

> value3 = value3/10 - 149;

> value4 = value4/10 - 149;

> value5 = value5/10 - 149;

> Serial.print(value1);

> Serial.print("   ");

> Serial.print(value2);

> Serial.print("   ");

> Serial.print(value3);

> Serial.print("   ");

> Serial.print(value4);

> Serial.print("   ");

> Serial.print(value5);

> Serial.println("   ");

> delay(25);

}

我的CH3目前顯示-41，表示搖桿是拉到底的狀態，如果往上漸漸調升，則數字會越來越大；CH5是gyro調整用的，因此只有0和1，當我撥至0的時候會顯示-52(負數)左右，當我撥至1的時候會顯示52(正數)。


![http://4.bp.blogspot.com/-XA0cbPmjfMc/UO5e_Foo9EI/AAAAAAAAAbk/gDtY-Df46Is/s400/2013-01-10+14.25.31.jpg](http://4.bp.blogspot.com/-XA0cbPmjfMc/UO5e_Foo9EI/AAAAAAAAAbk/gDtY-Df46Is/s400/2013-01-10+14.25.31.jpg)

CH3 搖桿 表示油門

![http://1.bp.blogspot.com/-pmhB0be3nAo/UO5e_JSt9yI/AAAAAAAAAbo/16rUxo2a1ko/s1600/2013-01-10+14.25.25.jpg](http://1.bp.blogspot.com/-pmhB0be3nAo/UO5e_JSt9yI/AAAAAAAAAbo/16rUxo2a1ko/s1600/2013-01-10+14.25.25.jpg)

CH5 Gyro 調整鈕

![http://4.bp.blogspot.com/-_YdZbNIdzPw/UO5d2HlVWAI/AAAAAAAAAbM/Y0naMsGbDXA/s1600/2013-01-10_142033.jpg](http://4.bp.blogspot.com/-_YdZbNIdzPw/UO5d2HlVWAI/AAAAAAAAAbM/Y0naMsGbDXA/s1600/2013-01-10_142033.jpg)

CH3 搖桿撥到最低的狀態
CH5 按鈕調整至 0 的狀態

![http://3.bp.blogspot.com/-tjMgHrBe71E/UO5d2LQtbKI/AAAAAAAAAbQ/OCDFdvCn_00/s1600/2013-01-10_142009.jpg](http://3.bp.blogspot.com/-tjMgHrBe71E/UO5d2LQtbKI/AAAAAAAAAbQ/OCDFdvCn_00/s1600/2013-01-10_142009.jpg)

CH3 搖桿撥到最高的狀態
CH5 按鈕調整至 1 的狀態
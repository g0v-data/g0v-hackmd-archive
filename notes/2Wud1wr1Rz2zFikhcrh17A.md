WS2812 RGB燈(文章轉載):

 


# 一、簡介
WS2812只需要一條訊號線就能控制燈的多種顏色的變化，多個燈可以級聯，在**30hz**的刷新頻率下一個信號線能夠控製**至多500個LED**。
![image](https://hackmd.io/_uploads/B1-NYi1ca.png)


# 二、原理
WS2812B是一個集控制電路與發光電路於一體的智慧外控LED光源。其外型與一個5050LED燈珠相同，**每個元件即為一個像素點**。像素點內部包含了智慧數位介面資料鎖存訊號整形放大驅動電路，也包含**高精度的內部振盪器和可程式定電流控制部分**，有效確保了**像素點光的色彩高度一致**。d


# 三、硬體介紹
1.內建訊號整形電路，任何一個像素點收到**訊號後經過波形整形再輸出**，確保線路波形畸變不會累積。
2.**內建上電重設與掉電重設電路**
3.每個像素點的三基色顏色可實現**256級亮度顯示**，完成16777216中顏色的全真彩顯示，掃描頻率不低於400hz/s
4.串行級聯接口，能透過**一條訊號線完成資料的接收與接碼**。
5.**資料發送速度可達800kbps**（相當於1.25us傳輸一位元資料）

# 四、通訊協定
數據協定採用**單線歸零碼**的通訊方式，像素點在上電重設以後，DIN端接受從控制器傳輸過來的數據，首先送過來的24bit數據被第一個像素點提取後，送到像素點內部的資料鎖存器，剩餘的資料經過內部整形處理電路整形放大後透過DO埠開始轉送輸出給下一個級聯的像素點，每經過一個像素點的傳輸，訊號減少24bit。像素點採用自動整形轉送技術，使得此像素點的級聯個數不受訊號傳送的限制，僅受限於訊號傳輸速度要求。

資料碼的邏輯實作：
![image](https://hackmd.io/_uploads/BJb_Yik9a.png)
![image](https://hackmd.io/_uploads/rJftFi19p.png)
![image](https://hackmd.io/_uploads/rkIqFo15a.png)
![image](https://hackmd.io/_uploads/r1ziFjJqT.png)



文件部分請參考這位作者：
https://blog.csdn.net/tangxing1212/article/details/42964417

# 五、程序
調試延遲的時候可以用小馬哥視訊的方法
這裡給出連結。
https://www.bilibili.com/video/BV1Qs41137dk/?spm_id_from=333.788.videocard.0



Ws2812.h
```
#ifndef WS2812
#define WS2812

#define RGB_Port_RCC RCC_APB2Periph_GPIOB //RGB时钟
#define RGB_PIN GPIO_Pin_9 //RGB引脚
#define RGB_PORT GPIOB //RGB端口

#define RGBLED PBout(9)  //RGB灯

// 发送0x000000是关闭灯

void RGB_Init(void); // RGB初始化IO管脚
void RGB_ColorSet(uchar red,uchar green,uchar blue); // 设置一个灯的颜色
void RGB_RandomColor(void); // 产生随机数颜色
void RGB_RandomColor4(void); // 4个灯产生随机的颜色
#endif


Ws2812.c

#include "All.h"

// RGBLED 管脚初始化
void RGB_Init(void)
{
  GPIO_InitTypeDef GPIO_InitStructure;
	
	RCC_APB2PeriphClockCmd(RGB_Port_RCC,ENABLE);//系统时钟使能
	
	GPIO_InitStructure.GPIO_Pin = RGB_PIN; //定义管脚
	GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;//管脚输出模式
	GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;//管脚的速度
	GPIO_Init(RGB_PORT,&GPIO_InitStructure); //初始化端口


}

// 信号0 300ns高电平  900ns低电平
void RGB_Write0(void)
{
	uchar cnt1=1,cnt2 = 5;
  RGBLED = 1;   // 高电平
	while(cnt1--)  // 300ns
		__nop();
	
	RGBLED = 0;
	while(cnt2--)  // 900ns
		__nop();
}

// 信号1  600ns高电平  600ns低电平
void RGB_Write1(void)
{
	uchar cnt1=3,cnt2 = 3;
  RGBLED = 1;   // 高电平
	while(cnt1--)  // 600ns
		__nop();
	
	RGBLED = 0;
	while(cnt2--)  // 600ns
		__nop();	
}
// 复位   80us低电平
void RGB_LEDReset()
{
	RGBLED = 0;
	delay_us(80);
}


// RGB写一个字节
void RGB_WriteByte(uchar dat)
{
  uchar i;
	for(i= 0;i<8;i++)
	{
		dat <<= i;
	  if(dat & 0x80) // 判断最高位
		{
		   RGB_Write1(); // 写1
		}
		else
		{
		   RGB_Write0(); // 写0
		}
	}
}

// 设置一个灯的颜色
void RGB_ColorSet(uchar red,uchar green,uchar blue)
{
	// 灯的实际写入颜色是GRB
	RGB_WriteByte(green);  // 写入绿色
	RGB_WriteByte(red); // 写入红色
	RGB_WriteByte(blue); // 写入蓝色
}


// 产生一个随机的颜色
void RGB_RandomColor(void)
{
   uchar red,green,blue; 
	// srand((int)time(0)); // 设置随机种子
	 red = rand() % 255; //产生随机数在一个字节的范围内
	 green = rand() % 255;
	 blue = rand() % 255;
	 RGB_ColorSet(red,green,blue); // 合成颜色
}

/* 4个灯各自产生随机的颜色*/
void RGB_RandomColor4(void)
{
  	RGB_RandomColor();   // 产生随机颜色
		RGB_RandomColor(); 
		RGB_RandomColor(); 
		RGB_RandomColor(); 
}
————————————————
```

                            版权声明：本文为博主原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接和本声明。
                        
原文链接：https://blog.csdn.net/lengyuefeng212/article/details/109706246

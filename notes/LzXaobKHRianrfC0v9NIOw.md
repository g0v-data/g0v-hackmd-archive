# CODE


>電腦不難
>http://it-easy.tw/category/c-cpp/
---
>lcd程式
>https://download.mikroe.com/documents/compilers/mikroc/pic/help/lcd_library.htm
>
---
>delay
>https://www.itread01.com/content/1547171469.html
>
---
>sizeof為C語言的特殊運算符號之一，用來取得變數的位元組大小。
>http://it-easy.tw/c-sizeof/
>
---
>與extern對應的關鍵字是static，被它修飾的全域變數和函數只能在本模組中使用。
>https://b8807053.pixnet.net/blog/post/3612202
>
---
>HAL_Init();    HAL_OK  
>https://www.twblogs.net/a/5b8567c02b71775d1cd2e29c
>
---
>GPIO_InitTypeDef
>GPIO_InitStructure.Pin，
>GPIO_InitStructure.Mode，
>GPIO_InitStructure.Speed
> GPIO_InitStructure.Pull
> 
> 解釋
>![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ea7dbf08f89fa4a88857bcd80e5a4012.png)
>
---
>static void GPIO_Write (GPIO_TypeDef* GPIOx, uint16_t PortVal, uint16_t Mask)
{
    GPIOx->ODR = (GPIOx->ODR & (~Mask)) | (PortVal & Mask);
}
>GPIO_Write
>將數據寫入指定的GPIO數據端口。
>GPIOx
>-GPIOx：其中x可以是（A..G）選擇GPIO外設。
>PortVal
>指定要寫入端口輸出數據寄存器的值。
>Mask
>指定要寫入的端口位
>
---

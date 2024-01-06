# 工海專論--自走船程式
```c=
void HAL_TIM_IC_CaptureCallback(TIM_HandleTypeDef* htim){

 if(htim->Instance==TIM2){
   if(HAL_GPIO_ReadPin(GPIOA,GPIO_PIN_0)==1){
    __HAL_TIM_SET_COUNTER(&htim2,0);
   }else{
    cnt=__HAL_TIM_GET_COUNTER(&htim2);
    left=cnt/(double)58;
    integer=(int)left;
    point=(int)((left-integer)*100);
    char tosend[20]={0};
//    sprintf(tosend,"%d.%02d\r\n",integer,point);
//    HAL_UART_Transmit(&huart2,"1:",2,0xFFFF);
//    HAL_UART_Transmit(&huart2,tosend,sizeof(tosend),0xffff);
   }
  }

  if(htim->Instance==TIM3){
    if(HAL_GPIO_ReadPin(GPIOA,GPIO_PIN_4)==1){
     __HAL_TIM_SET_COUNTER(&htim3,0);
    }else{
     cnt1=__HAL_TIM_GET_COUNTER(&htim3);
     center=cnt1/(double)58;
     integer1=(int)center;
     point1=(int)((center-integer1)*100);
     char tosend1[20]={0};
     sprintf(tosend1,"%d.%02d\r\n",integer1,point1);
     HAL_UART_Transmit(&huart2,"2:",2,0xFFFF);
     HAL_UART_Transmit(&huart2,tosend1,sizeof(tosend1),0xffff);
    }
   }

  if(htim->Instance==TIM15){
    if(HAL_GPIO_ReadPin(GPIOB,GPIO_PIN_15)==1){
     __HAL_TIM_SET_COUNTER(&htim15,0);
    }else{
     cnt2=__HAL_TIM_GET_COUNTER(&htim15);
     right=cnt2/(double)58;
     integer2=(int)right;
     point2=(int)((right-integer2)*100);
     char tosend2[20]={0};
//     sprintf(tosend2,"%d.%02d\r\n",integer2,point2);
//     HAL_UART_Transmit(&huart2,"3:",2,0xFFFF);
//     HAL_UART_Transmit(&huart2,tosend2,sizeof(tosend2),0xffff);
    }
   }

  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_1, GPIO_PIN_RESET);
  HAL_GPIO_WritePin(GPIOB, GPIO_PIN_0, GPIO_PIN_RESET);
  HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET);
  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_10, GPIO_PIN_RESET);
  

  if(right>50&&left>40&&(right+left)<220&& (right+left) > 140 && center<20 &&
  tmpcenter<20 && tmpcenter2<20){ //center may have to modified
     TIM8->CCR4=0;
     TIM8->CCR3=0;
     TIM4->CCR3=100;                 
     TIM4->CCR4=0;
     turnright=1;
     turnleft=0;
     delay=1;
     HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET);
//     HAL_UART_Transmit(&huart2,"mode1..\n",5,0xFFFF);

  }else if(left<100&&center<120&&right>80&&(left+right)>115){ 
     //center modified from 100=>120
     TIM8->CCR4=0;
     TIM8->CCR3=0;
     TIM4->CCR3=100;                
     TIM4->CCR4=0;
     turnright=1;
     turnleft=0;
     delay=1;
     HAL_GPIO_WritePin(GPIOA, GPIO_PIN_10, GPIO_PIN_SET);
//     HAL_UART_Transmit(&huart2,"mode2..\n",5,0xFFFF);
   
   }else{
      if (center < 15 && delay == 0){
          TIM8->CCR4=0;
          TIM8->CCR3=0;
          TIM4->CCR3=0;
          TIM4->CCR4=100;
          HAL_GPIO_WritePin(GPIOA, GPIO_PIN_1, GPIO_PIN_SET);
          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_0, GPIO_PIN_SET);
          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET);
          HAL_GPIO_WritePin(GPIOA, GPIO_PIN_10, GPIO_PIN_SET);
      }
      else if(center<50 && right+left>60 && tmpcenter<50 && tmpcenter2<50){  
          delay = 0;
          if((left+50>right)&&right<80){  
          //左邊距離大於右邊距離，且右邊小於40cm，要左轉，右邊馬達開大
              TIM8->CCR4=90;                
              TIM8->CCR3=0;
              TIM4->CCR3=0;
              TIM4->CCR4=0;
              turnleft=1;
              turnright=0;
//            HAL_UART_Transmit(&huart2,"mode3..\n",5,0xFFFF);
            HAL_GPIO_WritePin(GPIOB, GPIO_PIN_0, GPIO_PIN_SET);
           }
           else if((right>left)&&left<40){  
           //右邊距離大於左邊距離，且左邊小於40cm，要右轉，左邊馬達開大
              TIM8->CCR4=0;
              TIM8->CCR3=0;
              TIM4->CCR3=70;                 
              TIM4->CCR4=0;
              turnright=1;
              turnleft=0;
           }
      }
      else{
          turnleft=0;
          turnright=0;
          delay=1;
//        HAL_UART_Transmit(&huart2,"mode4..\n",5,0xFFFF);

          HAL_GPIO_WritePin(GPIOA, GPIO_PIN_1, GPIO_PIN_SET);//1
          if(left-right>10&&(left+right)<60){
               TIM8->CCR4=70;
               TIM8->CCR3=0;
               TIM4->CCR3=70;
               TIM4->CCR4=0;
          }else if(right-left>20&&(left+right)<60){
               TIM8->CCR4=70;
               TIM8->CCR3=0;
               TIM4->CCR3=80;
               TIM4->CCR4=0;
          }else{
               TIM8->CCR4=80;
               TIM8->CCR3=0;
               TIM4->CCR3=80;
               TIM4->CCR4=0;
           }
         }
  }
     tmpcenter2=tmpcenter;     //tmpcenter2為前前次center值
     tmpcenter=center;         //tmpcenter為前次center值
}


while (1)
  {
    /* USER CODE END WHILE */
     TIM8->CCR4=0;
     TIM8->CCR3=0;
     TIM4->CCR3=0;                 
     TIM4->CCR4=0;

     //HAL_UART_Transmit(&huart2,"delay1\n",5,0xFFFF);
     HAL_Delay(135);
     /* USER CODE BEGIN 3 */
  }
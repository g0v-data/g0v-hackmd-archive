hallsensor 
#define PPR 6 // 每转的脉冲数，例如 3 个霍尔传感器和 2 对极

uint32_t Get_Period(void) {
    // 获取当前捕获值，这里假设已经用定时器捕获了霍尔传感器信号
    uint32_t ccr1 = __HAL_TIM_GET_COMPARE(&htim, TIM_CHANNEL_1);
    uint32_t ccr2 = __HAL_TIM_GET_COMPARE(&htim, TIM_CHANNEL_2);

    // 计算两个捕获值之间的周期
    return ccr2 - ccr1;
}

uint32_t Calculate_RPM(void) {
    uint32_t period = Get_Period();

    // 如果周期为 0，返回 0 转速，避免除以 0 错误
    if (period == 0) return 0;

    // 使用定时器的时钟频率计算频率
    uint32_t frequency = HAL_RCC_GetPCLK1Freq() / period;

    // 计算 RPM
    uint32_t rpm = (frequency * 60) / PPR;

    return rpm;
}

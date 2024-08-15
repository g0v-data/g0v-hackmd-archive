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
注意事项
PPR 确定：

PPR 必须根据你所使用的电机和霍尔传感器的配置来确定。对于一个有 3 个霍尔传感器和 2 对极的电机，通常 PPR 为 6。
计时器设置：

确保定时器的时钟频率足够高，以提供准确的周期测量。通常，预分频器和计数器的设置需要根据目标转速和霍尔传感器信号频率进行调整。
噪声处理：

在实际应用中，霍尔传感器信号可能会受到噪声影响，因此你可能需要增加滤波或对信号进行去抖动处理，以提高测量的准确性。
通过这些步骤，你可以精确地计算电机的转速，从而用于电机控制或监控应用。
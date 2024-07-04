7767517
451 501
Input                    images                   0 1 images
Convolution              /backbone/features.0/features.0.0/Conv 1 1 images /backbone/features.0/features.0.0/Conv_output_0 0=16 1=3 3=2 4=1 5=1 6=432
HardSwish                /backbone/features.0/features.0.2/Mul 1 1 /backbone/features.0/features.0.0/Conv_output_0 /backbone/features.0/features.0.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.1/conv/conv.0/Conv 1 1 /backbone/features.0/features.0.2/Mul_output_0 /backbone/features.1/conv/conv.0/Conv_output_0 0=16 1=5 4=2 5=1 6=400 7=16
HardSwish                /backbone/features.1/conv/conv.2/Mul 1 1 /backbone/features.1/conv/conv.0/Conv_output_0 /backbone/features.1/conv/conv.2/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.1/conv/conv.3/Conv 1 1 /backbone/features.1/conv/conv.2/Mul_output_0 /backbone/features.1/conv/conv.3/Conv_output_0 0=8 1=1 5=1 6=128
Convolution              /backbone/features.2/conv/conv.0/Conv 1 1 /backbone/features.1/conv/conv.3/Conv_output_0 /backbone/features.2/conv/conv.0/Conv_output_0 0=48 1=1 5=1 6=384
HardSwish                /backbone/features.2/conv/conv.2/Mul 1 1 /backbone/features.2/conv/conv.0/Conv_output_0 /backbone/features.2/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.2/conv/conv.3/Conv 1 1 /backbone/features.2/conv/conv.2/Mul_output_0 /backbone/features.2/conv/conv.3/Conv_output_0 0=48 1=5 3=2 4=2 5=1 6=1200 7=48
HardSwish                /backbone/features.2/conv/conv.5/Mul 1 1 /backbone/features.2/conv/conv.3/Conv_output_0 /backbone/features.2/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.2/conv/conv.6/Conv 1 1 /backbone/features.2/conv/conv.5/Mul_output_0 /backbone/features.2/conv/conv.6/Conv_output_0 0=16 1=1 5=1 6=768
Split                    split_1                  1 2 /backbone/features.2/conv/conv.6/Conv_output_0 /backbone/features.2/conv/conv.6/Conv_output_0_splitncnn_0 /backbone/features.2/conv/conv.6/Conv_output_0_splitncnn_1
Convolution              /backbone/features.3/conv/conv.0/Conv 1 1 /backbone/features.2/conv/conv.6/Conv_output_0_splitncnn_1 /backbone/features.3/conv/conv.0/Conv_output_0 0=96 1=1 5=1 6=1536
HardSwish                /backbone/features.3/conv/conv.2/Mul 1 1 /backbone/features.3/conv/conv.0/Conv_output_0 /backbone/features.3/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.3/conv/conv.3/Conv 1 1 /backbone/features.3/conv/conv.2/Mul_output_0 /backbone/features.3/conv/conv.3/Conv_output_0 0=96 1=5 4=2 5=1 6=2400 7=96
HardSwish                /backbone/features.3/conv/conv.5/Mul 1 1 /backbone/features.3/conv/conv.3/Conv_output_0 /backbone/features.3/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.3/conv/conv.6/Conv 1 1 /backbone/features.3/conv/conv.5/Mul_output_0 /backbone/features.3/conv/conv.6/Conv_output_0 0=16 1=1 5=1 6=1536
BinaryOp                 add_0                    2 1 /backbone/features.2/conv/conv.6/Conv_output_0_splitncnn_0 /backbone/features.3/conv/conv.6/Conv_output_0 /backbone/features.3/Add_output_0
Convolution              /backbone/features.4/conv/conv.0/Conv 1 1 /backbone/features.3/Add_output_0 /backbone/features.4/conv/conv.0/Conv_output_0 0=96 1=1 5=1 6=1536
HardSwish                /backbone/features.4/conv/conv.2/Mul 1 1 /backbone/features.4/conv/conv.0/Conv_output_0 /backbone/features.4/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.4/conv/conv.3/Conv 1 1 /backbone/features.4/conv/conv.2/Mul_output_0 /backbone/features.4/conv/conv.3/Conv_output_0 0=96 1=5 3=2 4=2 5=1 6=2400 7=96
HardSwish                /backbone/features.4/conv/conv.5/Mul 1 1 /backbone/features.4/conv/conv.3/Conv_output_0 /backbone/features.4/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.4/conv/conv.6/Conv 1 1 /backbone/features.4/conv/conv.5/Mul_output_0 /backbone/features.4/conv/conv.6/Conv_output_0 0=16 1=1 5=1 6=1536
Split                    split_2                  1 2 /backbone/features.4/conv/conv.6/Conv_output_0 /backbone/features.4/conv/conv.6/Conv_output_0_splitncnn_0 /backbone/features.4/conv/conv.6/Conv_output_0_splitncnn_1
Convolution              /backbone/features.5/conv/conv.0/Conv 1 1 /backbone/features.4/conv/conv.6/Conv_output_0_splitncnn_1 /backbone/features.5/conv/conv.0/Conv_output_0 0=96 1=1 5=1 6=1536
HardSwish                /backbone/features.5/conv/conv.2/Mul 1 1 /backbone/features.5/conv/conv.0/Conv_output_0 /backbone/features.5/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.5/conv/conv.3/Conv 1 1 /backbone/features.5/conv/conv.2/Mul_output_0 /backbone/features.5/conv/conv.3/Conv_output_0 0=96 1=5 4=2 5=1 6=2400 7=96
HardSwish                /backbone/features.5/conv/conv.5/Mul 1 1 /backbone/features.5/conv/conv.3/Conv_output_0 /backbone/features.5/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.5/conv/conv.6/Conv 1 1 /backbone/features.5/conv/conv.5/Mul_output_0 /backbone/features.5/conv/conv.6/Conv_output_0 0=16 1=1 5=1 6=1536
BinaryOp                 add_1                    2 1 /backbone/features.4/conv/conv.6/Conv_output_0_splitncnn_0 /backbone/features.5/conv/conv.6/Conv_output_0 /backbone/features.5/Add_output_0
Split                    split_3                  1 2 /backbone/features.5/Add_output_0 /backbone/features.5/Add_output_0_splitncnn_0 /backbone/features.5/Add_output_0_splitncnn_1
Convolution              /backbone/features.6/conv/conv.0/Conv 1 1 /backbone/features.5/Add_output_0_splitncnn_1 /backbone/features.6/conv/conv.0/Conv_output_0 0=96 1=1 5=1 6=1536
HardSwish                /backbone/features.6/conv/conv.2/Mul 1 1 /backbone/features.6/conv/conv.0/Conv_output_0 /backbone/features.6/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.6/conv/conv.3/Conv 1 1 /backbone/features.6/conv/conv.2/Mul_output_0 /backbone/features.6/conv/conv.3/Conv_output_0 0=96 1=5 4=2 5=1 6=2400 7=96
HardSwish                /backbone/features.6/conv/conv.5/Mul 1 1 /backbone/features.6/conv/conv.3/Conv_output_0 /backbone/features.6/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.6/conv/conv.6/Conv 1 1 /backbone/features.6/conv/conv.5/Mul_output_0 /backbone/features.6/conv/conv.6/Conv_output_0 0=16 1=1 5=1 6=1536
BinaryOp                 add_2                    2 1 /backbone/features.5/Add_output_0_splitncnn_0 /backbone/features.6/conv/conv.6/Conv_output_0 /backbone/features.6/Add_output_0
Split                    split_4                  1 2 /backbone/features.6/Add_output_0 /backbone/features.6/Add_output_0_splitncnn_0 /backbone/features.6/Add_output_0_splitncnn_1
Convolution              /backbone/features.7/conv/conv.0/Conv 1 1 /backbone/features.6/Add_output_0_splitncnn_1 /backbone/features.7/conv/conv.0/Conv_output_0 0=96 1=1 5=1 6=1536
HardSwish                /backbone/features.7/conv/conv.2/Mul 1 1 /backbone/features.7/conv/conv.0/Conv_output_0 /backbone/features.7/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.7/conv/conv.3/Conv 1 1 /backbone/features.7/conv/conv.2/Mul_output_0 /backbone/features.7/conv/conv.3/Conv_output_0 0=96 1=5 3=2 4=2 5=1 6=2400 7=96
HardSwish                /backbone/features.7/conv/conv.5/Mul 1 1 /backbone/features.7/conv/conv.3/Conv_output_0 /backbone/features.7/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.7/conv/conv.6/Conv 1 1 /backbone/features.7/conv/conv.5/Mul_output_0 /backbone/features.7/conv/conv.6/Conv_output_0 0=32 1=1 5=1 6=3072
Split                    split_5                  1 2 /backbone/features.7/conv/conv.6/Conv_output_0 /backbone/features.7/conv/conv.6/Conv_output_0_splitncnn_0 /backbone/features.7/conv/conv.6/Conv_output_0_splitncnn_1
Convolution              /backbone/features.8/conv/conv.0/Conv 1 1 /backbone/features.7/conv/conv.6/Conv_output_0_splitncnn_1 /backbone/features.8/conv/conv.0/Conv_output_0 0=192 1=1 5=1 6=6144
HardSwish                /backbone/features.8/conv/conv.2/Mul 1 1 /backbone/features.8/conv/conv.0/Conv_output_0 /backbone/features.8/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.8/conv/conv.3/Conv 1 1 /backbone/features.8/conv/conv.2/Mul_output_0 /backbone/features.8/conv/conv.3/Conv_output_0 0=192 1=5 4=2 5=1 6=4800 7=192
HardSwish                /backbone/features.8/conv/conv.5/Mul 1 1 /backbone/features.8/conv/conv.3/Conv_output_0 /backbone/features.8/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.8/conv/conv.6/Conv 1 1 /backbone/features.8/conv/conv.5/Mul_output_0 /backbone/features.8/conv/conv.6/Conv_output_0 0=32 1=1 5=1 6=6144
BinaryOp                 add_3                    2 1 /backbone/features.7/conv/conv.6/Conv_output_0_splitncnn_0 /backbone/features.8/conv/conv.6/Conv_output_0 /backbone/features.8/Add_output_0
Split                    split_6                  1 2 /backbone/features.8/Add_output_0 /backbone/features.8/Add_output_0_splitncnn_0 /backbone/features.8/Add_output_0_splitncnn_1
Convolution              /backbone/features.9/conv/conv.0/Conv 1 1 /backbone/features.8/Add_output_0_splitncnn_1 /backbone/features.9/conv/conv.0/Conv_output_0 0=192 1=1 5=1 6=6144
HardSwish                /backbone/features.9/conv/conv.2/Mul 1 1 /backbone/features.9/conv/conv.0/Conv_output_0 /backbone/features.9/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.9/conv/conv.3/Conv 1 1 /backbone/features.9/conv/conv.2/Mul_output_0 /backbone/features.9/conv/conv.3/Conv_output_0 0=192 1=5 4=2 5=1 6=4800 7=192
HardSwish                /backbone/features.9/conv/conv.5/Mul 1 1 /backbone/features.9/conv/conv.3/Conv_output_0 /backbone/features.9/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.9/conv/conv.6/Conv 1 1 /backbone/features.9/conv/conv.5/Mul_output_0 /backbone/features.9/conv/conv.6/Conv_output_0 0=32 1=1 5=1 6=6144
BinaryOp                 add_4                    2 1 /backbone/features.8/Add_output_0_splitncnn_0 /backbone/features.9/conv/conv.6/Conv_output_0 /backbone/features.9/Add_output_0
Split                    split_7                  1 2 /backbone/features.9/Add_output_0 /backbone/features.9/Add_output_0_splitncnn_0 /backbone/features.9/Add_output_0_splitncnn_1
Convolution              /backbone/features.10/conv/conv.0/Conv 1 1 /backbone/features.9/Add_output_0_splitncnn_1 /backbone/features.10/conv/conv.0/Conv_output_0 0=192 1=1 5=1 6=6144
HardSwish                /backbone/features.10/conv/conv.2/Mul 1 1 /backbone/features.10/conv/conv.0/Conv_output_0 /backbone/features.10/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.10/conv/conv.3/Conv 1 1 /backbone/features.10/conv/conv.2/Mul_output_0 /backbone/features.10/conv/conv.3/Conv_output_0 0=192 1=5 4=2 5=1 6=4800 7=192
HardSwish                /backbone/features.10/conv/conv.5/Mul 1 1 /backbone/features.10/conv/conv.3/Conv_output_0 /backbone/features.10/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.10/conv/conv.6/Conv 1 1 /backbone/features.10/conv/conv.5/Mul_output_0 /backbone/features.10/conv/conv.6/Conv_output_0 0=32 1=1 5=1 6=6144
BinaryOp                 add_5                    2 1 /backbone/features.9/Add_output_0_splitncnn_0 /backbone/features.10/conv/conv.6/Conv_output_0 /backbone/features.10/Add_output_0
Convolution              /backbone/features.11/conv/conv.0/Conv 1 1 /backbone/features.10/Add_output_0 /backbone/features.11/conv/conv.0/Conv_output_0 0=192 1=1 5=1 6=6144
HardSwish                /backbone/features.11/conv/conv.2/Mul 1 1 /backbone/features.11/conv/conv.0/Conv_output_0 /backbone/features.11/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.11/conv/conv.3/Conv 1 1 /backbone/features.11/conv/conv.2/Mul_output_0 /backbone/features.11/conv/conv.3/Conv_output_0 0=192 1=5 4=2 5=1 6=4800 7=192
HardSwish                /backbone/features.11/conv/conv.5/Mul 1 1 /backbone/features.11/conv/conv.3/Conv_output_0 /backbone/features.11/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.11/conv/conv.6/Conv 1 1 /backbone/features.11/conv/conv.5/Mul_output_0 /backbone/features.11/conv/conv.6/Conv_output_0 0=48 1=1 5=1 6=9216
Split                    split_8                  1 2 /backbone/features.11/conv/conv.6/Conv_output_0 /backbone/features.11/conv/conv.6/Conv_output_0_splitncnn_0 /backbone/features.11/conv/conv.6/Conv_output_0_splitncnn_1
Convolution              /backbone/features.12/conv/conv.0/Conv 1 1 /backbone/features.11/conv/conv.6/Conv_output_0_splitncnn_1 /backbone/features.12/conv/conv.0/Conv_output_0 0=288 1=1 5=1 6=13824
HardSwish                /backbone/features.12/conv/conv.2/Mul 1 1 /backbone/features.12/conv/conv.0/Conv_output_0 /backbone/features.12/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.12/conv/conv.3/Conv 1 1 /backbone/features.12/conv/conv.2/Mul_output_0 /backbone/features.12/conv/conv.3/Conv_output_0 0=288 1=5 4=2 5=1 6=7200 7=288
HardSwish                /backbone/features.12/conv/conv.5/Mul 1 1 /backbone/features.12/conv/conv.3/Conv_output_0 /backbone/features.12/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.12/conv/conv.6/Conv 1 1 /backbone/features.12/conv/conv.5/Mul_output_0 /backbone/features.12/conv/conv.6/Conv_output_0 0=48 1=1 5=1 6=13824
BinaryOp                 add_6                    2 1 /backbone/features.11/conv/conv.6/Conv_output_0_splitncnn_0 /backbone/features.12/conv/conv.6/Conv_output_0 /backbone/features.12/Add_output_0
Split                    split_9                  1 2 /backbone/features.12/Add_output_0 /backbone/features.12/Add_output_0_splitncnn_0 /backbone/features.12/Add_output_0_splitncnn_1
Convolution              /backbone/features.13/conv/conv.0/Conv 1 1 /backbone/features.12/Add_output_0_splitncnn_1 /backbone/features.13/conv/conv.0/Conv_output_0 0=288 1=1 5=1 6=13824
HardSwish                /backbone/features.13/conv/conv.2/Mul 1 1 /backbone/features.13/conv/conv.0/Conv_output_0 /backbone/features.13/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.13/conv/conv.3/Conv 1 1 /backbone/features.13/conv/conv.2/Mul_output_0 /backbone/features.13/conv/conv.3/Conv_output_0 0=288 1=5 4=2 5=1 6=7200 7=288
HardSwish                /backbone/features.13/conv/conv.5/Mul 1 1 /backbone/features.13/conv/conv.3/Conv_output_0 /backbone/features.13/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.13/conv/conv.6/Conv 1 1 /backbone/features.13/conv/conv.5/Mul_output_0 /backbone/features.13/conv/conv.6/Conv_output_0 0=48 1=1 5=1 6=13824
BinaryOp                 add_7                    2 1 /backbone/features.12/Add_output_0_splitncnn_0 /backbone/features.13/conv/conv.6/Conv_output_0 /backbone/features.13/Add_output_0
Split                    split_10                 1 2 /backbone/features.13/Add_output_0 /backbone/features.13/Add_output_0_splitncnn_0 /backbone/features.13/Add_output_0_splitncnn_1
Convolution              /backbone/features.14/conv/conv.0/Conv 1 1 /backbone/features.13/Add_output_0_splitncnn_1 /backbone/features.14/conv/conv.0/Conv_output_0 0=288 1=1 5=1 6=13824
HardSwish                /backbone/features.14/conv/conv.2/Mul 1 1 /backbone/features.14/conv/conv.0/Conv_output_0 /backbone/features.14/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.14/conv/conv.3/Conv 1 1 /backbone/features.14/conv/conv.2/Mul_output_0 /backbone/features.14/conv/conv.3/Conv_output_0 0=288 1=5 3=2 4=2 5=1 6=7200 7=288
HardSwish                /backbone/features.14/conv/conv.5/Mul 1 1 /backbone/features.14/conv/conv.3/Conv_output_0 /backbone/features.14/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.14/conv/conv.6/Conv 1 1 /backbone/features.14/conv/conv.5/Mul_output_0 /backbone/features.14/conv/conv.6/Conv_output_0 0=80 1=1 5=1 6=23040
Split                    split_11                 1 2 /backbone/features.14/conv/conv.6/Conv_output_0 /backbone/features.14/conv/conv.6/Conv_output_0_splitncnn_0 /backbone/features.14/conv/conv.6/Conv_output_0_splitncnn_1
Convolution              /backbone/features.15/conv/conv.0/Conv 1 1 /backbone/features.14/conv/conv.6/Conv_output_0_splitncnn_1 /backbone/features.15/conv/conv.0/Conv_output_0 0=480 1=1 5=1 6=38400
HardSwish                /backbone/features.15/conv/conv.2/Mul 1 1 /backbone/features.15/conv/conv.0/Conv_output_0 /backbone/features.15/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.15/conv/conv.3/Conv 1 1 /backbone/features.15/conv/conv.2/Mul_output_0 /backbone/features.15/conv/conv.3/Conv_output_0 0=480 1=5 4=2 5=1 6=12000 7=480
HardSwish                /backbone/features.15/conv/conv.5/Mul 1 1 /backbone/features.15/conv/conv.3/Conv_output_0 /backbone/features.15/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.15/conv/conv.6/Conv 1 1 /backbone/features.15/conv/conv.5/Mul_output_0 /backbone/features.15/conv/conv.6/Conv_output_0 0=80 1=1 5=1 6=38400
BinaryOp                 add_8                    2 1 /backbone/features.14/conv/conv.6/Conv_output_0_splitncnn_0 /backbone/features.15/conv/conv.6/Conv_output_0 /backbone/features.15/Add_output_0
Split                    split_12                 1 2 /backbone/features.15/Add_output_0 /backbone/features.15/Add_output_0_splitncnn_0 /backbone/features.15/Add_output_0_splitncnn_1
Convolution              /backbone/features.16/conv/conv.0/Conv 1 1 /backbone/features.15/Add_output_0_splitncnn_1 /backbone/features.16/conv/conv.0/Conv_output_0 0=480 1=1 5=1 6=38400
HardSwish                /backbone/features.16/conv/conv.2/Mul 1 1 /backbone/features.16/conv/conv.0/Conv_output_0 /backbone/features.16/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.16/conv/conv.3/Conv 1 1 /backbone/features.16/conv/conv.2/Mul_output_0 /backbone/features.16/conv/conv.3/Conv_output_0 0=480 1=5 4=2 5=1 6=12000 7=480
HardSwish                /backbone/features.16/conv/conv.5/Mul 1 1 /backbone/features.16/conv/conv.3/Conv_output_0 /backbone/features.16/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.16/conv/conv.6/Conv 1 1 /backbone/features.16/conv/conv.5/Mul_output_0 /backbone/features.16/conv/conv.6/Conv_output_0 0=80 1=1 5=1 6=38400
BinaryOp                 add_9                    2 1 /backbone/features.15/Add_output_0_splitncnn_0 /backbone/features.16/conv/conv.6/Conv_output_0 /backbone/features.16/Add_output_0
Convolution              /backbone/features.17/conv/conv.0/Conv 1 1 /backbone/features.16/Add_output_0 /backbone/features.17/conv/conv.0/Conv_output_0 0=480 1=1 5=1 6=38400
HardSwish                /backbone/features.17/conv/conv.2/Mul 1 1 /backbone/features.17/conv/conv.0/Conv_output_0 /backbone/features.17/conv/conv.2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /backbone/features.17/conv/conv.3/Conv 1 1 /backbone/features.17/conv/conv.2/Mul_output_0 /backbone/features.17/conv/conv.3/Conv_output_0 0=480 1=5 4=2 5=1 6=12000 7=480
HardSwish                /backbone/features.17/conv/conv.5/Mul 1 1 /backbone/features.17/conv/conv.3/Conv_output_0 /backbone/features.17/conv/conv.5/Mul_output_0 0=1.666667e-01
Convolution              /backbone/features.17/conv/conv.6/Conv 1 1 /backbone/features.17/conv/conv.5/Mul_output_0 /backbone/features.17/conv/conv.6/Conv_output_0 0=160 1=1 5=1 6=76800
Convolution              /neck/reduce_layer0/block/conv/Conv 1 1 /backbone/features.17/conv/conv.6/Conv_output_0 /neck/reduce_layer0/block/conv/Conv_output_0 0=64 1=1 5=1 6=10240
HardSwish                /neck/reduce_layer0/block/act/Mul 1 1 /neck/reduce_layer0/block/conv/Conv_output_0 /neck/reduce_layer0/block/act/Mul_output_0 0=1.666667e-01
Split                    split_13                 1 3 /neck/reduce_layer0/block/act/Mul_output_0 /neck/reduce_layer0/block/act/Mul_output_0_splitncnn_0 /neck/reduce_layer0/block/act/Mul_output_0_splitncnn_1 /neck/reduce_layer0/block/act/Mul_output_0_splitncnn_2
Convolution              /neck/reduce_layer1/block/conv/Conv 1 1 /backbone/features.13/Add_output_0_splitncnn_0 /neck/reduce_layer1/block/conv/Conv_output_0 0=64 1=1 5=1 6=3072
HardSwish                /neck/reduce_layer1/block/act/Mul 1 1 /neck/reduce_layer1/block/conv/Conv_output_0 /neck/reduce_layer1/block/act/Mul_output_0 0=1.666667e-01
Convolution              /neck/reduce_layer2/block/conv/Conv 1 1 /backbone/features.6/Add_output_0_splitncnn_0 /neck/reduce_layer2/block/conv/Conv_output_0 0=64 1=1 5=1 6=1024
HardSwish                /neck/reduce_layer2/block/act/Mul 1 1 /neck/reduce_layer2/block/conv/Conv_output_0 /neck/reduce_layer2/block/act/Mul_output_0 0=1.666667e-01
Interp                   interp_0                 1 1 /neck/reduce_layer0/block/act/Mul_output_0_splitncnn_2 /neck/upsample0/Resize_output_0 0=1 1=2.000000e+00 2=2.000000e+00
Concat                   /neck/Concat             2 1 /neck/upsample0/Resize_output_0 /neck/reduce_layer1/block/act/Mul_output_0 /neck/Concat_output_0
Split                    split_14                 1 2 /neck/Concat_output_0 /neck/Concat_output_0_splitncnn_0 /neck/Concat_output_0_splitncnn_1
Convolution              /neck/Csp_p4/conv_1/block/conv/Conv 1 1 /neck/Concat_output_0_splitncnn_1 /neck/Csp_p4/conv_1/block/conv/Conv_output_0 0=32 1=1 5=1 6=4096
HardSwish                /neck/Csp_p4/conv_1/block/act/Mul 1 1 /neck/Csp_p4/conv_1/block/conv/Conv_output_0 /neck/Csp_p4/conv_1/block/act/Mul_output_0 0=1.666667e-01
Convolution              /neck/Csp_p4/blocks/conv_1/block/conv/Conv 1 1 /neck/Csp_p4/conv_1/block/act/Mul_output_0 /neck/Csp_p4/blocks/conv_1/block/conv/Conv_output_0 0=32 1=1 5=1 6=1024
HardSwish                /neck/Csp_p4/blocks/conv_1/block/act/Mul 1 1 /neck/Csp_p4/blocks/conv_1/block/conv/Conv_output_0 /neck/Csp_p4/blocks/conv_1/block/act/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /neck/Csp_p4/blocks/conv_2/conv_dw_1/Conv 1 1 /neck/Csp_p4/blocks/conv_1/block/act/Mul_output_0 /neck/Csp_p4/blocks/conv_2/conv_dw_1/Conv_output_0 0=32 1=5 4=2 5=1 6=800 7=32
HardSwish                /neck/Csp_p4/blocks/conv_2/act_1/Mul 1 1 /neck/Csp_p4/blocks/conv_2/conv_dw_1/Conv_output_0 /neck/Csp_p4/blocks/conv_2/act_1/Mul_output_0 0=1.666667e-01
Convolution              /neck/Csp_p4/blocks/conv_2/conv_pw_1/Conv 1 1 /neck/Csp_p4/blocks/conv_2/act_1/Mul_output_0 /neck/Csp_p4/blocks/conv_2/conv_pw_1/Conv_output_0 0=32 1=1 5=1 6=1024
HardSwish                /neck/Csp_p4/blocks/conv_2/act_2/Mul 1 1 /neck/Csp_p4/blocks/conv_2/conv_pw_1/Conv_output_0 /neck/Csp_p4/blocks/conv_2/act_2/Mul_output_0 0=1.666667e-01
Convolution              /neck/Csp_p4/conv_2/block/conv/Conv 1 1 /neck/Concat_output_0_splitncnn_0 /neck/Csp_p4/conv_2/block/conv/Conv_output_0 0=32 1=1 5=1 6=4096
HardSwish                /neck/Csp_p4/conv_2/block/act/Mul 1 1 /neck/Csp_p4/conv_2/block/conv/Conv_output_0 /neck/Csp_p4/conv_2/block/act/Mul_output_0 0=1.666667e-01
Concat                   /neck/Csp_p4/Concat      2 1 /neck/Csp_p4/blocks/conv_2/act_2/Mul_output_0 /neck/Csp_p4/conv_2/block/act/Mul_output_0 /neck/Csp_p4/Concat_output_0
Convolution              /neck/Csp_p4/conv_3/block/conv/Conv 1 1 /neck/Csp_p4/Concat_output_0 /neck/Csp_p4/conv_3/block/conv/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /neck/Csp_p4/conv_3/block/act/Mul 1 1 /neck/Csp_p4/conv_3/block/conv/Conv_output_0 /neck/Csp_p4/conv_3/block/act/Mul_output_0 0=1.666667e-01
Split                    split_15                 1 2 /neck/Csp_p4/conv_3/block/act/Mul_output_0 /neck/Csp_p4/conv_3/block/act/Mul_output_0_splitncnn_0 /neck/Csp_p4/conv_3/block/act/Mul_output_0_splitncnn_1
Interp                   interp_1                 1 1 /neck/Csp_p4/conv_3/block/act/Mul_output_0_splitncnn_1 /neck/upsample1/Resize_output_0 0=1 1=2.000000e+00 2=2.000000e+00
Concat                   /neck/Concat_1           2 1 /neck/upsample1/Resize_output_0 /neck/reduce_layer2/block/act/Mul_output_0 /neck/Concat_1_output_0
Split                    split_16                 1 2 /neck/Concat_1_output_0 /neck/Concat_1_output_0_splitncnn_0 /neck/Concat_1_output_0_splitncnn_1
Convolution              /neck/Csp_p3/conv_1/block/conv/Conv 1 1 /neck/Concat_1_output_0_splitncnn_1 /neck/Csp_p3/conv_1/block/conv/Conv_output_0 0=32 1=1 5=1 6=4096
HardSwish                /neck/Csp_p3/conv_1/block/act/Mul 1 1 /neck/Csp_p3/conv_1/block/conv/Conv_output_0 /neck/Csp_p3/conv_1/block/act/Mul_output_0 0=1.666667e-01
Convolution              /neck/Csp_p3/blocks/conv_1/block/conv/Conv 1 1 /neck/Csp_p3/conv_1/block/act/Mul_output_0 /neck/Csp_p3/blocks/conv_1/block/conv/Conv_output_0 0=32 1=1 5=1 6=1024
HardSwish                /neck/Csp_p3/blocks/conv_1/block/act/Mul 1 1 /neck/Csp_p3/blocks/conv_1/block/conv/Conv_output_0 /neck/Csp_p3/blocks/conv_1/block/act/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /neck/Csp_p3/blocks/conv_2/conv_dw_1/Conv 1 1 /neck/Csp_p3/blocks/conv_1/block/act/Mul_output_0 /neck/Csp_p3/blocks/conv_2/conv_dw_1/Conv_output_0 0=32 1=5 4=2 5=1 6=800 7=32
HardSwish                /neck/Csp_p3/blocks/conv_2/act_1/Mul 1 1 /neck/Csp_p3/blocks/conv_2/conv_dw_1/Conv_output_0 /neck/Csp_p3/blocks/conv_2/act_1/Mul_output_0 0=1.666667e-01
Convolution              /neck/Csp_p3/blocks/conv_2/conv_pw_1/Conv 1 1 /neck/Csp_p3/blocks/conv_2/act_1/Mul_output_0 /neck/Csp_p3/blocks/conv_2/conv_pw_1/Conv_output_0 0=32 1=1 5=1 6=1024
HardSwish                /neck/Csp_p3/blocks/conv_2/act_2/Mul 1 1 /neck/Csp_p3/blocks/conv_2/conv_pw_1/Conv_output_0 /neck/Csp_p3/blocks/conv_2/act_2/Mul_output_0 0=1.666667e-01
Convolution              /neck/Csp_p3/conv_2/block/conv/Conv 1 1 /neck/Concat_1_output_0_splitncnn_0 /neck/Csp_p3/conv_2/block/conv/Conv_output_0 0=32 1=1 5=1 6=4096
HardSwish                /neck/Csp_p3/conv_2/block/act/Mul 1 1 /neck/Csp_p3/conv_2/block/conv/Conv_output_0 /neck/Csp_p3/conv_2/block/act/Mul_output_0 0=1.666667e-01
Concat                   /neck/Csp_p3/Concat      2 1 /neck/Csp_p3/blocks/conv_2/act_2/Mul_output_0 /neck/Csp_p3/conv_2/block/act/Mul_output_0 /neck/Csp_p3/Concat_output_0
Convolution              /neck/Csp_p3/conv_3/block/conv/Conv 1 1 /neck/Csp_p3/Concat_output_0 /neck/Csp_p3/conv_3/block/conv/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /neck/Csp_p3/conv_3/block/act/Mul 1 1 /neck/Csp_p3/conv_3/block/conv/Conv_output_0 /neck/Csp_p3/conv_3/block/act/Mul_output_0 0=1.666667e-01
Split                    split_17                 1 2 /neck/Csp_p3/conv_3/block/act/Mul_output_0 /neck/Csp_p3/conv_3/block/act/Mul_output_0_splitncnn_0 /neck/Csp_p3/conv_3/block/act/Mul_output_0_splitncnn_1
ConvolutionDepthWise     /neck/downsample2/conv_dw_1/Conv 1 1 /neck/Csp_p3/conv_3/block/act/Mul_output_0_splitncnn_1 /neck/downsample2/conv_dw_1/Conv_output_0 0=64 1=5 3=2 4=2 5=1 6=1600 7=64
HardSwish                /neck/downsample2/act_1/Mul 1 1 /neck/downsample2/conv_dw_1/Conv_output_0 /neck/downsample2/act_1/Mul_output_0 0=1.666667e-01
Convolution              /neck/downsample2/conv_pw_1/Conv 1 1 /neck/downsample2/act_1/Mul_output_0 /neck/downsample2/conv_pw_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /neck/downsample2/act_2/Mul 1 1 /neck/downsample2/conv_pw_1/Conv_output_0 /neck/downsample2/act_2/Mul_output_0 0=1.666667e-01
Concat                   /neck/Concat_2           2 1 /neck/downsample2/act_2/Mul_output_0 /neck/Csp_p4/conv_3/block/act/Mul_output_0_splitncnn_0 /neck/Concat_2_output_0
Split                    split_18                 1 2 /neck/Concat_2_output_0 /neck/Concat_2_output_0_splitncnn_0 /neck/Concat_2_output_0_splitncnn_1
Convolution              /neck/Csp_n3/conv_1/block/conv/Conv 1 1 /neck/Concat_2_output_0_splitncnn_1 /neck/Csp_n3/conv_1/block/conv/Conv_output_0 0=32 1=1 5=1 6=4096
HardSwish                /neck/Csp_n3/conv_1/block/act/Mul 1 1 /neck/Csp_n3/conv_1/block/conv/Conv_output_0 /neck/Csp_n3/conv_1/block/act/Mul_output_0 0=1.666667e-01
Convolution              /neck/Csp_n3/blocks/conv_1/block/conv/Conv 1 1 /neck/Csp_n3/conv_1/block/act/Mul_output_0 /neck/Csp_n3/blocks/conv_1/block/conv/Conv_output_0 0=32 1=1 5=1 6=1024
HardSwish                /neck/Csp_n3/blocks/conv_1/block/act/Mul 1 1 /neck/Csp_n3/blocks/conv_1/block/conv/Conv_output_0 /neck/Csp_n3/blocks/conv_1/block/act/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /neck/Csp_n3/blocks/conv_2/conv_dw_1/Conv 1 1 /neck/Csp_n3/blocks/conv_1/block/act/Mul_output_0 /neck/Csp_n3/blocks/conv_2/conv_dw_1/Conv_output_0 0=32 1=5 4=2 5=1 6=800 7=32
HardSwish                /neck/Csp_n3/blocks/conv_2/act_1/Mul 1 1 /neck/Csp_n3/blocks/conv_2/conv_dw_1/Conv_output_0 /neck/Csp_n3/blocks/conv_2/act_1/Mul_output_0 0=1.666667e-01
Convolution              /neck/Csp_n3/blocks/conv_2/conv_pw_1/Conv 1 1 /neck/Csp_n3/blocks/conv_2/act_1/Mul_output_0 /neck/Csp_n3/blocks/conv_2/conv_pw_1/Conv_output_0 0=32 1=1 5=1 6=1024
HardSwish                /neck/Csp_n3/blocks/conv_2/act_2/Mul 1 1 /neck/Csp_n3/blocks/conv_2/conv_pw_1/Conv_output_0 /neck/Csp_n3/blocks/conv_2/act_2/Mul_output_0 0=1.666667e-01
Convolution              /neck/Csp_n3/conv_2/block/conv/Conv 1 1 /neck/Concat_2_output_0_splitncnn_0 /neck/Csp_n3/conv_2/block/conv/Conv_output_0 0=32 1=1 5=1 6=4096
HardSwish                /neck/Csp_n3/conv_2/block/act/Mul 1 1 /neck/Csp_n3/conv_2/block/conv/Conv_output_0 /neck/Csp_n3/conv_2/block/act/Mul_output_0 0=1.666667e-01
Concat                   /neck/Csp_n3/Concat      2 1 /neck/Csp_n3/blocks/conv_2/act_2/Mul_output_0 /neck/Csp_n3/conv_2/block/act/Mul_output_0 /neck/Csp_n3/Concat_output_0
Convolution              /neck/Csp_n3/conv_3/block/conv/Conv 1 1 /neck/Csp_n3/Concat_output_0 /neck/Csp_n3/conv_3/block/conv/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /neck/Csp_n3/conv_3/block/act/Mul 1 1 /neck/Csp_n3/conv_3/block/conv/Conv_output_0 /neck/Csp_n3/conv_3/block/act/Mul_output_0 0=1.666667e-01
Split                    split_19                 1 2 /neck/Csp_n3/conv_3/block/act/Mul_output_0 /neck/Csp_n3/conv_3/block/act/Mul_output_0_splitncnn_0 /neck/Csp_n3/conv_3/block/act/Mul_output_0_splitncnn_1
ConvolutionDepthWise     /neck/downsample1/conv_dw_1/Conv 1 1 /neck/Csp_n3/conv_3/block/act/Mul_output_0_splitncnn_1 /neck/downsample1/conv_dw_1/Conv_output_0 0=64 1=5 3=2 4=2 5=1 6=1600 7=64
HardSwish                /neck/downsample1/act_1/Mul 1 1 /neck/downsample1/conv_dw_1/Conv_output_0 /neck/downsample1/act_1/Mul_output_0 0=1.666667e-01
Convolution              /neck/downsample1/conv_pw_1/Conv 1 1 /neck/downsample1/act_1/Mul_output_0 /neck/downsample1/conv_pw_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /neck/downsample1/act_2/Mul 1 1 /neck/downsample1/conv_pw_1/Conv_output_0 /neck/downsample1/act_2/Mul_output_0 0=1.666667e-01
Concat                   /neck/Concat_3           2 1 /neck/downsample1/act_2/Mul_output_0 /neck/reduce_layer0/block/act/Mul_output_0_splitncnn_1 /neck/Concat_3_output_0
Split                    split_20                 1 2 /neck/Concat_3_output_0 /neck/Concat_3_output_0_splitncnn_0 /neck/Concat_3_output_0_splitncnn_1
Convolution              /neck/Csp_n4/conv_1/block/conv/Conv 1 1 /neck/Concat_3_output_0_splitncnn_1 /neck/Csp_n4/conv_1/block/conv/Conv_output_0 0=32 1=1 5=1 6=4096
HardSwish                /neck/Csp_n4/conv_1/block/act/Mul 1 1 /neck/Csp_n4/conv_1/block/conv/Conv_output_0 /neck/Csp_n4/conv_1/block/act/Mul_output_0 0=1.666667e-01
Convolution              /neck/Csp_n4/blocks/conv_1/block/conv/Conv 1 1 /neck/Csp_n4/conv_1/block/act/Mul_output_0 /neck/Csp_n4/blocks/conv_1/block/conv/Conv_output_0 0=32 1=1 5=1 6=1024
HardSwish                /neck/Csp_n4/blocks/conv_1/block/act/Mul 1 1 /neck/Csp_n4/blocks/conv_1/block/conv/Conv_output_0 /neck/Csp_n4/blocks/conv_1/block/act/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /neck/Csp_n4/blocks/conv_2/conv_dw_1/Conv 1 1 /neck/Csp_n4/blocks/conv_1/block/act/Mul_output_0 /neck/Csp_n4/blocks/conv_2/conv_dw_1/Conv_output_0 0=32 1=5 4=2 5=1 6=800 7=32
HardSwish                /neck/Csp_n4/blocks/conv_2/act_1/Mul 1 1 /neck/Csp_n4/blocks/conv_2/conv_dw_1/Conv_output_0 /neck/Csp_n4/blocks/conv_2/act_1/Mul_output_0 0=1.666667e-01
Convolution              /neck/Csp_n4/blocks/conv_2/conv_pw_1/Conv 1 1 /neck/Csp_n4/blocks/conv_2/act_1/Mul_output_0 /neck/Csp_n4/blocks/conv_2/conv_pw_1/Conv_output_0 0=32 1=1 5=1 6=1024
HardSwish                /neck/Csp_n4/blocks/conv_2/act_2/Mul 1 1 /neck/Csp_n4/blocks/conv_2/conv_pw_1/Conv_output_0 /neck/Csp_n4/blocks/conv_2/act_2/Mul_output_0 0=1.666667e-01
Convolution              /neck/Csp_n4/conv_2/block/conv/Conv 1 1 /neck/Concat_3_output_0_splitncnn_0 /neck/Csp_n4/conv_2/block/conv/Conv_output_0 0=32 1=1 5=1 6=4096
HardSwish                /neck/Csp_n4/conv_2/block/act/Mul 1 1 /neck/Csp_n4/conv_2/block/conv/Conv_output_0 /neck/Csp_n4/conv_2/block/act/Mul_output_0 0=1.666667e-01
Concat                   /neck/Csp_n4/Concat      2 1 /neck/Csp_n4/blocks/conv_2/act_2/Mul_output_0 /neck/Csp_n4/conv_2/block/act/Mul_output_0 /neck/Csp_n4/Concat_output_0
Convolution              /neck/Csp_n4/conv_3/block/conv/Conv 1 1 /neck/Csp_n4/Concat_output_0 /neck/Csp_n4/conv_3/block/conv/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /neck/Csp_n4/conv_3/block/act/Mul 1 1 /neck/Csp_n4/conv_3/block/conv/Conv_output_0 /neck/Csp_n4/conv_3/block/act/Mul_output_0 0=1.666667e-01
Split                    split_21                 1 4 /neck/Csp_n4/conv_3/block/act/Mul_output_0 /neck/Csp_n4/conv_3/block/act/Mul_output_0_splitncnn_0 /neck/Csp_n4/conv_3/block/act/Mul_output_0_splitncnn_1 /neck/Csp_n4/conv_3/block/act/Mul_output_0_splitncnn_2 /neck/Csp_n4/conv_3/block/act/Mul_output_0_splitncnn_3
ConvolutionDepthWise     /neck/p6_conv_1/conv_dw_1/Conv 1 1 /neck/reduce_layer0/block/act/Mul_output_0_splitncnn_0 /neck/p6_conv_1/conv_dw_1/Conv_output_0 0=64 1=5 3=2 4=2 5=1 6=1600 7=64
HardSwish                /neck/p6_conv_1/act_1/Mul 1 1 /neck/p6_conv_1/conv_dw_1/Conv_output_0 /neck/p6_conv_1/act_1/Mul_output_0 0=1.666667e-01
Convolution              /neck/p6_conv_1/conv_pw_1/Conv 1 1 /neck/p6_conv_1/act_1/Mul_output_0 /neck/p6_conv_1/conv_pw_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /neck/p6_conv_1/act_2/Mul 1 1 /neck/p6_conv_1/conv_pw_1/Conv_output_0 /neck/p6_conv_1/act_2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /neck/p6_conv_2/conv_dw_1/Conv 1 1 /neck/Csp_n4/conv_3/block/act/Mul_output_0_splitncnn_3 /neck/p6_conv_2/conv_dw_1/Conv_output_0 0=64 1=5 3=2 4=2 5=1 6=1600 7=64
HardSwish                /neck/p6_conv_2/act_1/Mul 1 1 /neck/p6_conv_2/conv_dw_1/Conv_output_0 /neck/p6_conv_2/act_1/Mul_output_0 0=1.666667e-01
Convolution              /neck/p6_conv_2/conv_pw_1/Conv 1 1 /neck/p6_conv_2/act_1/Mul_output_0 /neck/p6_conv_2/conv_pw_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /neck/p6_conv_2/act_2/Mul 1 1 /neck/p6_conv_2/conv_pw_1/Conv_output_0 /neck/p6_conv_2/act_2/Mul_output_0 0=1.666667e-01
BinaryOp                 add_10                   2 1 /neck/p6_conv_1/act_2/Mul_output_0 /neck/p6_conv_2/act_2/Mul_output_0 /neck/Add_output_0
Split                    split_22                 1 2 /neck/Add_output_0 /neck/Add_output_0_splitncnn_0 /neck/Add_output_0_splitncnn_1
Interp                   interp_2                 1 1 /neck/Csp_n4/conv_3/block/act/Mul_output_0_splitncnn_2 /neck/fpn_upsample0/Resize_output_0 0=1 1=2.000000e+00 2=2.000000e+00
Concat                   /neck/Concat_4           2 1 /neck/fpn_upsample0/Resize_output_0 /neck/Csp_n3/conv_3/block/act/Mul_output_0_splitncnn_0 /neck/Concat_4_output_0
Split                    split_23                 1 2 /neck/Concat_4_output_0 /neck/Concat_4_output_0_splitncnn_0 /neck/Concat_4_output_0_splitncnn_1
Convolution              /neck/fpn_Csp_p4/conv_1/block/conv/Conv 1 1 /neck/Concat_4_output_0_splitncnn_1 /neck/fpn_Csp_p4/conv_1/block/conv/Conv_output_0 0=32 1=1 5=1 6=4096
HardSwish                /neck/fpn_Csp_p4/conv_1/block/act/Mul 1 1 /neck/fpn_Csp_p4/conv_1/block/conv/Conv_output_0 /neck/fpn_Csp_p4/conv_1/block/act/Mul_output_0 0=1.666667e-01
Convolution              /neck/fpn_Csp_p4/blocks/conv_1/block/conv/Conv 1 1 /neck/fpn_Csp_p4/conv_1/block/act/Mul_output_0 /neck/fpn_Csp_p4/blocks/conv_1/block/conv/Conv_output_0 0=32 1=1 5=1 6=1024
HardSwish                /neck/fpn_Csp_p4/blocks/conv_1/block/act/Mul 1 1 /neck/fpn_Csp_p4/blocks/conv_1/block/conv/Conv_output_0 /neck/fpn_Csp_p4/blocks/conv_1/block/act/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /neck/fpn_Csp_p4/blocks/conv_2/conv_dw_1/Conv 1 1 /neck/fpn_Csp_p4/blocks/conv_1/block/act/Mul_output_0 /neck/fpn_Csp_p4/blocks/conv_2/conv_dw_1/Conv_output_0 0=32 1=5 4=2 5=1 6=800 7=32
HardSwish                /neck/fpn_Csp_p4/blocks/conv_2/act_1/Mul 1 1 /neck/fpn_Csp_p4/blocks/conv_2/conv_dw_1/Conv_output_0 /neck/fpn_Csp_p4/blocks/conv_2/act_1/Mul_output_0 0=1.666667e-01
Convolution              /neck/fpn_Csp_p4/blocks/conv_2/conv_pw_1/Conv 1 1 /neck/fpn_Csp_p4/blocks/conv_2/act_1/Mul_output_0 /neck/fpn_Csp_p4/blocks/conv_2/conv_pw_1/Conv_output_0 0=32 1=1 5=1 6=1024
HardSwish                /neck/fpn_Csp_p4/blocks/conv_2/act_2/Mul 1 1 /neck/fpn_Csp_p4/blocks/conv_2/conv_pw_1/Conv_output_0 /neck/fpn_Csp_p4/blocks/conv_2/act_2/Mul_output_0 0=1.666667e-01
Convolution              /neck/fpn_Csp_p4/conv_2/block/conv/Conv 1 1 /neck/Concat_4_output_0_splitncnn_0 /neck/fpn_Csp_p4/conv_2/block/conv/Conv_output_0 0=32 1=1 5=1 6=4096
HardSwish                /neck/fpn_Csp_p4/conv_2/block/act/Mul 1 1 /neck/fpn_Csp_p4/conv_2/block/conv/Conv_output_0 /neck/fpn_Csp_p4/conv_2/block/act/Mul_output_0 0=1.666667e-01
Concat                   /neck/fpn_Csp_p4/Concat  2 1 /neck/fpn_Csp_p4/blocks/conv_2/act_2/Mul_output_0 /neck/fpn_Csp_p4/conv_2/block/act/Mul_output_0 /neck/fpn_Csp_p4/Concat_output_0
Convolution              /neck/fpn_Csp_p4/conv_3/block/conv/Conv 1 1 /neck/fpn_Csp_p4/Concat_output_0 /neck/fpn_Csp_p4/conv_3/block/conv/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /neck/fpn_Csp_p4/conv_3/block/act/Mul 1 1 /neck/fpn_Csp_p4/conv_3/block/conv/Conv_output_0 /neck/fpn_Csp_p4/conv_3/block/act/Mul_output_0 0=1.666667e-01
Split                    split_24                 1 3 /neck/fpn_Csp_p4/conv_3/block/act/Mul_output_0 /neck/fpn_Csp_p4/conv_3/block/act/Mul_output_0_splitncnn_0 /neck/fpn_Csp_p4/conv_3/block/act/Mul_output_0_splitncnn_1 /neck/fpn_Csp_p4/conv_3/block/act/Mul_output_0_splitncnn_2
Interp                   interp_3                 1 1 /neck/fpn_Csp_p4/conv_3/block/act/Mul_output_0_splitncnn_2 /neck/fpn_upsample1/Resize_output_0 0=1 1=2.000000e+00 2=2.000000e+00
Concat                   /neck/Concat_5           2 1 /neck/fpn_upsample1/Resize_output_0 /neck/Csp_p3/conv_3/block/act/Mul_output_0_splitncnn_0 /neck/Concat_5_output_0
Split                    split_25                 1 2 /neck/Concat_5_output_0 /neck/Concat_5_output_0_splitncnn_0 /neck/Concat_5_output_0_splitncnn_1
Convolution              /neck/fpn_Csp_p3/conv_1/block/conv/Conv 1 1 /neck/Concat_5_output_0_splitncnn_1 /neck/fpn_Csp_p3/conv_1/block/conv/Conv_output_0 0=32 1=1 5=1 6=4096
HardSwish                /neck/fpn_Csp_p3/conv_1/block/act/Mul 1 1 /neck/fpn_Csp_p3/conv_1/block/conv/Conv_output_0 /neck/fpn_Csp_p3/conv_1/block/act/Mul_output_0 0=1.666667e-01
Convolution              /neck/fpn_Csp_p3/blocks/conv_1/block/conv/Conv 1 1 /neck/fpn_Csp_p3/conv_1/block/act/Mul_output_0 /neck/fpn_Csp_p3/blocks/conv_1/block/conv/Conv_output_0 0=32 1=1 5=1 6=1024
HardSwish                /neck/fpn_Csp_p3/blocks/conv_1/block/act/Mul 1 1 /neck/fpn_Csp_p3/blocks/conv_1/block/conv/Conv_output_0 /neck/fpn_Csp_p3/blocks/conv_1/block/act/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /neck/fpn_Csp_p3/blocks/conv_2/conv_dw_1/Conv 1 1 /neck/fpn_Csp_p3/blocks/conv_1/block/act/Mul_output_0 /neck/fpn_Csp_p3/blocks/conv_2/conv_dw_1/Conv_output_0 0=32 1=5 4=2 5=1 6=800 7=32
HardSwish                /neck/fpn_Csp_p3/blocks/conv_2/act_1/Mul 1 1 /neck/fpn_Csp_p3/blocks/conv_2/conv_dw_1/Conv_output_0 /neck/fpn_Csp_p3/blocks/conv_2/act_1/Mul_output_0 0=1.666667e-01
Convolution              /neck/fpn_Csp_p3/blocks/conv_2/conv_pw_1/Conv 1 1 /neck/fpn_Csp_p3/blocks/conv_2/act_1/Mul_output_0 /neck/fpn_Csp_p3/blocks/conv_2/conv_pw_1/Conv_output_0 0=32 1=1 5=1 6=1024
HardSwish                /neck/fpn_Csp_p3/blocks/conv_2/act_2/Mul 1 1 /neck/fpn_Csp_p3/blocks/conv_2/conv_pw_1/Conv_output_0 /neck/fpn_Csp_p3/blocks/conv_2/act_2/Mul_output_0 0=1.666667e-01
Convolution              /neck/fpn_Csp_p3/conv_2/block/conv/Conv 1 1 /neck/Concat_5_output_0_splitncnn_0 /neck/fpn_Csp_p3/conv_2/block/conv/Conv_output_0 0=32 1=1 5=1 6=4096
HardSwish                /neck/fpn_Csp_p3/conv_2/block/act/Mul 1 1 /neck/fpn_Csp_p3/conv_2/block/conv/Conv_output_0 /neck/fpn_Csp_p3/conv_2/block/act/Mul_output_0 0=1.666667e-01
Concat                   /neck/fpn_Csp_p3/Concat  2 1 /neck/fpn_Csp_p3/blocks/conv_2/act_2/Mul_output_0 /neck/fpn_Csp_p3/conv_2/block/act/Mul_output_0 /neck/fpn_Csp_p3/Concat_output_0
Convolution              /neck/fpn_Csp_p3/conv_3/block/conv/Conv 1 1 /neck/fpn_Csp_p3/Concat_output_0 /neck/fpn_Csp_p3/conv_3/block/conv/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /neck/fpn_Csp_p3/conv_3/block/act/Mul 1 1 /neck/fpn_Csp_p3/conv_3/block/conv/Conv_output_0 /neck/fpn_Csp_p3/conv_3/block/act/Mul_output_0 0=1.666667e-01
Split                    split_26                 1 2 /neck/fpn_Csp_p3/conv_3/block/act/Mul_output_0 /neck/fpn_Csp_p3/conv_3/block/act/Mul_output_0_splitncnn_0 /neck/fpn_Csp_p3/conv_3/block/act/Mul_output_0_splitncnn_1
ConvolutionDepthWise     /detect/cls_convs/cls_convs.0/Conv 1 1 /neck/fpn_Csp_p3/conv_3/block/act/Mul_output_0_splitncnn_1 /detect/cls_convs/cls_convs.0/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.1/Conv 1 1 /detect/cls_convs/cls_convs.0/Conv_output_0 /detect/cls_convs/cls_convs.1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.3/Mul 1 1 /detect/cls_convs/cls_convs.1/Conv_output_0 /detect/cls_convs/cls_convs.3/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_convs/cls_convs.4/Conv 1 1 /detect/cls_convs/cls_convs.3/Mul_output_0 /detect/cls_convs/cls_convs.4/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.5/Conv 1 1 /detect/cls_convs/cls_convs.4/Conv_output_0 /detect/cls_convs/cls_convs.5/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.7/Mul 1 1 /detect/cls_convs/cls_convs.5/Conv_output_0 /detect/cls_convs/cls_convs.7/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_convs/cls_convs.8/Conv 1 1 /detect/cls_convs/cls_convs.7/Mul_output_0 /detect/cls_convs/cls_convs.8/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.9/Conv 1 1 /detect/cls_convs/cls_convs.8/Conv_output_0 /detect/cls_convs/cls_convs.9/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.11/Mul 1 1 /detect/cls_convs/cls_convs.9/Conv_output_0 /detect/cls_convs/cls_convs.11/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_convs/cls_convs.12/Conv 1 1 /detect/cls_convs/cls_convs.11/Mul_output_0 /detect/cls_convs/cls_convs.12/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.13/Conv 1 1 /detect/cls_convs/cls_convs.12/Conv_output_0 /detect/cls_convs/cls_convs.13/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.15/Mul 1 1 /detect/cls_convs/cls_convs.13/Conv_output_0 /detect/cls_convs/cls_convs.15/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_preds/cls_preds.0/Conv 1 1 /detect/cls_convs/cls_convs.15/Mul_output_0 /detect/cls_preds/cls_preds.0/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_preds/cls_preds.1/Conv 1 1 /detect/cls_preds/cls_preds.0/Conv_output_0 /detect/cls_preds/cls_preds.1/Conv_output_0 0=3 1=1 5=1 6=192
ConvolutionDepthWise     /detect/reg_convs/reg_convs.0/Conv 1 1 /neck/fpn_Csp_p3/conv_3/block/act/Mul_output_0_splitncnn_0 /detect/reg_convs/reg_convs.0/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.1/Conv 1 1 /detect/reg_convs/reg_convs.0/Conv_output_0 /detect/reg_convs/reg_convs.1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.3/Mul 1 1 /detect/reg_convs/reg_convs.1/Conv_output_0 /detect/reg_convs/reg_convs.3/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/reg_convs/reg_convs.4/Conv 1 1 /detect/reg_convs/reg_convs.3/Mul_output_0 /detect/reg_convs/reg_convs.4/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.5/Conv 1 1 /detect/reg_convs/reg_convs.4/Conv_output_0 /detect/reg_convs/reg_convs.5/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.7/Mul 1 1 /detect/reg_convs/reg_convs.5/Conv_output_0 /detect/reg_convs/reg_convs.7/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/reg_convs/reg_convs.8/Conv 1 1 /detect/reg_convs/reg_convs.7/Mul_output_0 /detect/reg_convs/reg_convs.8/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.9/Conv 1 1 /detect/reg_convs/reg_convs.8/Conv_output_0 /detect/reg_convs/reg_convs.9/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.11/Mul 1 1 /detect/reg_convs/reg_convs.9/Conv_output_0 /detect/reg_convs/reg_convs.11/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/reg_convs/reg_convs.12/Conv 1 1 /detect/reg_convs/reg_convs.11/Mul_output_0 /detect/reg_convs/reg_convs.12/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.13/Conv 1 1 /detect/reg_convs/reg_convs.12/Conv_output_0 /detect/reg_convs/reg_convs.13/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.15/Mul 1 1 /detect/reg_convs/reg_convs.13/Conv_output_0 /detect/reg_convs/reg_convs.15/Mul_output_0 0=1.666667e-01
Split                    split_27                 1 2 /detect/reg_convs/reg_convs.15/Mul_output_0 /detect/reg_convs/reg_convs.15/Mul_output_0_splitncnn_0 /detect/reg_convs/reg_convs.15/Mul_output_0_splitncnn_1
ConvolutionDepthWise     /detect/reg_preds/reg_preds.0/Conv 1 1 /detect/reg_convs/reg_convs.15/Mul_output_0_splitncnn_1 /detect/reg_preds/reg_preds.0/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_preds/reg_preds.1/Conv 1 1 /detect/reg_preds/reg_preds.0/Conv_output_0 /detect/Relu_output_0 0=4 1=1 5=1 6=256 9=1
ConvolutionDepthWise     /detect/kpt_stem/kpt_stem.0/Conv 1 1 /detect/reg_convs/reg_convs.15/Mul_output_0_splitncnn_0 /detect/kpt_stem/kpt_stem.0/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/kpt_stem/kpt_stem.1/Conv 1 1 /detect/kpt_stem/kpt_stem.0/Conv_output_0 /detect/kpt_stem/kpt_stem.1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/kpt_stem/kpt_stem.3/Mul 1 1 /detect/kpt_stem/kpt_stem.1/Conv_output_0 /detect/kpt_stem/kpt_stem.3/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/kpt_stem/kpt_stem.4/Conv 1 1 /detect/kpt_stem/kpt_stem.3/Mul_output_0 /detect/kpt_stem/kpt_stem.4/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/kpt_stem/kpt_stem.5/Conv 1 1 /detect/kpt_stem/kpt_stem.4/Conv_output_0 /detect/kpt_stem/kpt_stem.5/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/kpt_stem/kpt_stem.7/Mul 1 1 /detect/kpt_stem/kpt_stem.5/Conv_output_0 /detect/kpt_stem/kpt_stem.7/Mul_output_0 0=1.666667e-01
Split                    split_28                 1 5 /detect/kpt_stem/kpt_stem.7/Mul_output_0 /detect/kpt_stem/kpt_stem.7/Mul_output_0_splitncnn_0 /detect/kpt_stem/kpt_stem.7/Mul_output_0_splitncnn_1 /detect/kpt_stem/kpt_stem.7/Mul_output_0_splitncnn_2 /detect/kpt_stem/kpt_stem.7/Mul_output_0_splitncnn_3 /detect/kpt_stem/kpt_stem.7/Mul_output_0_splitncnn_4
ConvolutionDepthWise     /detect/head_preds/head_preds.0/Conv 1 1 /detect/kpt_stem/kpt_stem.7/Mul_output_0_splitncnn_4 /detect/head_preds/head_preds.0/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/head_preds/head_preds.1/Conv 1 1 /detect/head_preds/head_preds.0/Conv_output_0 /detect/head_preds/head_preds.1/Conv_output_0 0=30 1=1 5=1 6=1920
ConvolutionDepthWise     /detect/left_arm_preds/left_arm_preds.0/Conv 1 1 /detect/kpt_stem/kpt_stem.7/Mul_output_0_splitncnn_3 /detect/left_arm_preds/left_arm_preds.0/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/left_arm_preds/left_arm_preds.1/Conv 1 1 /detect/left_arm_preds/left_arm_preds.0/Conv_output_0 /detect/left_arm_preds/left_arm_preds.1/Conv_output_0 0=6 1=1 5=1 6=384
ConvolutionDepthWise     /detect/right_arm_preds/right_arm_preds.0/Conv 1 1 /detect/kpt_stem/kpt_stem.7/Mul_output_0_splitncnn_2 /detect/right_arm_preds/right_arm_preds.0/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/right_arm_preds/right_arm_preds.1/Conv 1 1 /detect/right_arm_preds/right_arm_preds.0/Conv_output_0 /detect/right_arm_preds/right_arm_preds.1/Conv_output_0 0=6 1=1 5=1 6=384
ConvolutionDepthWise     /detect/left_leg_preds/left_leg_preds.0/Conv 1 1 /detect/kpt_stem/kpt_stem.7/Mul_output_0_splitncnn_1 /detect/left_leg_preds/left_leg_preds.0/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/left_leg_preds/left_leg_preds.1/Conv 1 1 /detect/left_leg_preds/left_leg_preds.0/Conv_output_0 /detect/left_leg_preds/left_leg_preds.1/Conv_output_0 0=15 1=1 5=1 6=960
ConvolutionDepthWise     /detect/right_leg_preds/right_leg_preds.0/Conv 1 1 /detect/kpt_stem/kpt_stem.7/Mul_output_0_splitncnn_0 /detect/right_leg_preds/right_leg_preds.0/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/right_leg_preds/right_leg_preds.1/Conv 1 1 /detect/right_leg_preds/right_leg_preds.0/Conv_output_0 /detect/right_leg_preds/right_leg_preds.1/Conv_output_0 0=15 1=1 5=1 6=960
Concat                   /detect/Concat           5 1 /detect/head_preds/head_preds.1/Conv_output_0 /detect/left_arm_preds/left_arm_preds.1/Conv_output_0 /detect/right_arm_preds/right_arm_preds.1/Conv_output_0 /detect/left_leg_preds/left_leg_preds.1/Conv_output_0 /detect/right_leg_preds/right_leg_preds.1/Conv_output_0 /detect/Concat_output_0
Reshape                  reshape_0                1 1 /detect/cls_preds/cls_preds.1/Conv_output_0 /detect/Reshape_output_0 0=4800 1=3
Permute                  /detect/Transpose        1 1 /detect/Reshape_output_0 P3/logits 0=1
Reshape                  reshape_1                1 1 /detect/Relu_output_0 /detect/Reshape_1_output_0 0=4800 1=4
Permute                  /detect/Transpose_1      1 1 /detect/Reshape_1_output_0 P3/bbox_reg 0=1
Reshape                  reshape_2                1 1 /detect/Concat_output_0 /detect/Reshape_2_output_0 0=4800 1=72
Permute                  /detect/Transpose_2      1 1 /detect/Reshape_2_output_0 P3/keypoints 0=1
ConvolutionDepthWise     /detect/cls_convs/cls_convs.0_1/Conv 1 1 /neck/fpn_Csp_p4/conv_3/block/act/Mul_output_0_splitncnn_1 /detect/cls_convs/cls_convs.0_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.1_1/Conv 1 1 /detect/cls_convs/cls_convs.0_1/Conv_output_0 /detect/cls_convs/cls_convs.1_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.3_1/Mul 1 1 /detect/cls_convs/cls_convs.1_1/Conv_output_0 /detect/cls_convs/cls_convs.3_1/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_convs/cls_convs.4_1/Conv 1 1 /detect/cls_convs/cls_convs.3_1/Mul_output_0 /detect/cls_convs/cls_convs.4_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.5_1/Conv 1 1 /detect/cls_convs/cls_convs.4_1/Conv_output_0 /detect/cls_convs/cls_convs.5_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.7_1/Mul 1 1 /detect/cls_convs/cls_convs.5_1/Conv_output_0 /detect/cls_convs/cls_convs.7_1/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_convs/cls_convs.8_1/Conv 1 1 /detect/cls_convs/cls_convs.7_1/Mul_output_0 /detect/cls_convs/cls_convs.8_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.9_1/Conv 1 1 /detect/cls_convs/cls_convs.8_1/Conv_output_0 /detect/cls_convs/cls_convs.9_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.11_1/Mul 1 1 /detect/cls_convs/cls_convs.9_1/Conv_output_0 /detect/cls_convs/cls_convs.11_1/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_convs/cls_convs.12_1/Conv 1 1 /detect/cls_convs/cls_convs.11_1/Mul_output_0 /detect/cls_convs/cls_convs.12_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.13_1/Conv 1 1 /detect/cls_convs/cls_convs.12_1/Conv_output_0 /detect/cls_convs/cls_convs.13_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.15_1/Mul 1 1 /detect/cls_convs/cls_convs.13_1/Conv_output_0 /detect/cls_convs/cls_convs.15_1/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_preds/cls_preds.0_1/Conv 1 1 /detect/cls_convs/cls_convs.15_1/Mul_output_0 /detect/cls_preds/cls_preds.0_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_preds/cls_preds.1_1/Conv 1 1 /detect/cls_preds/cls_preds.0_1/Conv_output_0 /detect/cls_preds/cls_preds.1_1/Conv_output_0 0=3 1=1 5=1 6=192
ConvolutionDepthWise     /detect/reg_convs/reg_convs.0_1/Conv 1 1 /neck/fpn_Csp_p4/conv_3/block/act/Mul_output_0_splitncnn_0 /detect/reg_convs/reg_convs.0_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.1_1/Conv 1 1 /detect/reg_convs/reg_convs.0_1/Conv_output_0 /detect/reg_convs/reg_convs.1_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.3_1/Mul 1 1 /detect/reg_convs/reg_convs.1_1/Conv_output_0 /detect/reg_convs/reg_convs.3_1/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/reg_convs/reg_convs.4_1/Conv 1 1 /detect/reg_convs/reg_convs.3_1/Mul_output_0 /detect/reg_convs/reg_convs.4_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.5_1/Conv 1 1 /detect/reg_convs/reg_convs.4_1/Conv_output_0 /detect/reg_convs/reg_convs.5_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.7_1/Mul 1 1 /detect/reg_convs/reg_convs.5_1/Conv_output_0 /detect/reg_convs/reg_convs.7_1/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/reg_convs/reg_convs.8_1/Conv 1 1 /detect/reg_convs/reg_convs.7_1/Mul_output_0 /detect/reg_convs/reg_convs.8_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.9_1/Conv 1 1 /detect/reg_convs/reg_convs.8_1/Conv_output_0 /detect/reg_convs/reg_convs.9_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.11_1/Mul 1 1 /detect/reg_convs/reg_convs.9_1/Conv_output_0 /detect/reg_convs/reg_convs.11_1/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/reg_convs/reg_convs.12_1/Conv 1 1 /detect/reg_convs/reg_convs.11_1/Mul_output_0 /detect/reg_convs/reg_convs.12_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.13_1/Conv 1 1 /detect/reg_convs/reg_convs.12_1/Conv_output_0 /detect/reg_convs/reg_convs.13_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.15_1/Mul 1 1 /detect/reg_convs/reg_convs.13_1/Conv_output_0 /detect/reg_convs/reg_convs.15_1/Mul_output_0 0=1.666667e-01
Split                    split_29                 1 2 /detect/reg_convs/reg_convs.15_1/Mul_output_0 /detect/reg_convs/reg_convs.15_1/Mul_output_0_splitncnn_0 /detect/reg_convs/reg_convs.15_1/Mul_output_0_splitncnn_1
ConvolutionDepthWise     /detect/reg_preds/reg_preds.0_1/Conv 1 1 /detect/reg_convs/reg_convs.15_1/Mul_output_0_splitncnn_1 /detect/reg_preds/reg_preds.0_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_preds/reg_preds.1_1/Conv 1 1 /detect/reg_preds/reg_preds.0_1/Conv_output_0 /detect/reg_preds/reg_preds.1_1/Conv_output_0 0=4 1=1 5=1 6=256
BinaryOp                 /detect/scales.1/Mul     1 1 /detect/reg_preds/reg_preds.1_1/Conv_output_0 /detect/scales.1/Mul_output_0 0=2 1=1 2=1.000000e+00
ReLU                     relu_1                   1 1 /detect/scales.1/Mul_output_0 /detect/Relu_1_output_0
ConvolutionDepthWise     /detect/kpt_stem/kpt_stem.0_1/Conv 1 1 /detect/reg_convs/reg_convs.15_1/Mul_output_0_splitncnn_0 /detect/kpt_stem/kpt_stem.0_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/kpt_stem/kpt_stem.1_1/Conv 1 1 /detect/kpt_stem/kpt_stem.0_1/Conv_output_0 /detect/kpt_stem/kpt_stem.1_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/kpt_stem/kpt_stem.3_1/Mul 1 1 /detect/kpt_stem/kpt_stem.1_1/Conv_output_0 /detect/kpt_stem/kpt_stem.3_1/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/kpt_stem/kpt_stem.4_1/Conv 1 1 /detect/kpt_stem/kpt_stem.3_1/Mul_output_0 /detect/kpt_stem/kpt_stem.4_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/kpt_stem/kpt_stem.5_1/Conv 1 1 /detect/kpt_stem/kpt_stem.4_1/Conv_output_0 /detect/kpt_stem/kpt_stem.5_1/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/kpt_stem/kpt_stem.7_1/Mul 1 1 /detect/kpt_stem/kpt_stem.5_1/Conv_output_0 /detect/kpt_stem/kpt_stem.7_1/Mul_output_0 0=1.666667e-01
Split                    split_30                 1 5 /detect/kpt_stem/kpt_stem.7_1/Mul_output_0 /detect/kpt_stem/kpt_stem.7_1/Mul_output_0_splitncnn_0 /detect/kpt_stem/kpt_stem.7_1/Mul_output_0_splitncnn_1 /detect/kpt_stem/kpt_stem.7_1/Mul_output_0_splitncnn_2 /detect/kpt_stem/kpt_stem.7_1/Mul_output_0_splitncnn_3 /detect/kpt_stem/kpt_stem.7_1/Mul_output_0_splitncnn_4
ConvolutionDepthWise     /detect/head_preds/head_preds.0_1/Conv 1 1 /detect/kpt_stem/kpt_stem.7_1/Mul_output_0_splitncnn_4 /detect/head_preds/head_preds.0_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/head_preds/head_preds.1_1/Conv 1 1 /detect/head_preds/head_preds.0_1/Conv_output_0 /detect/head_preds/head_preds.1_1/Conv_output_0 0=30 1=1 5=1 6=1920
ConvolutionDepthWise     /detect/left_arm_preds/left_arm_preds.0_1/Conv 1 1 /detect/kpt_stem/kpt_stem.7_1/Mul_output_0_splitncnn_3 /detect/left_arm_preds/left_arm_preds.0_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/left_arm_preds/left_arm_preds.1_1/Conv 1 1 /detect/left_arm_preds/left_arm_preds.0_1/Conv_output_0 /detect/left_arm_preds/left_arm_preds.1_1/Conv_output_0 0=6 1=1 5=1 6=384
ConvolutionDepthWise     /detect/right_arm_preds/right_arm_preds.0_1/Conv 1 1 /detect/kpt_stem/kpt_stem.7_1/Mul_output_0_splitncnn_2 /detect/right_arm_preds/right_arm_preds.0_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/right_arm_preds/right_arm_preds.1_1/Conv 1 1 /detect/right_arm_preds/right_arm_preds.0_1/Conv_output_0 /detect/right_arm_preds/right_arm_preds.1_1/Conv_output_0 0=6 1=1 5=1 6=384
ConvolutionDepthWise     /detect/left_leg_preds/left_leg_preds.0_1/Conv 1 1 /detect/kpt_stem/kpt_stem.7_1/Mul_output_0_splitncnn_1 /detect/left_leg_preds/left_leg_preds.0_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/left_leg_preds/left_leg_preds.1_1/Conv 1 1 /detect/left_leg_preds/left_leg_preds.0_1/Conv_output_0 /detect/left_leg_preds/left_leg_preds.1_1/Conv_output_0 0=15 1=1 5=1 6=960
ConvolutionDepthWise     /detect/right_leg_preds/right_leg_preds.0_1/Conv 1 1 /detect/kpt_stem/kpt_stem.7_1/Mul_output_0_splitncnn_0 /detect/right_leg_preds/right_leg_preds.0_1/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/right_leg_preds/right_leg_preds.1_1/Conv 1 1 /detect/right_leg_preds/right_leg_preds.0_1/Conv_output_0 /detect/right_leg_preds/right_leg_preds.1_1/Conv_output_0 0=15 1=1 5=1 6=960
Concat                   /detect/Concat_1         5 1 /detect/head_preds/head_preds.1_1/Conv_output_0 /detect/left_arm_preds/left_arm_preds.1_1/Conv_output_0 /detect/right_arm_preds/right_arm_preds.1_1/Conv_output_0 /detect/left_leg_preds/left_leg_preds.1_1/Conv_output_0 /detect/right_leg_preds/right_leg_preds.1_1/Conv_output_0 /detect/Concat_1_output_0
Reshape                  reshape_3                1 1 /detect/cls_preds/cls_preds.1_1/Conv_output_0 /detect/Reshape_3_output_0 0=1200 1=3
Permute                  /detect/Transpose_3      1 1 /detect/Reshape_3_output_0 P4/logits 0=1
Reshape                  reshape_4                1 1 /detect/Relu_1_output_0 /detect/Reshape_4_output_0 0=1200 1=4
Permute                  /detect/Transpose_4      1 1 /detect/Reshape_4_output_0 P4/bbox_reg 0=1
Reshape                  reshape_5                1 1 /detect/Concat_1_output_0 /detect/Reshape_5_output_0 0=1200 1=72
Permute                  /detect/Transpose_5      1 1 /detect/Reshape_5_output_0 P4/keypoints 0=1
ConvolutionDepthWise     /detect/cls_convs/cls_convs.0_2/Conv 1 1 /neck/Csp_n4/conv_3/block/act/Mul_output_0_splitncnn_1 /detect/cls_convs/cls_convs.0_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.1_2/Conv 1 1 /detect/cls_convs/cls_convs.0_2/Conv_output_0 /detect/cls_convs/cls_convs.1_2/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.3_2/Mul 1 1 /detect/cls_convs/cls_convs.1_2/Conv_output_0 /detect/cls_convs/cls_convs.3_2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_convs/cls_convs.4_2/Conv 1 1 /detect/cls_convs/cls_convs.3_2/Mul_output_0 /detect/cls_convs/cls_convs.4_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.5_2/Conv 1 1 /detect/cls_convs/cls_convs.4_2/Conv_output_0 /detect/cls_convs/cls_convs.5_2/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.7_2/Mul 1 1 /detect/cls_convs/cls_convs.5_2/Conv_output_0 /detect/cls_convs/cls_convs.7_2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_convs/cls_convs.8_2/Conv 1 1 /detect/cls_convs/cls_convs.7_2/Mul_output_0 /detect/cls_convs/cls_convs.8_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.9_2/Conv 1 1 /detect/cls_convs/cls_convs.8_2/Conv_output_0 /detect/cls_convs/cls_convs.9_2/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.11_2/Mul 1 1 /detect/cls_convs/cls_convs.9_2/Conv_output_0 /detect/cls_convs/cls_convs.11_2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_convs/cls_convs.12_2/Conv 1 1 /detect/cls_convs/cls_convs.11_2/Mul_output_0 /detect/cls_convs/cls_convs.12_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.13_2/Conv 1 1 /detect/cls_convs/cls_convs.12_2/Conv_output_0 /detect/cls_convs/cls_convs.13_2/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.15_2/Mul 1 1 /detect/cls_convs/cls_convs.13_2/Conv_output_0 /detect/cls_convs/cls_convs.15_2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_preds/cls_preds.0_2/Conv 1 1 /detect/cls_convs/cls_convs.15_2/Mul_output_0 /detect/cls_preds/cls_preds.0_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_preds/cls_preds.1_2/Conv 1 1 /detect/cls_preds/cls_preds.0_2/Conv_output_0 /detect/cls_preds/cls_preds.1_2/Conv_output_0 0=3 1=1 5=1 6=192
ConvolutionDepthWise     /detect/reg_convs/reg_convs.0_2/Conv 1 1 /neck/Csp_n4/conv_3/block/act/Mul_output_0_splitncnn_0 /detect/reg_convs/reg_convs.0_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.1_2/Conv 1 1 /detect/reg_convs/reg_convs.0_2/Conv_output_0 /detect/reg_convs/reg_convs.1_2/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.3_2/Mul 1 1 /detect/reg_convs/reg_convs.1_2/Conv_output_0 /detect/reg_convs/reg_convs.3_2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/reg_convs/reg_convs.4_2/Conv 1 1 /detect/reg_convs/reg_convs.3_2/Mul_output_0 /detect/reg_convs/reg_convs.4_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.5_2/Conv 1 1 /detect/reg_convs/reg_convs.4_2/Conv_output_0 /detect/reg_convs/reg_convs.5_2/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.7_2/Mul 1 1 /detect/reg_convs/reg_convs.5_2/Conv_output_0 /detect/reg_convs/reg_convs.7_2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/reg_convs/reg_convs.8_2/Conv 1 1 /detect/reg_convs/reg_convs.7_2/Mul_output_0 /detect/reg_convs/reg_convs.8_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.9_2/Conv 1 1 /detect/reg_convs/reg_convs.8_2/Conv_output_0 /detect/reg_convs/reg_convs.9_2/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.11_2/Mul 1 1 /detect/reg_convs/reg_convs.9_2/Conv_output_0 /detect/reg_convs/reg_convs.11_2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/reg_convs/reg_convs.12_2/Conv 1 1 /detect/reg_convs/reg_convs.11_2/Mul_output_0 /detect/reg_convs/reg_convs.12_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.13_2/Conv 1 1 /detect/reg_convs/reg_convs.12_2/Conv_output_0 /detect/reg_convs/reg_convs.13_2/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.15_2/Mul 1 1 /detect/reg_convs/reg_convs.13_2/Conv_output_0 /detect/reg_convs/reg_convs.15_2/Mul_output_0 0=1.666667e-01
Split                    split_31                 1 2 /detect/reg_convs/reg_convs.15_2/Mul_output_0 /detect/reg_convs/reg_convs.15_2/Mul_output_0_splitncnn_0 /detect/reg_convs/reg_convs.15_2/Mul_output_0_splitncnn_1
ConvolutionDepthWise     /detect/reg_preds/reg_preds.0_2/Conv 1 1 /detect/reg_convs/reg_convs.15_2/Mul_output_0_splitncnn_1 /detect/reg_preds/reg_preds.0_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_preds/reg_preds.1_2/Conv 1 1 /detect/reg_preds/reg_preds.0_2/Conv_output_0 /detect/reg_preds/reg_preds.1_2/Conv_output_0 0=4 1=1 5=1 6=256
BinaryOp                 /detect/scales.2/Mul     1 1 /detect/reg_preds/reg_preds.1_2/Conv_output_0 /detect/scales.2/Mul_output_0 0=2 1=1 2=1.000000e+00
ReLU                     relu_2                   1 1 /detect/scales.2/Mul_output_0 /detect/Relu_2_output_0
ConvolutionDepthWise     /detect/kpt_stem/kpt_stem.0_2/Conv 1 1 /detect/reg_convs/reg_convs.15_2/Mul_output_0_splitncnn_0 /detect/kpt_stem/kpt_stem.0_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/kpt_stem/kpt_stem.1_2/Conv 1 1 /detect/kpt_stem/kpt_stem.0_2/Conv_output_0 /detect/kpt_stem/kpt_stem.1_2/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/kpt_stem/kpt_stem.3_2/Mul 1 1 /detect/kpt_stem/kpt_stem.1_2/Conv_output_0 /detect/kpt_stem/kpt_stem.3_2/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/kpt_stem/kpt_stem.4_2/Conv 1 1 /detect/kpt_stem/kpt_stem.3_2/Mul_output_0 /detect/kpt_stem/kpt_stem.4_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/kpt_stem/kpt_stem.5_2/Conv 1 1 /detect/kpt_stem/kpt_stem.4_2/Conv_output_0 /detect/kpt_stem/kpt_stem.5_2/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/kpt_stem/kpt_stem.7_2/Mul 1 1 /detect/kpt_stem/kpt_stem.5_2/Conv_output_0 /detect/kpt_stem/kpt_stem.7_2/Mul_output_0 0=1.666667e-01
Split                    split_32                 1 5 /detect/kpt_stem/kpt_stem.7_2/Mul_output_0 /detect/kpt_stem/kpt_stem.7_2/Mul_output_0_splitncnn_0 /detect/kpt_stem/kpt_stem.7_2/Mul_output_0_splitncnn_1 /detect/kpt_stem/kpt_stem.7_2/Mul_output_0_splitncnn_2 /detect/kpt_stem/kpt_stem.7_2/Mul_output_0_splitncnn_3 /detect/kpt_stem/kpt_stem.7_2/Mul_output_0_splitncnn_4
ConvolutionDepthWise     /detect/head_preds/head_preds.0_2/Conv 1 1 /detect/kpt_stem/kpt_stem.7_2/Mul_output_0_splitncnn_4 /detect/head_preds/head_preds.0_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/head_preds/head_preds.1_2/Conv 1 1 /detect/head_preds/head_preds.0_2/Conv_output_0 /detect/head_preds/head_preds.1_2/Conv_output_0 0=30 1=1 5=1 6=1920
ConvolutionDepthWise     /detect/left_arm_preds/left_arm_preds.0_2/Conv 1 1 /detect/kpt_stem/kpt_stem.7_2/Mul_output_0_splitncnn_3 /detect/left_arm_preds/left_arm_preds.0_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/left_arm_preds/left_arm_preds.1_2/Conv 1 1 /detect/left_arm_preds/left_arm_preds.0_2/Conv_output_0 /detect/left_arm_preds/left_arm_preds.1_2/Conv_output_0 0=6 1=1 5=1 6=384
ConvolutionDepthWise     /detect/right_arm_preds/right_arm_preds.0_2/Conv 1 1 /detect/kpt_stem/kpt_stem.7_2/Mul_output_0_splitncnn_2 /detect/right_arm_preds/right_arm_preds.0_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/right_arm_preds/right_arm_preds.1_2/Conv 1 1 /detect/right_arm_preds/right_arm_preds.0_2/Conv_output_0 /detect/right_arm_preds/right_arm_preds.1_2/Conv_output_0 0=6 1=1 5=1 6=384
ConvolutionDepthWise     /detect/left_leg_preds/left_leg_preds.0_2/Conv 1 1 /detect/kpt_stem/kpt_stem.7_2/Mul_output_0_splitncnn_1 /detect/left_leg_preds/left_leg_preds.0_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/left_leg_preds/left_leg_preds.1_2/Conv 1 1 /detect/left_leg_preds/left_leg_preds.0_2/Conv_output_0 /detect/left_leg_preds/left_leg_preds.1_2/Conv_output_0 0=15 1=1 5=1 6=960
ConvolutionDepthWise     /detect/right_leg_preds/right_leg_preds.0_2/Conv 1 1 /detect/kpt_stem/kpt_stem.7_2/Mul_output_0_splitncnn_0 /detect/right_leg_preds/right_leg_preds.0_2/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/right_leg_preds/right_leg_preds.1_2/Conv 1 1 /detect/right_leg_preds/right_leg_preds.0_2/Conv_output_0 /detect/right_leg_preds/right_leg_preds.1_2/Conv_output_0 0=15 1=1 5=1 6=960
Concat                   /detect/Concat_2         5 1 /detect/head_preds/head_preds.1_2/Conv_output_0 /detect/left_arm_preds/left_arm_preds.1_2/Conv_output_0 /detect/right_arm_preds/right_arm_preds.1_2/Conv_output_0 /detect/left_leg_preds/left_leg_preds.1_2/Conv_output_0 /detect/right_leg_preds/right_leg_preds.1_2/Conv_output_0 /detect/Concat_2_output_0
Reshape                  reshape_6                1 1 /detect/cls_preds/cls_preds.1_2/Conv_output_0 /detect/Reshape_6_output_0 0=300 1=3
Permute                  /detect/Transpose_6      1 1 /detect/Reshape_6_output_0 P5/logits 0=1
Reshape                  reshape_7                1 1 /detect/Relu_2_output_0 /detect/Reshape_7_output_0 0=300 1=4
Permute                  /detect/Transpose_7      1 1 /detect/Reshape_7_output_0 P5/bbox_reg 0=1
Reshape                  reshape_8                1 1 /detect/Concat_2_output_0 /detect/Reshape_8_output_0 0=300 1=72
Permute                  /detect/Transpose_8      1 1 /detect/Reshape_8_output_0 P5/keypoints 0=1
ConvolutionDepthWise     /detect/cls_convs/cls_convs.0_3/Conv 1 1 /neck/Add_output_0_splitncnn_1 /detect/cls_convs/cls_convs.0_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.1_3/Conv 1 1 /detect/cls_convs/cls_convs.0_3/Conv_output_0 /detect/cls_convs/cls_convs.1_3/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.3_3/Mul 1 1 /detect/cls_convs/cls_convs.1_3/Conv_output_0 /detect/cls_convs/cls_convs.3_3/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_convs/cls_convs.4_3/Conv 1 1 /detect/cls_convs/cls_convs.3_3/Mul_output_0 /detect/cls_convs/cls_convs.4_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.5_3/Conv 1 1 /detect/cls_convs/cls_convs.4_3/Conv_output_0 /detect/cls_convs/cls_convs.5_3/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.7_3/Mul 1 1 /detect/cls_convs/cls_convs.5_3/Conv_output_0 /detect/cls_convs/cls_convs.7_3/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_convs/cls_convs.8_3/Conv 1 1 /detect/cls_convs/cls_convs.7_3/Mul_output_0 /detect/cls_convs/cls_convs.8_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.9_3/Conv 1 1 /detect/cls_convs/cls_convs.8_3/Conv_output_0 /detect/cls_convs/cls_convs.9_3/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.11_3/Mul 1 1 /detect/cls_convs/cls_convs.9_3/Conv_output_0 /detect/cls_convs/cls_convs.11_3/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_convs/cls_convs.12_3/Conv 1 1 /detect/cls_convs/cls_convs.11_3/Mul_output_0 /detect/cls_convs/cls_convs.12_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_convs/cls_convs.13_3/Conv 1 1 /detect/cls_convs/cls_convs.12_3/Conv_output_0 /detect/cls_convs/cls_convs.13_3/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/cls_convs/cls_convs.15_3/Mul 1 1 /detect/cls_convs/cls_convs.13_3/Conv_output_0 /detect/cls_convs/cls_convs.15_3/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/cls_preds/cls_preds.0_3/Conv 1 1 /detect/cls_convs/cls_convs.15_3/Mul_output_0 /detect/cls_preds/cls_preds.0_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/cls_preds/cls_preds.1_3/Conv 1 1 /detect/cls_preds/cls_preds.0_3/Conv_output_0 /detect/cls_preds/cls_preds.1_3/Conv_output_0 0=3 1=1 5=1 6=192
ConvolutionDepthWise     /detect/reg_convs/reg_convs.0_3/Conv 1 1 /neck/Add_output_0_splitncnn_0 /detect/reg_convs/reg_convs.0_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.1_3/Conv 1 1 /detect/reg_convs/reg_convs.0_3/Conv_output_0 /detect/reg_convs/reg_convs.1_3/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.3_3/Mul 1 1 /detect/reg_convs/reg_convs.1_3/Conv_output_0 /detect/reg_convs/reg_convs.3_3/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/reg_convs/reg_convs.4_3/Conv 1 1 /detect/reg_convs/reg_convs.3_3/Mul_output_0 /detect/reg_convs/reg_convs.4_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.5_3/Conv 1 1 /detect/reg_convs/reg_convs.4_3/Conv_output_0 /detect/reg_convs/reg_convs.5_3/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.7_3/Mul 1 1 /detect/reg_convs/reg_convs.5_3/Conv_output_0 /detect/reg_convs/reg_convs.7_3/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/reg_convs/reg_convs.8_3/Conv 1 1 /detect/reg_convs/reg_convs.7_3/Mul_output_0 /detect/reg_convs/reg_convs.8_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.9_3/Conv 1 1 /detect/reg_convs/reg_convs.8_3/Conv_output_0 /detect/reg_convs/reg_convs.9_3/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.11_3/Mul 1 1 /detect/reg_convs/reg_convs.9_3/Conv_output_0 /detect/reg_convs/reg_convs.11_3/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/reg_convs/reg_convs.12_3/Conv 1 1 /detect/reg_convs/reg_convs.11_3/Mul_output_0 /detect/reg_convs/reg_convs.12_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_convs/reg_convs.13_3/Conv 1 1 /detect/reg_convs/reg_convs.12_3/Conv_output_0 /detect/reg_convs/reg_convs.13_3/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/reg_convs/reg_convs.15_3/Mul 1 1 /detect/reg_convs/reg_convs.13_3/Conv_output_0 /detect/reg_convs/reg_convs.15_3/Mul_output_0 0=1.666667e-01
Split                    split_33                 1 2 /detect/reg_convs/reg_convs.15_3/Mul_output_0 /detect/reg_convs/reg_convs.15_3/Mul_output_0_splitncnn_0 /detect/reg_convs/reg_convs.15_3/Mul_output_0_splitncnn_1
ConvolutionDepthWise     /detect/reg_preds/reg_preds.0_3/Conv 1 1 /detect/reg_convs/reg_convs.15_3/Mul_output_0_splitncnn_1 /detect/reg_preds/reg_preds.0_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/reg_preds/reg_preds.1_3/Conv 1 1 /detect/reg_preds/reg_preds.0_3/Conv_output_0 /detect/reg_preds/reg_preds.1_3/Conv_output_0 0=4 1=1 5=1 6=256
BinaryOp                 /detect/scales.3/Mul     1 1 /detect/reg_preds/reg_preds.1_3/Conv_output_0 /detect/scales.3/Mul_output_0 0=2 1=1 2=1.000000e+00
ReLU                     relu_3                   1 1 /detect/scales.3/Mul_output_0 /detect/Relu_3_output_0
ConvolutionDepthWise     /detect/kpt_stem/kpt_stem.0_3/Conv 1 1 /detect/reg_convs/reg_convs.15_3/Mul_output_0_splitncnn_0 /detect/kpt_stem/kpt_stem.0_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/kpt_stem/kpt_stem.1_3/Conv 1 1 /detect/kpt_stem/kpt_stem.0_3/Conv_output_0 /detect/kpt_stem/kpt_stem.1_3/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/kpt_stem/kpt_stem.3_3/Mul 1 1 /detect/kpt_stem/kpt_stem.1_3/Conv_output_0 /detect/kpt_stem/kpt_stem.3_3/Mul_output_0 0=1.666667e-01
ConvolutionDepthWise     /detect/kpt_stem/kpt_stem.4_3/Conv 1 1 /detect/kpt_stem/kpt_stem.3_3/Mul_output_0 /detect/kpt_stem/kpt_stem.4_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/kpt_stem/kpt_stem.5_3/Conv 1 1 /detect/kpt_stem/kpt_stem.4_3/Conv_output_0 /detect/kpt_stem/kpt_stem.5_3/Conv_output_0 0=64 1=1 5=1 6=4096
HardSwish                /detect/kpt_stem/kpt_stem.7_3/Mul 1 1 /detect/kpt_stem/kpt_stem.5_3/Conv_output_0 /detect/kpt_stem/kpt_stem.7_3/Mul_output_0 0=1.666667e-01
Split                    split_34                 1 5 /detect/kpt_stem/kpt_stem.7_3/Mul_output_0 /detect/kpt_stem/kpt_stem.7_3/Mul_output_0_splitncnn_0 /detect/kpt_stem/kpt_stem.7_3/Mul_output_0_splitncnn_1 /detect/kpt_stem/kpt_stem.7_3/Mul_output_0_splitncnn_2 /detect/kpt_stem/kpt_stem.7_3/Mul_output_0_splitncnn_3 /detect/kpt_stem/kpt_stem.7_3/Mul_output_0_splitncnn_4
ConvolutionDepthWise     /detect/head_preds/head_preds.0_3/Conv 1 1 /detect/kpt_stem/kpt_stem.7_3/Mul_output_0_splitncnn_4 /detect/head_preds/head_preds.0_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/head_preds/head_preds.1_3/Conv 1 1 /detect/head_preds/head_preds.0_3/Conv_output_0 /detect/head_preds/head_preds.1_3/Conv_output_0 0=30 1=1 5=1 6=1920
ConvolutionDepthWise     /detect/left_arm_preds/left_arm_preds.0_3/Conv 1 1 /detect/kpt_stem/kpt_stem.7_3/Mul_output_0_splitncnn_3 /detect/left_arm_preds/left_arm_preds.0_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/left_arm_preds/left_arm_preds.1_3/Conv 1 1 /detect/left_arm_preds/left_arm_preds.0_3/Conv_output_0 /detect/left_arm_preds/left_arm_preds.1_3/Conv_output_0 0=6 1=1 5=1 6=384
ConvolutionDepthWise     /detect/right_arm_preds/right_arm_preds.0_3/Conv 1 1 /detect/kpt_stem/kpt_stem.7_3/Mul_output_0_splitncnn_2 /detect/right_arm_preds/right_arm_preds.0_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/right_arm_preds/right_arm_preds.1_3/Conv 1 1 /detect/right_arm_preds/right_arm_preds.0_3/Conv_output_0 /detect/right_arm_preds/right_arm_preds.1_3/Conv_output_0 0=6 1=1 5=1 6=384
ConvolutionDepthWise     /detect/left_leg_preds/left_leg_preds.0_3/Conv 1 1 /detect/kpt_stem/kpt_stem.7_3/Mul_output_0_splitncnn_1 /detect/left_leg_preds/left_leg_preds.0_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/left_leg_preds/left_leg_preds.1_3/Conv 1 1 /detect/left_leg_preds/left_leg_preds.0_3/Conv_output_0 /detect/left_leg_preds/left_leg_preds.1_3/Conv_output_0 0=15 1=1 5=1 6=960
ConvolutionDepthWise     /detect/right_leg_preds/right_leg_preds.0_3/Conv 1 1 /detect/kpt_stem/kpt_stem.7_3/Mul_output_0_splitncnn_0 /detect/right_leg_preds/right_leg_preds.0_3/Conv_output_0 0=64 1=5 4=2 5=1 6=1600 7=64
Convolution              /detect/right_leg_preds/right_leg_preds.1_3/Conv 1 1 /detect/right_leg_preds/right_leg_preds.0_3/Conv_output_0 /detect/right_leg_preds/right_leg_preds.1_3/Conv_output_0 0=15 1=1 5=1 6=960
Concat                   /detect/Concat_3         5 1 /detect/head_preds/head_preds.1_3/Conv_output_0 /detect/left_arm_preds/left_arm_preds.1_3/Conv_output_0 /detect/right_arm_preds/right_arm_preds.1_3/Conv_output_0 /detect/left_leg_preds/left_leg_preds.1_3/Conv_output_0 /detect/right_leg_preds/right_leg_preds.1_3/Conv_output_0 /detect/Concat_3_output_0
Reshape                  reshape_9                1 1 /detect/cls_preds/cls_preds.1_3/Conv_output_0 /detect/Reshape_9_output_0 0=80 1=3
Permute                  /detect/Transpose_9      1 1 /detect/Reshape_9_output_0 P6/logits 0=1
Reshape                  reshape_10               1 1 /detect/Relu_3_output_0 /detect/Reshape_10_output_0 0=80 1=4
Permute                  /detect/Transpose_10     1 1 /detect/Reshape_10_output_0 P6/bbox_reg 0=1
Reshape                  reshape_11               1 1 /detect/Concat_3_output_0 /detect/Reshape_11_output_0 0=80 1=72
Permute                  /detect/Transpose_11     1 1 /detect/Reshape_11_output_0 P6/keypoints 0=1

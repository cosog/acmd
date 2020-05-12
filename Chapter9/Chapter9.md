# 第九章 功率平衡

- [第九章 功率平衡](Chapter9.md#第九章-功率平衡)
   - [9.1 输入文本](Chapter9.md#91-输入文本)
     - [9.1.1 输入参数说明](Chapter9.md#911-输入参数说明)
     - [9.1.2 输入实例](Chapter9.md#912-输入实例)
	 - [9.1.3 数据收集表](Chapter9.md#913-数据收集表)
   - [9.2 输出文本](Chapter9.md#92-输出文本)
     - [9.2.1 输出参数说明](Chapter9.md#921-输出参数说明)
     - [9.2.2 输出实例](Chapter9.md#922-输出实例)

## 9.1 输入文本

### 9.1.1 输入参数说明

*表9-1 输入参数说明表*

| 代码                     | 名称               | 单位  | 类型     | 必填     | 备注                                                        |
|--------------------------|--------------------|-------|----------|----------|-------------------------------------------------------------|
| AKString                 | 应用密钥           |       | string   |          | 预留字段                                                    |
| WellName                 | 井名               |       | string   | *&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;        |                         |
| **PumpingUnit**          | **抽油机数据**     |       |          |          |                                                             |
| Manufacturer             | 厂商               |       | string   |          |                                                             |
| Model                    | 型号               |       | string   |          |                                                             |
| Type                     | 类型               |       | int      |          | 1-前置式，2-后置式（默认），3-立式                          |
| CrankRotationDirection   | 曲柄旋转方向       |       | string   | *        | Clockwise－顺时针，Anticlockwise－逆时针，立式无            |
| OffsetAngleOfCrank       | 曲柄偏置角         | °     | float64  | *        | 非异相型抽油机填0                                           |
| InitialAngleOfCrank      | 曲柄初始角度       | °     | float64  |          | 非异相型默认0度，异相型默认12度，前置型默认15度             |
| BalanceMaxMoveSpace      | 平衡块最大移动距离 | m     | float64  |          | 默认3m，自动化调平衡预留                                    |
| **Balance**              | **平衡块数据**     |       |          |          |                                                             |
| MaxCNT                   | 出厂标配平衡块数   |       | int      |          |                                                             |
| **EveryBalance**         | **每块平衡块数据** |       |          |          |                                                             |
| Position                 | 目前位置           | m     | float64  | *         |                                                             |
| Weight                   | 重量               | kN    | float64  | *        |                                                             |
| **PRTF**                 | **位置扭矩因数**   |       |          |          |                                                             |
| CrankAngle               | 曲柄转角           | °     | []float64  |          |                                                             |
| PR                       | 光杆位置因数       | %     | []float64  |          | 国标为%，api为小数                                          |
| TF                       | 扭矩因数           | m     | []float64  |          |                                                             |
| **PSDiagram**            | **电功图数据**     |       |          |          |                                                             |
| AcquisitionTime          | 采集时间           |       | string   |          | "YYYY-MM-DD HH:NN:SS"                                       |
| Stroke                   | 冲程               | m     | float64  |          |                                                             |
| SPM                      | 冲次               | 1/min | float64  | *        |                                                             |
| P                        | 有功功率           | kW    | []float64  | *        |                                                             |
| S                        | 位移               | m     | []float64  | *        |                                                             |
| **SystemEfficiency**     | **系统效率**       |       |          |          |                                                             |
| MotorEfficiency          | 电机效率           | 小数  | float64  |          |                                                             |
| BeltEfficiency           | 皮带效率           | 小数  | float64  |          |                                                             |
| GearReducerEfficiency    | 减速箱效率         | 小数  | float64  |          |                                                             |

### 9.1.2 输入实例

```
{
	"AKString": "",                             //（1）应用密钥
	"WellName": "J01-001",                      //（2）井名
	"PumpingUnit": {                            //（3）抽油机数据
		"Manufacturer": "吉油",
		"Model": "CYJY12-4.8-53HF",
		"Type": 2,
		"CrankRotationDirection": "Clockwise",
		"OffsetAngleOfCrank": -8,
		"InitialAngleOfCrank": 12,
		"BalanceMaxMoveSpace": 3,
		"Balance": {
			"MaxCNT": 4,
			"EveryBalance": [
				{
					"Position": 0.45,
					"Weight": 10.58
                },
				{
					"Position": 0.45,
					"Weight": 10.58
                },
				{
					"Position": 0.45,
					"Weight": 10.58
                },
				{
					"Position": 0.45,
					"Weight": 10.58
                }
            ]
		},
		"PRTF": {
			"CrankAngle": [
            14.48,
            16.97,
            19.45,
            21.93,
			...
            4.55,
            7.03,
            9.52,
            12
        ],
			"PR": [
            0,
            0.0542,
            0.214,
            0.48,
			...
            0.394,
            0.175,
            0.0443,
            0
        ],
			"TF": [
            0.0508,
            0.15,
            0.249,
            0.348,
			...
            -0.205,
            -0.122,
            -0.0415,
            0
        ]
		}
	},
	"PSDiagram": {                            //（4）电功图数据
		"AcquisitionTime": "2018-03-08 08:00:00",
		"SPM": 3.89,
		"Stroke": 4.061,
		"P": [
            50.46,
            51.025,
            51.825,
            52.64,
			...
            49.78,
            49.87,
            50.08,
            50.46
        ],
		"S": [
            0,
            0.0022,
            0.0087,
            0.0195,
			...
            0.016,
            0.0071,
            0.0018,
            0
        ]
	},
	"SystemEfficiency": {                     //（5）系统效率
		"MotorEfficiency": 0.95,
		"BeltEfficiency": 0.9,
		"GearReducerEfficiency": 0.95
	}
}
```

### 9.1.3 数据收集表

*表9-2 抽油机数据表*

| 序号     | 井名* | 厂家 | 型号 | 类型 | 曲柄旋转方向* | 曲柄偏置角 (°)* |
|----------|-------|------------|------------|------------|---------------|------------------|
| 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   |     |        |
| 2        |       |            |            |            |               |                  |
| 3        |       |            |            |            |               |                  |

*表9-3 平衡块数据表*

| 序号     | 井名* | 平衡块位置及重量(m，kN) (例：0.2,10.58;0.2,10.58;0.25,10.58;0.25,10.58)*    | 平衡块最大移动距离(m)   |
|----------|-------|-----------------------------------------------------------------------------|-------------------------|
| 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  |     |                   |
| 2        |       |                                                                             |                         |
| 3        |       |                                                                             |                         |

## 9.2 输出文本

### 9.2.1 输出参数说明

*表9-4 输出参数说明表*

| 代码                              | 名称                   | 单位   | 类型     | 备注                                        |
|-----------------------------------|------------------------|--------|----------|---------------------------------------------|
| WellName                          | 井名                   |        | string   |                                             |
| AcquisitionTime                   | 采集时间               |        | string   |                                             |
| **CalculationStatus**             | **计算状态**           |        |          |                                             |
| ResultStatus                      | 计算结果状态           |        | int      | 详见表底注释[1]                             |
| **Verification**                  | **数据校验**           |        |          |                                             |
| ErrorCounter                      | 错误参数计数器         |        | int      | 错误参数个数                                |
| ErrorString                       | 错误参数字符串         |        | string   | 数据错误，计算不成功                        |
| WarningCounter                    | 报警计数器             |        | int      | 报警参数个数                                |
| WarningString                     | 报警字符串             |        | string   | 报警参数（取默认值，计算正常进行）          |
| **CurrentTorqueCurve**            | **目前扭矩曲线**       |        |          |                                             |
| Net                               | 减速箱输出轴净扭矩     | kN·m   | []float64  |                                             |
| **NetAnalysis**                   | **净扭矩曲线分析**     |        |          |                                             |
| MeanSquareRoot                    | 曲线均方根值           |        | float64  |                                             |
| UpStrokeMaxValue                  | 上冲程最大值           |        | float64  |                                             |
| DownStrokeMaxValue                | 下冲程最大值           |        | float64  |                                             |
| MaxValueDegreeOfBalance           | 最大值平衡度           |        | float64  |                                             |
| UpStrokeAveragePower              | 上冲程平均功率         |        | float64  |                                             |
| DownStrokeAveragePower            | 下冲程平均功率         |        | float64  |                                             |
| AveragePowerDegreeOfBalance       | 平均功率平衡度         |        | float64  |                                             |
| **MaxValueMethod**                | **最大值法**           |        |          |                                             |
| DeltaRadius                       | 移动距离               | m      | float64  | + 代表向外移，-代表向内移                   |
| DeltaBlock                        | 平衡块数变化           |        | int      | + 代表增加平衡块数， -代表减少平衡块数      |
| DeltaMaxValueDOB                  | 最大值平衡度预期变化   | %      | float64  | + 代表平衡度上升 -代表平衡度下降            |
| DeltaPowerDOB                     | 平均功率平衡度预期变化 | %      | float64  | + 代表平衡度上升 -代表平衡度下降            |
| PercentageOfDifferenceMSR         | 均方根预期变化率       | %      | float64  | (预期均值-目前均值)/目前均值*100            |
| **TorqueCurve**                   | **扭矩曲线**           |        |          |                                             |
| Net                               | 减速箱输出轴净扭矩     | kN·m   | []float64  |                                             |
| **NetAnalysis**                   | **净扭矩曲线分析**     |        |          |                                             |
| MeanSquareRoot                    | 曲线均方根值           |        | float64  |                                             |
| UpStrokeMaxValue                  | 上冲程最大值           |        | float64  |                                             |
| DownStrokeMaxValue                | 下冲程最大值           |        | float64  |                                             |
| MaxValueDegreeOfBalance           | 最大值平衡度           |        | float64  |                                             |
| UpStrokeAveragePower              | 上冲程平均功率         |        | float64  |                                             |
| DownStrokeAveragePower            | 下冲程平均功率         |        | float64  |                                             |
| AveragePowerDegreeOfBalance       | 平均功率平衡度         |        | float64  |                                             |
| **Balance**                       | **平衡块**             |        |          |                                             |
| MaxCNT                            | 标配平衡块数           |        | int      |                                             |
| **EveryBalance**                  | **平衡块参数**         |        |          |                                             |
| Position                          | 位置                   | m      | float64  |                                             |
| Weight                            | 重量                   | kN     | float64  |                                             |
| **AveragePowerMethod**            | **平均功率法**         |        |          |                                             |
| DeltaRadius                       | 移动距离               | m      | float64  | + 代表向外移，-代表向内移                   |
| DeltaBlock                        | 平衡块数变化           |        | int      | + 代表增加平衡块数， -代表减少平衡块数      |
| DeltaMaxValueDOB                  | 最大值平衡度预期变化   | %      | float64  | + 代表平衡度上升 -代表平衡度下降            |
| DeltaPowerDOB                     | 平均功率平衡度预期变化 | %      | float64  | + 代表平衡度上升 -代表平衡度下降            |
| PercentageOfDifferenceMSR         | 均方根预期变化率       | %      | float64  | (预期均值-目前均值)/目前均值*100            |
| **TorqueCurve**                   | **扭矩曲线**           |        |          |                                             |
| Net                               | 减速箱输出轴净扭矩     | kN·m   | []float64  |                                             |
| **NetAnalysis**                   | **净扭矩曲线分析**     |        |          |                                             |
| MeanSquareRoot                    | 曲线均方根值           |        | float64  |                                             |
| UpStrokeMaxValue                  | 上冲程最大值           |        | float64  |                                             |
| DownStrokeMaxValue                | 下冲程最大值           |        | float64  |                                             |
| MaxValueDegreeOfBalance           | 最大值平衡度           |        | float64  |                                             |
| UpStrokeAveragePower              | 上冲程平均功率         |        | float64  |                                             |
| DownStrokeAveragePower            | 下冲程平均功率         |        | float64  |                                             |
| AveragePowerDegreeOfBalance       | 平均功率平衡度         |        | float64  |                                             |
| **Balance**                       | **平衡块**             |        |          |                                             |
| MaxCNT                            | 标配平衡块数           |        | int      |                                             |
| **EveryBalance**                  | **平衡块参数**         |        |          |                                             |
| Position                          | 位置                   | m      | float64  |                                             |
| Weight                            | 重量                   | kN     | float64  |                                             |
| **MeanSquareRootMethod**          | **均方根法**           |        |          |                                             |
| DeltaRadius                       | 移动距离               | m      | float64  | + 代表向外移，-代表向内移                   |
| DeltaBlock                        | 平衡块数变化           |        | int      | + 代表增加平衡块数， -代表减少平衡块数      |
| DeltaMaxValueDOB                  | 最大值平衡度预期变化   | %      | float64  | + 代表平衡度上升 -代表平衡度下降            |
| DeltaPowerDOB                     | 平均功率平衡度预期变化 | %      | float64  | + 代表平衡度上升 -代表平衡度下降            |
| PercentageOfDifferenceMSR         | 均方根预期变化率       | %      | float64  | (预期均值-目前均值)/目前均值*100            |
| **TorqueCurve**                   | **扭矩曲线**           |        |          |                                             |
| Net                               | 减速箱输出轴净扭矩     | kN·m   | []float64  |                                             |
| **NetAnalysis**                   | **净扭矩曲线分析**     |        |          |                                             |
| MeanSquareRoot                    | 曲线均方根值           |        | float64  |                                             |
| UpStrokeMaxValue                  | 上冲程最大值           |        | float64  |                                             |
| DownStrokeMaxValue                | 下冲程最大值           |        | float64  |                                             |
| MaxValueDegreeOfBalance           | 最大值平衡度           |        | float64  |                                             |
| UpStrokeAveragePower              | 上冲程平均功率         |        | float64  |                                             |
| DownStrokeAveragePower            | 下冲程平均功率         |        | float64  |                                             |
| AveragePowerDegreeOfBalance       | 平均功率平衡度         |        | float64  |                                             |
| **Balance**                       | **平衡块**             |        |          |                                             |
| MaxCNT                            | 标配平衡块数           |        | int      |                                             |
| **EveryBalance**                  | **平衡块参数**         |        |          |                                             |
| Position                          | 位置                   | m      | float64  |                                             |
| Weight                            | 重量                   | kN     | float64  |                                             |
| **PRTF**                          | **位置扭矩因数**       |        |          |                                             |
| CrankAngle                        | 曲柄转角               | °      | []float64  |                                             |
| PR                                | 光杆位置因数           | %      | []float64  |                                             |
| TF                                | 扭矩因数               | m      | []float64  |                                             |
| **MotionCurve**                   | **运动特性曲线**       |        |          |                                             |
| CrankAngle                        | 曲柄转角               | °      | []float64  |                                             |
| S                                 | 光杆位移               | m      | []float64  |                                             |
| V                                 | 光杆速度               | m/s    | []float64  |                                             |
| A                                 | 光杆加速度             | m/S^2  | []float64  |                                             |

**[1]** *计算结果状态:1:计算成功，-44:请求数据读取失败，-55:请求数据json解码失败， -66:井数许可超限，-77:计算异常， -88:响应数据json编码失败， -99:数据校验错误*

### 9.2.2 输出实例

```
{
    "WellName": "J01-001",
    "AcquisitionTime": "2018-03-08 08: 00: 00",
    "CalculationStatus": {                      //（1）计算状态
        "ResultStatus": 1
    },
    "Verification": {                           //（2）数据校验
        "ErrorCounter": 0,
        "ErrorString": "",
        "WarningCounter": 0,
        "WarningString": ""
    },
    "CurrentTorqueCurve": {                    //（3）目前扭矩曲线
        "Net": [
            100.61,
            101.74,
            103.34,
            104.96,
			...
            99.26,
            99.44,
            99.86,
            100.61
        ],
        "NetAnalysis": {
            "MeanSquareRoot": 108.04,
            "UpStrokeMaxValue": 123.13,
            "DownStrokeMaxValue": 118.82,
            "MaxValueDegreeOfBalance": 96.5,
            "UpStrokeAveragePower": 47.69,
            "DownStrokeAveragePower": 40.25,
            "AveragePowerDegreeOfBalance": 84.39
        }
    },
    "MaxValueMethod": {                             //（4）最大值法
        "DeltaRadius": 1.22,
        "DeltaBlock": 0,
        "DeltaMaxValueDOB": -83.91,
        "DeltaPowerDOB": -176.05,
        "PercentageOfDifferenceMSR": -99.76,
        "TorqueCurve": {
            "Net": [
                0.0261,
                0.0261,
                0.0582,
                0.0742,
				...
                -0.0366,
                -0.0225,
                -0.0063,
                0.00991
            ],
            "NetAnalysis": {
                "MeanSquareRoot": 0.264,
                "UpStrokeMaxValue": 0.374,
                "DownStrokeMaxValue": 0.0471,
                "MaxValueDegreeOfBalance": 12.6,
                "UpStrokeAveragePower": 0.101,
                "DownStrokeAveragePower": -0.0928,
                "AveragePowerDegreeOfBalance": -91.66
            }
        },
        "Balance": {
            "MaxCNT": 4,
            "EveryBalance": [
                {
                    "Position": 1.67,
                    "Weight": 10.58
                },
                {
                    "Position": 1.67,
                    "Weight": 10.58
                },
                {
                    "Position": 1.67,
                    "Weight": 10.58
                },
                {
                    "Position": 1.67,
                    "Weight": 10.58
                }
            ]
        }
    },
    "AveragePowerMethod": {                        //（5）平均功率法
        "DeltaRadius": 3,
        "DeltaBlock": 0,
        "DeltaMaxValueDOB": -3867.48,
        "DeltaPowerDOB": -176.05,
        "PercentageOfDifferenceMSR": -4.43,
        "TorqueCurve": {
            "Net": [
                -10.18,
                -10.18,
                -22.76,
                -28.99,
				...
                14.31,
                8.79,
                2.46,
                -3.87
            ],
            "NetAnalysis": {
                "MeanSquareRoot": 103.26,
                "UpStrokeMaxValue": -3.87,
                "DownStrokeMaxValue": 146,
                "MaxValueDegreeOfBalance": -3770.97,
                "UpStrokeAveragePower": -39.58,
                "DownStrokeAveragePower": 36.28,
                "AveragePowerDegreeOfBalance": -91.66
            }
        },
        "Balance": {
            "MaxCNT": 4,
            "EveryBalance": [
                {
                    "Position": 3.45,
                    "Weight": 10.58
                },
                {
                    "Position": 3.45,
                    "Weight": 10.58
                },
                {
                    "Position": 3.45,
                    "Weight": 10.58
                },
                {
                    "Position": 3.45,
                    "Weight": 10.58
                }
            ]
        }
    },
    "MeanSquareRootMethod": {                     //（6）均方根法
        "DeltaRadius": 3,
        "DeltaBlock": 0,
        "DeltaMaxValueDOB": -3867.48,
        "DeltaPowerDOB": -176.05,
        "PercentageOfDifferenceMSR": -16.9,
        "TorqueCurve": {
            "Net": [
                -8.86,
                -8.86,
                -19.79,
                -25.21,
				...
                12.44,
                7.64,
                2.14,
                -3.37
            ],
            "NetAnalysis": {
                "MeanSquareRoot": 89.79,
                "UpStrokeMaxValue": -3.37,
                "DownStrokeMaxValue": 126.96,
                "MaxValueDegreeOfBalance": -3770.97,
                "UpStrokeAveragePower": -34.42,
                "DownStrokeAveragePower": 31.54,
                "AveragePowerDegreeOfBalance": -91.66
            }
        },
        "Balance": {
            "MaxCNT": 4,
            "EveryBalance": [
                {
                    "Position": 3.45,
                    "Weight": 10.58
                },
                {
                    "Position": 3.45,
                    "Weight": 10.58
                },
                {
                    "Position": 3.45,
                    "Weight": 10.58
                },
                {
                    "Position": 3.45,
                    "Weight": 10.58
                }
            ]
        }
    },
    "PRTF": {                              //（7）位置扭矩因数
        "CrankAngle": [
            12,
            12,
            16.97,
            19.45,
			...
            2.38,
            4.55,
            7.03,
            9.52
        ],
        "PR": [
            0,
            0,
            0.0542,
            0.214,
			...
            0.699,
            0.394,
            0.175,
            0.0443
        ],
        "TF": [
            0,
            0,
            0.15,
            0.249,
			...
            -0.286,
            -0.205,
            -0.122,
            -0.0415
        ]
    },
    "MotionCurve": {                           //（8）运动特性曲线
        "CrankAngle": [
            14.48,
            16.97,
            19.45,
            21.93,
			...
            4.55,
            7.03,
            9.52,
            12
        ],
        "S": [
            0,
            0.0022,
            0.0087,
            0.0195,
			...
            0.016,
            0.0071,
            0.0018,
            0
        ],
        "V": [
            0.0207,
            0.0611,
            0.102,
            0.142,
			...
            -0.0837,
            -0.0498,
            -0.0169,
            0
        ],
        "A": [
            0.38,
            0.38,
            0.38,
            0.371,
			...
            0.318,
            0.309,
            0.159,
            0.194
        ]
    }
}
```

----[第八章 功图平衡](.././Chapter8/Chapter8.md)----[返回章节目录](.././README.md)----[第十章 电功图反演](.././Chapter10/Chapter10.md)----
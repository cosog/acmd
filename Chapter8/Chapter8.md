# 第八章 功图平衡

- [第八章 功图平衡](Chapter8.md#第八章-功图平衡)
   - [8.1 输入文本](Chapter8.md#81-输入文本)
     - [8.1.1 输入参数说明](Chapter8.md#811-输入参数说明)
     - [8.1.2 输入实例](Chapter8.md#812-输入实例)
	 - [8.1.3 数据收集表](Chapter8.md#813-数据收集表)
   - [8.2 输出文本](Chapter8.md#82-输出文本)
     - [8.2.1 输出参数说明](Chapter8.md#821-输出参数说明)
     - [8.2.2 输出实例](Chapter8.md#822-输出实例)

## 8.1 输入文本

### 8.1.1 输入参数说明

*表8-1 输入参数说明表*

| 代码                             | 名称               | 单位  | 类型     | 必填     | 备注                                                    |
|----------------------------------|--------------------|-------|----------|----------|---------------------------------------------------------|
| AKString                         | 应用密钥           |       | string   |          | 预留字段                                                |
| WellName                         | 井名               |       | string   | *&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |                            |
| **PumpingUnit**                  | **抽油机数据**     |       |          |          |                                                         |
| Manufacturer                     | 厂商               |       | string   |          |                                                         |
| Model                            | 型号               |       | string   |          |                                                         |
| Type                             | 类型               |       | int      |          | 1-前置式，2-后置式（默认），3-立式                      |
| CrankRotationDirection           | 曲柄旋转方向       |       | string   | *        | Clockwise－顺时针，Anticlockwise－逆时针，立式无        |
| OffsetAngleOfCrank               | 曲柄偏置角         | °     | float64  | *        | 非异相型抽油机填0                                       |
| InitialAngleOfCrank              | 曲柄初始角度       | °     | float64  |          | 非异相型默认0度，异相型默认12度，前置型默认15度         |
| CrankGravityRadius               | 曲柄重心半径       | m     | float64  | *        |                                                         |
| SingleCrankWeight                | 单块曲柄重量       | kN    | float64  | *        |                                                         |
| BalanceMaxMoveSpace              | 平衡块最大移动距离 | m     | float64  |          | 默认3m，自动化调平衡预留                                |
| StructuralUnbalance              | 结构不平衡重       | kN    | float64  | *        | 复合平衡尾平衡按角度档位可调的                          |
| **Balance**                      | **平衡块**         |       |          |          |                                                         |
| MaxCNT                           | 标配平衡块数       |       | int      |          |                                                         |
| **EveryBalance**                 | **平衡块参数**     |       |          |          |                                                         |
| Position                         | 目前位置           | m     | float64  | *        |                                                         |
| Weight                           | 重量               | kN    | float64  | *        |                                                         |
| **PRTF**                         | **位置扭矩因数**   |       |          |          |                                                         |
| CrankAngle                       | 曲柄转角           | °     | []float64  |          |                                                         |
| PR                               | 光杆位置因数       | %     | []float64  |          | 国标为%，api为小数                                      |
| TF                               | 扭矩因数           | m     | []float64  |          |                                                         |
| **FSDiagram**                    | **地面功图**       |       |          |          |                                                         |
| AcquisitionTime                  | 采集时间           |       | string   |          | "YYYY-MM-DD HH:NN:SS"                                   |
| Stroke                           | 冲程               | m     | float64  |          |                                                         |
| SPM                              | 冲次               | 1/min | float64  | *        |                                                         |
| F                                | 载荷               | kN    | []float64  | *        |                                                         |
| S                                | 位移               | m     | []float64  | *        |                                                         |
| **SystemEfficiency**             | **系统效率**       |       |          |          |                                                         |
| FourBarLinkageEfficiency         | 四连杆效率         | 小数  | float64  |          |                                                         |

### 8.1.2 输入实例

```
{
	"AKString": "",                               //（1）应用密钥
	"WellName": "J01-001",                        //（2）井名
	"PumpingUnit": {                              //（3）抽油机数据
		"Manufacturer": "吉油",
		"Model": "CYJY12-4.8-53HF",
		"Type": 2,
		"CrankRotationDirection": "Clockwise",
		"OffsetAngleOfCrank": -8,
		"InitialAngleOfCrank": 12,
		"CrankGravityRadius": 1.12,
		"SingleCrankWeight": 18.19,
		"BalanceMaxMoveSpace": 3,
		"StructuralUnbalance": 26.75,
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
	"FSDiagram": {                                //（4）地面功图
		"AcquisitionTime": "2018-03-08 08:00:00",
		"SPM": 3.89,
		"Stroke": 4.061,
		"F": [
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
	"SystemEfficiency": {                         //（5）系统效率
		"FourBarLinkageEfficiency": 0.95
	}
} 
```


### 8.1.3 数据收集表

*表8-2 抽油机数据表*

| 序号      | 井名* | 厂家 | 型号 | 类型 | 曲柄旋转方向* | 曲柄偏置角(°)*   | 曲柄重心半径(m)*  | 单块曲柄重量(kN)*  | 结构不平衡重(kN)*   |
|----------|-------|------------|------------|------------|---------------|------------------|-------------------|--------------------|---------------------|
| 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;         |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;       |          |       |          |         |
| 2        |       |            |            |            |               |                  |                   |                    |                     |
| 3        |       |            |            |            |               |                  |                   |                    |                     |

*表8-3 平衡块数据表*

| 序号     | 井名* | 平衡块位置及重量(m，kN) (例：0.2,10.58;0.2,10.58;0.25,10.58;0.25,10.58)*    | 平衡块最大移动距离(m)   |
|----------|-------|-----------------------------------------------------------------------------|-------------------------|
| 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;       |                                                |                         |
| 2        |       |                                                                             |                         |
| 3        |       |                                                                             |                         |

*表8-4 抽油机特性曲线（选填）*

<html>
        <table>
            <tr>
                 <th colspan="7">光杆位置因数和扭矩因数</th>
            </tr>
            <tr>
                <td rowspan="2">曲柄位置(度)</td>
                <td colspan="3">光杆位置因数PR(%)</td>
                <td colspan="3">扭矩因数TF(m)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td>
            </tr>
            <tr>
                <td colspan="3">冲程长度(m)</td>
                <td colspan="3">冲程长度(m)</td>
            </tr>
            <tr>
                <td>顺时针/逆时针</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
            </tr>
            <tr>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
            </tr>
            <tr>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
                <td>&nbsp;</td>
            </tr>
        </table>
</html>

## 8.2 输出文本

### 8.2.1 输出参数说明

*表8-5 输出参数说明表*

| 代码                          | 名称                   | 单位   | 类型     | 备注                                    |
|-------------------------------|------------------------|--------|----------|-----------------------------------------|
| WellName                      | 井名                   |        | string   |                                         |
| AcquisitionTime               | 采集时间               |        | string   |                                         |
| **CalculationStatus**         | **计算状态**           |        |          |                                         |
| ResultStatus                  | 计算结果状态           |        | int      | 详见表底注释[1]                         |
| **Verification**              | **数据校验**           |        |          |                                         |
| ErrorCounter                  | 错误参数计数器         |        | int      | 错误参数个数                            |
| ErrorString                   | 错误参数字符串         |        | string   | 数据错误，计算不成功                    |
| WarningCounter                | 报警计数器             |        | int      | 报警参数个数                            |
| WarningString                 | 报警字符串             |        | string   | 报警参数（取默认值，计算正常进行）      |
| **CurrentTorqueCurve**        | **目前扭矩曲线**       |        |          |                                         |
| Load                          | 载荷扭矩               | kN·m   | []float64  |                                         |
| Balance                       | 平衡块扭矩             | kN·m   | []float64  |                                         |
| Crank                         | 曲柄扭矩               | kN·m   | []float64  |                                         |
| Net                           | 减速箱输出轴净扭矩     | kN·m   | []float64  |                                         |
| **NetAnalysis**               | **净扭矩曲线分析**     |        |          |                                         |
| MeanSquareRoot                | 曲线均方根值           |        | float64  |                                         |
| UpStrokeMaxValue              | 上冲程最大值           |        | float64  |                                         |
| DownStrokeMaxValue            | 下冲程最大值           |        | float64  |                                         |
| MaxValueDegreeOfBalance       | 最大值平衡度           |        | float64  |                                         |
| UpStrokeAveragePower          | 上冲程平均功率         |        | float64  |                                         |
| DownStrokeAveragePower        | 下冲程平均功率         |        | float64  |                                         |
| AveragePowerDegreeOfBalance   | 平均功率平衡度         |        | float64  |                                         |
| **MaxValueMethod**            | **最大值法**           |        |          |                                         |
| DeltaRadius                   | 移动距离               | m      | float64  | + 代表向外移，-代表向内移               |
| DeltaBlock                    | 平衡块数变化           |        | int      | + 代表增加平衡块数， -代表减少平衡块数  |
| DeltaMaxValueDOB              | 最大值平衡度预期变化   | %      | float64  | + 代表平衡度上升 -代表平衡度下降        |
| DeltaPowerDOB                 | 平均功率平衡度预期变化 | %      | float64  | + 代表平衡度上升 -代表平衡度下降        |
| PercentageOfDifferenceMSR     | 均方根预期变化率       | %      | float64  | (预期均值-目前均值)/目前均值*100        |
| **TorqueCurve**               | **扭矩曲线**           |        |          |                                         |
| Balance                       | 平衡块扭矩             | kN·m   | []float64  |                                         |
| Net                           | 减速箱输出轴净扭矩     | kN·m   | []float64  |                                         |
| **NetAnalysis**               | **净扭矩曲线分析**     |        |          |                                         |
| MeanSquareRoot                | 曲线均方根值           |        | float64  |                                         |
| UpStrokeMaxValue              | 上冲程最大值           |        | float64  |                                         |
| DownStrokeMaxValue            | 下冲程最大值           |        | float64  |                                         |
| MaxValueDegreeOfBalance       | 最大值平衡度           |        | float64  |                                         |
| UpStrokeAveragePower          | 上冲程平均功率         |        | float64  |                                         |
| DownStrokeAveragePower        | 下冲程平均功率         |        | float64  |                                         |
| AveragePowerDegreeOfBalance   | 平均功率平衡度         |        | float64  |                                         |
| **Balance **                  | **平衡块**             |        |          |                                         |
| MaxCNT                        | 标配平衡块数           |        | int      |                                         |
| **EveryBalance**              | **平衡块参数**         |        |          |                                         |
| Position                      | 位置                   | m      | float64  |                                         |
| Weight                        | 重量                   | kN     | float64  |                                         |
| **AveragePowerMethod**        | **平均功率法**         |        |          |                                         |
| DeltaRadius                   | 移动距离               | m      | float64  | + 代表向外移，-代表向内移               |
| DeltaBlock                    | 平衡块数变化           |        | int      | + 代表增加平衡块数， -代表减少平衡块数  |
| DeltaMaxValueDOB              | 最大值平衡度预期变化   | %      | float64  | + 代表平衡度上升 -代表平衡度下降        |
| DeltaPowerDOB                 | 平均功率平衡度预期变化 | %      | float64  | + 代表平衡度上升 -代表平衡度下降        |
| PercentageOfDifferenceMSR     | 均方根预期变化率       | %      | float64  | (预期均值-目前均值)/目前均值*100        |
| **TorqueCurve**               | **扭矩曲线**           |        |          |                                         |
| Balance                       | 平衡块扭矩             | kN·m   | []float64  |                                         |
| Net                           | 减速箱输出轴净扭矩     | kN·m   | []float64  |                                         |
| **NetAnalysis**               | **净扭矩曲线分析**     |        |          |                                         |
| MeanSquareRoot                | 曲线均方根值           |        | float64  |                                         |
| UpStrokeMaxValue              | 上冲程最大值           |        | float64  |                                         |
| DownStrokeMaxValue            | 下冲程最大值           |        | float64  |                                         |
| MaxValueDegreeOfBalance       | 最大值平衡度           |        | float64  |                                         |
| UpStrokeAveragePower          | 上冲程平均功率         |        | float64  |                                         |
| DownStrokeAveragePower        | 下冲程平均功率         |        | float64  |                                         |
| AveragePowerDegreeOfBalance   | 平均功率平衡度         |        | float64  |                                         |
| **Balance**                   | **平衡块**             |        |          |                                         |
| MaxCNT                        | 标配平衡块数           |        | int      |                                         |
| **EveryBalance**              | **平衡块参数**         |        |          |                                         |
| Position                      | 位置                   | m      | float64  |                                         |
| Weight                        | 重量                   | kN     | float64  |                                         |
| **MeanSquareRootMethod**      | **均方根法**           |        |          |                                         |
| DeltaRadius                   | 移动距离               | m      | float64  | + 代表向外移，-代表向内移               |
| DeltaBlock                    | 平衡块数变化           |        | int      | + 代表增加平衡块数， -代表减少平衡块数  |
| DeltaMaxValueDOB              | 最大值平衡度预期变化   | %      | float64  | + 代表平衡度上升 -代表平衡度下降        |
| DeltaPowerDOB                 | 平均功率平衡度预期变化 | %      | float64  | + 代表平衡度上升 -代表平衡度下降        |
| PercentageOfDifferenceMSR     | 均方根预期变化率       | %      | float64  | (预期均值-目前均值)/目前均值*100        |
| **TorqueCurve**               | **扭矩曲线**           |        |          |                                         |
| Balance                       | 平衡块扭矩             | kN·m   | []float64  |                                         |
| Net                           | 减速箱输出轴净扭矩     | kN·m   | []float64  |                                         |
| **NetAnalysis**               | **净扭矩曲线分析**     |        |          |                                         |
| MeanSquareRoot                | 曲线均方根值           |        | float64  |                                         |
| UpStrokeMaxValue              | 上冲程最大值           |        | float64  |                                         |
| DownStrokeMaxValue            | 下冲程最大值           |        | float64  |                                         |
| MaxValueDegreeOfBalance       | 最大值平衡度           |        | float64  |                                         |
| UpStrokeAveragePower          | 上冲程平均功率         |        | float64  |                                         |
| DownStrokeAveragePower        | 下冲程平均功率         |        | float64  |                                         |
| AveragePowerDegreeOfBalance   | 平均功率平衡度         |        | float64  |                                         |
| **Balance**                   | **平衡块**             |        |          |                                         |
| MaxCNT                        | 标配平衡块数           |        | int      |                                         |
| **EveryBalance**              | **平衡块参数**         |        |          |                                         |
| Position                      | 位置                   | m      | float64  |                                         |
| Weight                        | 重量                   | kN     | float64  |                                         |
| **PRTF**                      | **位置扭矩因数**       |        |          |                                         |
| CrankAngle                    | 曲柄转角               | °      | []float64  |                                         |
| PR                            | 光杆位置因数           | %      | []float64  |                                         |
| TF                            | 扭矩因数               | m      | []float64  |                                         |
| **MotionCurve**               | **运动特性曲线**       |        |          |                                         |
| CrankAngle                    | 曲柄转角               | °      | []float64  |                                         |
| S                             | 光杆位移               | m      | []float64  |                                         |
| V                             | 光杆速度               | m/s    | []float64  |                                         |
| A                             | 光杆加速度             | m/s^2  | []float64  |                                         |

**[1]** *计算结果状态:1:计算成功，-44:请求数据读取失败，-55:请求数据json解码失败， -66:井数许可超限，-77:计算异常， -88:响应数据json编码失败， -99:数据校验错误*

### 8.2.2 输出实例
```
{
    "WellName": "J01-001",
    "AcquisitionTime": "2018-03-08 08: 00: 00",
    "CalculationStatus": {                    //（1）计算状态
        "ResultStatus": 1
    },
    "Verification": {                         //（2）数据校验
        "ErrorCounter": 0,
        "ErrorString": "",
        "WarningCounter": 0,
        "WarningString": ""
    },
    "CurrentTorqueCurve": {                   //（3）目前扭矩曲线
        "Load": [
            0,
            0,
            3.76,
            6.45,
			...
            -6.59,
            -4.74,
            -2.84,
            -0.984
        ],
        "Balance": [
            -1.33,
            -1.33,
            -2.97,
            -3.78,
			...
            1.87,
            1.15,
            0.321,
            -0.505
        ],
        "Crank": [
            -2.84,
            -2.84,
            -6.35,
            -8.09,
			...
            3.99,
            2.45,
            0.688,
            -1.08
        ],
        "Net": [
            -4.17,
            -4.17,
            -5.56,
            -5.42,
			...
            -0.729,
            -1.14,
            -1.84,
            -2.57
        ],
        "NetAnalysis": {
            "MeanSquareRoot": 10.47,
            "UpStrokeMaxValue": 12.75,
            "DownStrokeMaxValue": 19.59,
            "MaxValueDegreeOfBalance": 153.68,
            "UpStrokeAveragePower": 1.89,
            "DownStrokeAveragePower": 4.07,
            "AveragePowerDegreeOfBalance": 215.51
        }
    },
    "MaxValueMethod": {                         //（4）最大值法
        "DeltaRadius": -0.084,
        "DeltaBlock": 0,
        "DeltaMaxValueDOB": -53.68,
        "DeltaPowerDOB": -103.76,
        "PercentageOfDifferenceMSR": -4.44,
        "TorqueCurve": {
            "Balance": [
                -1.08,
                -1.08,
                -2.41,
                -3.07,
				...
                1.52,
                0.932,
                0.261,
                -0.411
            ],
            "Net": [
                -3.92,
                -3.92,
                -5.01,
                -4.72,
				...
                -1.08,
                -1.36,
                -1.9,
                -2.48
            ],
            "NetAnalysis": {
                "MeanSquareRoot": 10.01,
                "UpStrokeMaxValue": 16.11,
                "DownStrokeMaxValue": 16.11,
                "MaxValueDegreeOfBalance": 100,
                "UpStrokeAveragePower": 2.85,
                "DownStrokeAveragePower": 3.19,
                "AveragePowerDegreeOfBalance": 111.75
            }
        },
        "Balance": {
            "MaxCNT": 4,
            "EveryBalance": [
                {
                    "Position": 0.366,
                    "Weight": 10.58
                },
                {
                    "Position": 0.366,
                    "Weight": 10.58
                },
                {
                    "Position": 0.366,
                    "Weight": 10.58
                },
                {
                    "Position": 0.366,
                    "Weight": 10.58
                }
            ]
        }
    },
    "AveragePowerMethod": {                      //（5）平均功率法
        "DeltaRadius": -0.1,
        "DeltaBlock": 0,
        "DeltaMaxValueDOB": -61.43,
        "DeltaPowerDOB": -116.01,
        "PercentageOfDifferenceMSR": -4.62,
        "TorqueCurve": {
            "Balance": [
                -1.03,
                -1.03,
                -2.31,
                -2.94,
				...
                1.45,
                0.891,
                0.25,
                -0.393
            ],
            "Net": [
                -3.88,
                -3.88,
                -4.9,
                -4.58,
				...
                -1.14,
                -1.4,
                -1.91,
                -2.46
            ],
            "NetAnalysis": {
                "MeanSquareRoot": 9.99,
                "UpStrokeMaxValue": 16.75,
                "DownStrokeMaxValue": 15.45,
                "MaxValueDegreeOfBalance": 92.25,
                "UpStrokeAveragePower": 3.04,
                "DownStrokeAveragePower": 3.02,
                "AveragePowerDegreeOfBalance": 99.5
            }
        },
        "Balance": {
            "MaxCNT": 4,
            "EveryBalance": [
                {
                    "Position": 0.35,
                    "Weight": 10.58
                },
                {
                    "Position": 0.35,
                    "Weight": 10.58
                },
                {
                    "Position": 0.35,
                    "Weight": 10.58
                },
                {
                    "Position": 0.35,
                    "Weight": 10.58
                }
            ]
        }
    },
    "MeanSquareRootMethod": {                     //（6）均方根法
        "DeltaRadius": -0.11,
        "DeltaBlock": 0,
        "DeltaMaxValueDOB": -66,
        "DeltaPowerDOB": -122.97,
        "PercentageOfDifferenceMSR": -4.62,
        "TorqueCurve": {
            "Balance": [
                -1,
                -1,
                -2.24,
                -2.86,
				...
                1.41,
                0.866,
                0.243,
                -0.382
            ],
            "Net": [
                -3.85,
                -3.85,
                -4.84,
                -4.5,
				...
                -1.19,
                -1.42,
                -1.91,
                -2.45
            ],
            "NetAnalysis": {
                "MeanSquareRoot": 9.99,
                "UpStrokeMaxValue": 17.15,
                "DownStrokeMaxValue": 15.04,
                "MaxValueDegreeOfBalance": 87.68,
                "UpStrokeAveragePower": 3.15,
                "DownStrokeAveragePower": 2.92,
                "AveragePowerDegreeOfBalance": 92.54
            }
        },
        "Balance": {
            "MaxCNT": 4,
            "EveryBalance": [
                {
                    "Position": 0.34,
                    "Weight": 10.58
                },
                {
                    "Position": 0.34,
                    "Weight": 10.58
                },
                {
                    "Position": 0.34,
                    "Weight": 10.58
                },
                {
                    "Position": 0.34,
                    "Weight": 10.58
                }
            ]
        }
    },
    "PRTF": {                                   //（7）位置扭矩因数
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
    "MotionCurve": {                             //（8）运动特性曲线
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

----[第七章 转速计产](.././Chapter7/Chapter7.md)----[返回章节目录](.././README.md)----[第九章 功率平衡](.././Chapter9/Chapter9.md)----